<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Anime Stickers Hub</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        header {
            text-align: center;
            padding: 30px 0;
            color: white;
        }

        .logo {
            font-size: 3rem;
            font-weight: 700;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4, #45b7d1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .subtitle {
            font-size: 1.2rem;
            opacity: 0.9;
            margin-bottom: 30px;
        }

        .categories {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
            margin-bottom: 40px;
        }

        .category-btn {
            padding: 12px 24px;
            background: rgba(255,255,255,0.2);
            border: 2px solid rgba(255,255,255,0.3);
            border-radius: 50px;
            color: white;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
            font-weight: 500;
        }

        .category-btn:hover,
        .category-btn.active {
            background: rgba(255,255,255,0.9);
            color: #333;
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }

        .search-box {
            display: flex;
            max-width: 400px;
            margin: 0 auto 30px;
            background: rgba(255,255,255,0.9);
            border-radius: 25px;
            padding: 5px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.1);
        }

        .search-box input {
            flex: 1;
            border: none;
            outline: none;
            padding: 15px 20px;
            font-size: 1rem;
            background: transparent;
        }

        .search-box i {
            color: #666;
            padding: 15px 20px;
            cursor: pointer;
            transition: color 0.3s ease;
        }

        .search-box i:hover {
            color: #667eea;
        }

        .stickers-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }

        .sticker-card {
            background: rgba(255,255,255,0.95);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            transition: all 0.4s ease;
            cursor: pointer;
            position: relative;
        }

        .sticker-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 25px 50px rgba(0,0,0,0.2);
        }

        .sticker-image {
            width: 100%;
            height: 200px;
            object-fit: cover;
            transition: transform 0.3s ease;
        }

        .sticker-card:hover .sticker-image {
            transform: scale(1.1);
        }

        .sticker-info {
            padding: 20px;
            text-align: center;
        }

        .sticker-name {
            font-weight: 600;
            margin-bottom: 10px;
            color: #333;
        }

        .sticker-category {
            font-size: 0.85rem;
            color: #667eea;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .download-btn {
            position: absolute;
            top: 10px;
            right: 10px;
            background: #ff6b6b;
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            cursor: pointer;
            opacity: 0;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .sticker-card:hover .download-btn {
            opacity: 1;
            transform: scale(1.1);
        }

        .load-more {
            display: block;
            margin: 40px auto;
            padding: 15px 40px;
            background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
            color: white;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .load-more:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 35px rgba(255,107,107,0.4);
        }

        .footer {
            text-align: center;
            padding: 40px 0;
            color: rgba(255,255,255,0.8);
            font-size: 0.9rem;
        }

        @media (max-width: 768px) {
            .stickers-grid {
                grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
                gap: 15px;
            }
            
            .logo {
                font-size: 2rem;
            }
            
            .categories {
                flex-direction: column;
                align-items: center;
            }
        }

        .no-results {
            text-align: center;
            grid-column: 1 / -1;
            padding: 60px 20px;
            color: rgba(255,255,255,0.8);
        }

        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }
    </style>
</head>
<body>
    <div class="particles" id="particles"></div>
    
    <div class="container">
        <header>
            <h1 class="logo">🎌 Anime Stickers Hub</h1>
            <p class="subtitle">Discover & Download the cutest anime stickers!</p>
        </header>

        <div class="search-box">
            <i class="fas fa-search"></i>
            <input type="text" id="searchInput" placeholder="Search stickers...">
        </div>

        <div class="categories">
            <div class="category-btn active" data-category="all">All</div>
            <div class="category-btn" data-category="kawaii">Kawaii</div>
            <div class="category-btn" data-category="attack">Attack on Titan</div>
            <div class="category-btn" data-category="naruto">Naruto</div>
            <div class="category-btn" data-category="demon">Demon Slayer</div>
            <div class="category-btn" data-category="jujutsu">Jujutsu Kaisen</div>
        </div>

        <div class="stickers-grid" id="stickersGrid">
            <!-- Stickers will be loaded here -->
        </div>

        <button class="load-more" onclick="loadMoreStickers()">Load More 🔥</button>

        <footer class="footer">
            <p>Made with ❤️ for anime lovers | Download & Share!</p>
        </footer>
    </div>

    <script>
        // Sample sticker data
        const stickersData = [
            { id: 1, name: "Chibi Goku", category: "kawaii", src: "https://images.unsplash.com/photo-1578864208457-718986bed1d2?w=300&h=300&fit=crop&crop=center" },
            { id: 2, name: "Nezuko Smile", category: "kawaii", src: "https://images.unsplash.com/photo-1643925439548-1a89770436b5?w=300&h=300&fit=crop&crop=center" },
            { id: 3, name: "Eren Yeager", category: "attack", src: "https://images.unsplash.com/photo-1655702437141-08a91f551cbd?w=300&h=300&fit=crop&crop=center" },
            { id: 4, name: "Naruto Uzumaki", category: "naruto", src: "https://images.unsplash.com/photo-1573426788788-2d759e4b18de?w=300&h=300&fit=crop&crop=center" },
            { id: 5, name: "Tanjiro Kamado", category: "demon", src: "https://images.unsplash.com/photo-1643925439548-1a89770436b5?w=300&h=300&fit=crop&crop=center" },
            { id: 6, name: "Gojo Satoru", category: "jujutsu", src: "https://images.unsplash.com/photo-1675718367111-58d5356ee3de?w=300&h=300&fit=crop&crop=center" },
            { id: 7, name: "Mikasa Ackerman", category: "attack", src: "https://images.unsplash.com/photo-1655702437141-08a91f551cbd?w=300&h=300&fit=crop&crop=center" },
            { id: 8, name: "Sakura Haruno", category: "naruto", src: "https://images.unsplash.com/photo-1578864208457-718986bed1d2?w=300&h=300&fit=crop&crop=center" },
            { id: 9, name: "Zenitsu Agatsuma", category: "demon", src: "https://images.unsplash.com/photo-1643925439548-1a89770436b5?w=300&h=300&fit=crop&crop=center" },
            { id: 10, name: "Itadori Yuji", category: "jujutsu", src: "https://images.unsplash.com/photo-1675718367111-58d5356ee3de?w=300&h=300&fit=crop&crop=center" },
            { id: 11, name: "Levi Ackerman", category: "attack", src: "https://images.unsplash.com/photo-1655702437141-08a91f551cbd?w=300&h=300&fit=crop&crop=center" },
            { id: 12, name: "Sasuke Uchiha", category: "naruto", src: "https://images.unsplash.com/photo-1573426788788-2d759e4b18de?w=300&h=300&fit=crop&crop=center" }
        ];

        let currentStickers = [];
        let visibleCount = 0;
        const stickersPerLoad = 6;

        // Initialize
        function init() {
            currentStickers = [...stickersData];
            renderStickers();
            setupEventListeners();
            createParticles();
        }

        function setupEventListeners() {
            // Category buttons
            document.querySelectorAll('.category-btn').forEach(btn => {
                btn.addEventListener('click', (e) => {
                    document.querySelectorAll('.category-btn').forEach(b => b.classList.remove('active'));
                    e.target.classList.add('active');
                    
                    const category = e.target.dataset.category;
                    filterStickers(category);
                });
            });

            // Search functionality
            document.getElementById('searchInput').addEventListener('input', (e) => {
                searchStickers(e.target.value);
            });
        }

        function renderStickers() {
            const grid = document.getElementById('stickersGrid');
            const visibleStickers = currentStickers.slice(0, visibleCount);
            
            if (visibleStickers.length === 0) {
                grid.innerHTML = '<div class="no-results"><i class="fas fa-search" style="font-size: 4rem; color: rgba(255,255,255,0.5); margin-bottom: 20px;"></i><h3>No stickers found</h3><p>Try different search terms or categories!</p></div>';
                return;
            }

            grid.innerHTML = visibleStickers.map(sticker => `
                <div class="sticker-card" data-category="${sticker.category}">
                    <img src="${sticker.src}" alt="${sticker.name}" class="sticker-image" loading="lazy">
                    <button class="download-btn" onclick="downloadSticker(event, '${sticker.src}', '${sticker.name}')">
                        <i class="fas fa-download"></i>
                    </button>
                    <div class="sticker-info">
                        <div class="sticker-name">${sticker.name}</div>
                        <div class="sticker-category">${sticker.category}</div>
                    </div>
                </div>
            `).join('');
        }

        function filterStickers(category) {
            if (category === 'all') {
                currentStickers = [...stickersData];
            } else {
                currentStickers = stickersData.filter(sticker => sticker.category === category);
            }
            visibleCount = stickersPerLoad;
            renderStickers();
        }

        function searchStickers(query) {
            if (!query.trim()) {
                currentStickers = [...stickersData];
            } else {
                currentStickers = stickersData.filter(sticker => 
                    sticker.name.toLowerCase().includes(query.toLowerCase()) ||
                    sticker.category.toLowerCase().includes(query.toLowerCase())
                );
            }
            visibleCount = stickersPerLoad;
            renderStickers();
        }

        function loadMoreStickers() {
            visibleCount += stickersPerLoad;
            renderStickers();
        }

        function downloadSticker(event, url, name) {
            event.stopPropagation();
            
            const link = document.createElement('a');
            link.href = url;
            link.download = `${name.replace(/[^a-z0-9]/gi, '_')}.png`;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
        }

        function createParticles() {
            const particles = document.getElementById('particles');
            for (let i = 0; i < 50; i++) {
                const particle = document.createElement('div');
                particle.style.cssText = `
                    position: absolute;
                    width: ${Math.random() * 4 + 2}px;
                    height: ${Math.random() * 4 + 2}px;
                    background: rgba(255,255,255,${Math.random() * 0.5 + 0.1});
                    border-radius: 50%;
                    left: ${Math.random() * 100}%;
                    top: ${Math.random() * 100}%;
                    animation: float ${10 + Math.random() * 10}s infinite linear;
                    animation-delay: ${Math.random() * 10}s;
                `;
                particles.appendChild(particle);
            }
        }

        // CSS for particle animation
        const style = document.createElement('style');
        style.textContent = `
            @keyframes float {
                0% { transform: translateY(0px) rotate(0deg); opacity: 1; }
                100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
            }
        `;
        document.head.appendChild(style);

        // Initialize app
        init();
    </script>
</body>
</html>
