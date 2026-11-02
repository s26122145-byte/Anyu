<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WEB DEV QUEST // 網頁程式設計作品集</title>
    <!-- Google Fonts: Orbitron for Sci-Fi numbers/titles, Noto Sans TC for Chinese text -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;700;900&family=Orbitron:wght@500;700;900&display=swap" rel="stylesheet">
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --bg-color: #0b0d19;
            --neon-cyan: #00f0ff;
            --neon-pink: #ff007f;
            --neon-purple: #7000ff;
            --neon-green: #00ff66;
            --glass-bg: rgba(20, 24, 45, 0.55);
            --glass-border: rgba(0, 240, 255, 0.25);
            --glass-border-pink: rgba(255, 0, 127, 0.3);
            --locked-bg: rgba(15, 18, 32, 0.4);
            --locked-text: #5d6785;
            --text-main: #e2e8f0;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            user-select: none;
        }

        body {
            font-family: 'Orbitron', 'Noto Sans TC', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: flex-start;
            padding: 2rem 1rem 4rem 1rem;
            overflow-x: hidden;
            position: relative;
        }

        /* Animated Cyber Grid Background */
        body::before {
            content: "";
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background: 
                linear-gradient(rgba(0, 240, 255, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 240, 255, 0.03) 1px, transparent 1px);
            background-size: 40px 40px;
            z-index: -2;
            pointer-events: none;
        }

        /* Ambient Glowing Orbs */
        .orb {
            position: fixed;
            border-radius: 50%;
            filter: blur(100px);
            z-index: -1;
            opacity: 0.4;
            pointer-events: none;
            animation: pulseOrb 8s infinite alternate ease-in-out;
        }

        .orb-1 {
            top: -10%;
            left: 10%;
            width: 400px;
            height: 400px;
            background: var(--neon-purple);
        }

        .orb-2 {
            bottom: -10%;
            right: 10%;
            width: 450px;
            height: 450px;
            background: var(--neon-cyan);
            animation-delay: -4s;
        }

        @keyframes pulseOrb {
            0% { transform: scale(1) translate(0, 0); opacity: 0.3; }
            100% { transform: scale(1.2) translate(30px, -20px); opacity: 0.6; }
        }

        /* Container Layout */
        .main-container {
            width: 100%;
            max-width: 1100px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 2.5rem;
        }

        /* Profile Header Section with Glassmorphism */
        .profile-card {
            background: var(--glass-bg);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid var(--glass-border);
            border-radius: 24px;
            padding: 2.5rem 2rem;
            width: 100%;
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.5),
                        inset 0 0 15px rgba(0, 240, 255, 0.1);
            position: relative;
            overflow: hidden;
        }

        /* Cyber Corner Accents */
        .profile-card::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--neon-cyan), var(--neon-pink), var(--neon-purple));
        }

        .avatar-wrapper {
            position: relative;
            margin-bottom: 1.25rem;
        }

        .avatar-img {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--neon-cyan);
            box-shadow: 0 0 20px rgba(0, 240, 255, 0.5);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .profile-card:hover .avatar-img {
            transform: scale(1.05) rotate(3deg);
            box-shadow: 0 0 30px rgba(255, 0, 127, 0.7);
            border-color: var(--neon-pink);
        }

        .status-badge {
            position: absolute;
            bottom: 5px;
            right: 0;
            background: #000;
            border: 1px solid var(--neon-green);
            color: var(--neon-green);
            font-size: 0.75rem;
            padding: 0.2rem 0.6rem;
            border-radius: 20px;
            display: flex;
            align-items: center;
            gap: 4px;
            box-shadow: 0 0 10px rgba(0, 255, 102, 0.4);
        }

        .status-dot {
            width: 6px;
            height: 6px;
            background-color: var(--neon-green);
            border-radius: 50%;
            animation: blink 1.5s infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.2; }
        }

        .user-title {
            font-size: 2rem;
            font-weight: 900;
            letter-spacing: 1px;
            background: linear-gradient(135deg, #ffffff 30%, var(--neon-cyan) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 0.5rem;
            text-shadow: 0 0 20px rgba(0, 240, 255, 0.3);
        }

        .user-subtitle {
            color: #94a3b8;
            font-size: 0.95rem;
            letter-spacing: 2px;
            margin-bottom: 1.5rem;
            font-family: 'Noto Sans TC', sans-serif;
        }

        /* RPG Stats Progress Bar */
        .stats-bar {
            width: 100%;
            max-width: 480px;
            background: rgba(0, 0, 0, 0.4);
            border-radius: 12px;
            padding: 0.8rem 1.2rem;
            border: 1px solid rgba(255, 255, 255, 0.05);
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
        }

        .stats-info {
            display: flex;
            justify-content: space-between;
            font-size: 0.8rem;
            color: #cbd5e1;
            font-weight: 700;
        }

        .progress-track {
            width: 100%;
            height: 8px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 4px;
            overflow: hidden;
            position: relative;
        }

        .progress-fill {
            width: 12.5%; /* 2/16 unlocked = 12.5% */
            height: 100%;
            background: linear-gradient(90deg, var(--neon-cyan), var(--neon-pink));
            box-shadow: 0 0 10px var(--neon-cyan);
            border-radius: 4px;
            transition: width 1s ease;
        }

        /* Quest Buttons Grid Layout */
        .grid-header {
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 0.5rem;
        }

        .section-title {
            font-size: 1.25rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            gap: 10px;
            color: #fff;
            letter-spacing: 1px;
        }

        .section-title i {
            color: var(--neon-pink);
        }

        .quest-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1.25rem;
            width: 100%;
        }

        /* Card Styles */
        .quest-card {
            position: relative;
            text-decoration: none;
            border-radius: 16px;
            padding: 1.4rem 1.2rem;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            min-height: 120px;
            transition: all 0.35s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            overflow: hidden;
        }

        /* Unlocked State Card */
        .quest-card.unlocked {
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
            cursor: pointer;
        }

        .quest-card.unlocked::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 4px;
            height: 100%;
            background: var(--neon-cyan);
            transition: all 0.3s ease;
        }

        .quest-card.unlocked:hover {
            transform: translateY(-6px) scale(1.02);
            border-color: var(--neon-cyan);
            box-shadow: 0 10px 30px rgba(0, 240, 255, 0.3),
                        inset 0 0 15px rgba(0, 240, 255, 0.2);
        }

        .quest-card.unlocked:hover::before {
            width: 100%;
            opacity: 0.08;
        }

        /* Alt Highlight for Week 2 */
        .quest-card.unlocked.alt-accent::before {
            background: var(--neon-pink);
        }

        .quest-card.unlocked.alt-accent:hover {
            border-color: var(--neon-pink);
            box-shadow: 0 10px 30px rgba(255, 0, 127, 0.35),
                        inset 0 0 15px rgba(255, 0, 127, 0.2);
        }

        /* Locked State Card */
        .quest-card.locked {
            background: var(--locked-bg);
            backdrop-filter: blur(6px);
            -webkit-backdrop-filter: blur(6px);
            border: 1px solid rgba(255, 255, 255, 0.05);
            color: var(--locked-text);
            cursor: not-allowed;
            opacity: 0.65;
            filter: grayscale(0.8);
        }

        .quest-card.locked:hover {
            transform: translateY(-2px);
            border-color: rgba(255, 255, 255, 0.15);
            opacity: 0.8;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.4);
        }

        /* Card Content Inner Elements */
        .card-top {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 0.75rem;
        }

        .week-tag {
            font-size: 0.75rem;
            font-weight: 900;
            letter-spacing: 1px;
            padding: 0.2rem 0.5rem;
            border-radius: 6px;
            background: rgba(255, 255, 255, 0.05);
            color: #94a3b8;
        }

        .unlocked .week-tag {
            background: rgba(0, 240, 255, 0.15);
            color: var(--neon-cyan);
        }

        .unlocked.alt-accent .week-tag {
            background: rgba(255, 0, 127, 0.15);
            color: var(--neon-pink);
        }

        .status-icon {
            font-size: 1.1rem;
        }

        .unlocked .status-icon {
            color: var(--neon-green);
            filter: drop-shadow(0 0 6px var(--neon-green));
        }

        .locked .status-icon {
            color: #475569;
        }

        .quest-title {
            font-size: 0.95rem;
            font-weight: 700;
            font-family: 'Noto Sans TC', sans-serif;
            color: var(--text-main);
            line-height: 1.4;
            transition: color 0.3s ease;
        }

        .locked .quest-title {
            color: #64748b;
        }

        .unlocked:hover .quest-title {
            color: #fff;
            text-shadow: 0 0 8px rgba(255, 255, 255, 0.6);
        }

        .quest-action {
            margin-top: 1rem;
            font-size: 0.75rem;
            display: flex;
            align-items: center;
            gap: 6px;
            font-weight: 700;
        }

        .unlocked .quest-action {
            color: var(--neon-cyan);
        }

        .unlocked.alt-accent .quest-action {
            color: var(--neon-pink);
        }

        .locked .quest-action {
            color: #475569;
        }

        /* Toast Notification for Locked Cards */
        .toast {
            position: fixed;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%) translateY(100px);
            background: rgba(15, 23, 42, 0.9);
            border: 1px solid var(--neon-pink);
            color: #fff;
            padding: 0.8rem 1.6rem;
            border-radius: 30px;
            box-shadow: 0 0 25px rgba(255, 0, 127, 0.4);
            backdrop-filter: blur(10px);
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 10px;
            opacity: 0;
            transition: all 0.4s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            pointer-events: none;
            z-index: 100;
            font-family: 'Noto Sans TC', sans-serif;
        }

        .toast.show {
            transform: translateX(-50%) translateY(0);
            opacity: 1;
        }

        /* Footer */
        footer {
            margin-top: 3rem;
            color: #64748b;
            font-size: 0.8rem;
            text-align: center;
            letter-spacing: 1px;
        }

        /* Responsive Breakpoints */
        @media (max-width: 1024px) {
            .quest-grid {
                grid-template-columns: repeat(3, 1fr);
            }
        }

        @media (max-width: 768px) {
            .quest-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 1rem;
            }

            .user-title {
                font-size: 1.6rem;
            }

            .profile-card {
                padding: 2rem 1.25rem;
            }
        }

        @media (max-width: 480px) {
            .quest-grid {
                grid-template-columns: repeat(1, 1fr);
            }

            body {
                padding: 1.2rem 0.8rem;
            }

            .avatar-img {
                width: 100px;
                height: 100px;
            }
        }
    </style>
</head>
<body>
    <!-- Background Animated Orbs -->
    <div class="orb orb-1"></div>
    <div class="orb orb-2"></div>

    <div class="main-container">
        
        <!-- Header / Profile Section -->
        <header class="profile-card">
            <div class="avatar-wrapper">
                <!-- Avatar placeholder using Dicebear API -->
                <img src="https://api.dicebear.com/7.x/bottts/svg?seed=CyberDev" alt="User Avatar" class="avatar-img">
                <div class="status-badge">
                    <span class="status-dot"></span>
                    <span>ONLINE</span>
                </div>
            </div>
            
            <h1 class="user-title">程式冒險者 // PORTFOLIO</h1>
            <p class="user-subtitle">網頁程式設計學習歷程與任務關卡入口</p>

            <!-- RPG Level Stats -->
            <div class="stats-bar">
                <div class="stats-info">
                    <span><i class="fa-solid fa-trophy" style="color: #ffd700;"></i> LEVEL 2 / 16</span>
                    <span>PROGRESS: 12.5%</span>
                </div>
                <div class="progress-track">
                    <div class="progress-fill"></div>
                </div>
            </div>
        </header>

        <!-- Main Quests Grid -->
        <main style="width: 100%;">
            <div class="grid-header" style="margin-bottom: 1.25rem;">
                <h2 class="section-title">
                    <i class="fa-solid fa-gamepad"></i> 任務關卡選單
                </h2>
                <span style="font-size: 0.8rem; color: #64748b;">16 WEEKS QUESTS</span>
            </div>

            <div class="quest-grid">
                
                <!-- Week 1 (Unlocked) -->
                <a href="w1/index.html" class="quest-card unlocked">
                    <div class="card-top">
                        <span class="week-tag">WEEK 01</span>
                        <i class="fa-solid fa-circle-check status-icon"></i>
                    </div>
                    <div class="quest-title">Week 1 - 數位名片</div>
                    <div class="quest-action">
                        <span>START MISSION</span>
                        <i class="fa-solid fa-arrow-right"></i>
                    </div>
                </a>

                <!-- Week 2 (Unlocked) -->
                <a href="w2/index.html" class="quest-card unlocked alt-accent">
                    <div class="card-top">
                        <span class="week-tag">WEEK 02</span>
                        <i class="fa-solid fa-circle-check status-icon"></i>
                    </div>
                    <div class="quest-title">Week 2 - 今天吃甚麼?</div>
                    <div class="quest-action">
                        <span>START MISSION</span>
                        <i class="fa-solid fa-arrow-right"></i>
                    </div>
                </a>

                <!-- Week 3 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 3')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 03</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 3 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 4 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 4')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 04</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 4 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 5 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 5')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 05</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 5 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 6 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 6')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 06</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 6 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 7 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 7')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 07</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 7 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 8 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 8')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 08</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 8 - 期中專案 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 9 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 9')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 09</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 9 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 10 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 10')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 10</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 10 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 11 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 11')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 11</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 11 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 12 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 12')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 12</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 12 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 13 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 13')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 13</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 13 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 14 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 14')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 14</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 14 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 15 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 15')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 15</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 15 - 尚未解鎖 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

                <!-- Week 16 (Locked) -->
                <a href="#" class="quest-card locked" onclick="showLockedToast(event, 'Week 16')">
                    <div class="card-top">
                        <span class="week-tag">WEEK 16</span>
                        <i class="fa-solid fa-lock status-icon"></i>
                    </div>
                    <div class="quest-title">Week 16 - 期末展示 🔒</div>
                    <div class="quest-action">
                        <span>LOCKED</span>
                    </div>
                </a>

            </div>
        </main>

        <footer>
            <p>© 2026 WEB PROGRAMMING COURSE // ALL RIGHTS RESERVED</p>
        </footer>
    </div>

    <!-- Toast Popup for Locked Quests -->
    <div id="toast" class="toast">
        <i class="fa-solid fa-triangle-exclamation" style="color: var(--neon-pink);"></i>
        <span id="toast-text">該關卡尚未解鎖，請先完成前置任務！</span>
    </div>

    <script>
        let toastTimeout;

        function showLockedToast(event, weekName) {
            // Prevent navigating
            event.preventDefault();

            const toast = document.getElementById('toast');
            const toastText = document.getElementById('toast-text');
            
            toastText.textContent = `【${weekName}】任務尚未解鎖！完成前置關卡後開放。`;
            
            toast.classList.add('show');

            clearTimeout(toastTimeout);
            toastTimeout = setTimeout(() => {
                toast.classList.remove('show');
            }, 2500);
        }
    </script>
</body>
</html>
