<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laptop Store Landing Page</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f8f9fa;
            color: #333;
            line-height: 1.6;
        }

        section {
            padding: 60px 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 20px;
            background-color: #fff;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            position: sticky;
            top: 0;
            z-index: 100;
            flex-wrap: wrap;
            gap: 15px;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: bold;
            color: #333;
        }

        .logo span {
            color: #4f46e5;
        }

        .search-container {
            display: flex;
            align-items: center;
            gap: 10px;
            flex: 1;
            max-width: 400px;
        }

        .search-container input {
            flex: 1;
            padding: 8px 12px;
            border: 1px solid #ddd;
            border-radius: 5px;
            outline: none;
        }

        .search-wrapper {
            position: relative;
        }

        .search-btn {
            background-color: #4f46e5;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .search-btn:hover {
            background-color: #4338ca;
        }

        .tooltip {
            position: absolute;
            top: 120%;
            left: 50%;
            transform: translateX(-50%);
            background-color: #333;
            color: #fff;
            padding: 5px 10px;
            border-radius: 4px;
            font-size: 0.8rem;
            white-space: nowrap;
            opacity: 0;
            visibility: hidden;
            transition: opacity 0.3s, visibility 0.3s;
            pointer-events: none;
        }

        .tooltip::after {
            content: '';
            position: absolute;
            bottom: 100%;
            left: 50%;
            margin-left: -5px;
            border-width: 5px;
            border-style: solid;
            border-color: transparent transparent #333 transparent;
        }

        .search-wrapper:hover .tooltip {
            opacity: 1;
            visibility: visible;
        }

        .nav-links {
            display: flex;
            align-items: center;
            gap: 20px;
        }

        .nav-links a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: #4f46e5;
        }

        .cart-icon {
            position: relative;
            font-size: 1.2rem;
            cursor: pointer;
        }

        .cart-count {
            position: absolute;
            top: -8px;
            right: -10px;
            background-color: #dc3545;
            color: white;
            font-size: 0.7rem;
            font-weight: bold;
            padding: 2px 6px;
            border-radius: 50%;
            transition: transform 0.2s ease;
        }

        .hero-section {
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: #f1f5ff;
            padding: 60px 40px;
            border-radius: 15px;
            margin-top: 20px;
            gap: 30px;
            flex-wrap: wrap;
        }

        .hero-content {
            flex: 1;
            min-width: 300px;
        }

        .hero-content h1 {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: #1a1a1a;
        }

        .hero-content p {
            font-size: 1.1rem;
            color: #555;
            margin-bottom: 25px;
        }

        .hero-image {
            flex: 1;
            min-width: 300px;
            text-align: center;
        }

        .hero-image img {
            max-width: 100%;
            border-radius: 10px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }

        h2 {
            font-size: 2rem;
            margin-bottom: 10px;
            text-align: center;
        }

        section > p {
            text-align: center;
            color: #666;
            margin-bottom: 40px;
        }

        .products-container {
            display: flex;
            flex-wrap: wrap;
            gap: 25px;
            justify-content: center;
        }

        .product-card {
            background: #fff;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            overflow: hidden;
            width: 280px;
            display: flex;
            flex-direction: column;
            transition: transform 0.3s ease;
        }

        .product-card:hover {
            transform: translateY(-5px);
        }

        .image-container {
            position: relative;
            width: 100%;
            height: 180px;
        }

        .image-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .label {
            position: absolute;
            top: 10px;
            left: 10px;
            padding: 5px 12px;
            border-radius: 5px;
            font-size: 0.8rem;
            font-weight: bold;
            color: #fff;
            z-index: 10;
        }

        .label.available { background-color: #28a745; }
        .label.not-available { background-color: #dc3545; }

        .product-info {
            padding: 20px;
            display: flex;
            flex-direction: column;
            flex-grow: 1;
        }

        .product-info h3 { margin-bottom: 10px; }

        .product-info p {
            color: #666;
            font-size: 0.9rem;
            margin-bottom: 15px;
            flex-grow: 1;
        }

        .price {
            font-size: 1.2rem;
            font-weight: bold;
            color: #333;
            margin-bottom: 15px;
        }

        .buy-btn {
            background-color: #4f46e5;
            color: white;
            border: none;
            padding: 10px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.3s;
        }

        .buy-btn:hover { background-color: #4338ca; }

        .upgrade-section {
            background-color: #eef2ff;
            border-radius: 15px;
            text-align: center;
            padding: 60px 20px;
            margin-bottom: 60px;
        }

        .upgrade-content {
            max-width: 600px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .upgrade-content p { margin-bottom: 25px; }

        .cta-btn {
            background-color: #4f46e5;
            color: white;
            padding: 12px 30px;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            cursor: pointer;
            font-weight: bold;
            transition: background 0.3s;
        }

        .cta-btn:hover { background-color: #4338ca; }

        .section-header {
            text-align: center;
            margin-bottom: 40px;
        }

        .features-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            justify-content: center;
        }

        .feature-card {
            background: #fff;
            padding: 30px 20px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.05);
            width: 300px;
            text-align: center;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .feature-icon {
            font-size: 2.5rem;
            color: #4f46e5;
            margin-bottom: 15px;
        }

        .feature-card h3 { margin-bottom: 10px; }
        .feature-card p { color: #666; font-size: 0.9rem; }

        footer {
            background-color: #1e1e2f;
            color: #fff;
            padding: 40px 20px 20px;
            margin-top: 40px;
        }

        .footer-content {
            max-width: 800px;
            margin: 0 auto;
            text-align: center;
        }

        .newsletter h3 {
            margin-bottom: 10px;
            font-size: 1.5rem;
        }

        .newsletter p {
            color: #aaa;
            margin-bottom: 20px;
            font-size: 0.9rem;
        }

        .newsletter-form {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 30px;
            flex-wrap: wrap;
        }

        .newsletter-form input {
            padding: 10px 15px;
            border: none;
            border-radius: 5px;
            width: 300px;
            outline: none;
        }

        .newsletter-form button {
            padding: 10px 20px;
            background-color: #4f46e5;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }

        .footer-bottom {
            border-top: 1px solid #333;
            padding-top: 20px;
            color: #888;
            font-size: 0.8rem;
        }

        .help-btn {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background-color: #4f46e5;
            color: white;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            transition: transform 0.3s ease;
        }

        .help-btn:hover { transform: scale(1.1); }

        @media (max-width: 992px) {
            .hero-content h1 { font-size: 2rem; }
            .navbar { justify-content: center; }
            .search-container { order: 3; max-width: 100%; width: 100%; margin-top: 10px; }
            .nav-links { order: 2; }
        }

        @media (max-width: 768px) {
            section { padding: 40px 15px; }
            
            .navbar {
                flex-direction: column;
                align-items: center;
            }

            .nav-links {
                flex-wrap: wrap;
                justify-content: center;
                gap: 15px;
            }

            .hero-section {
                flex-direction: column;
                text-align: center;
                padding: 40px 20px;
            }

            .product-card, .feature-card {
                width: 100%;
                max-width: 350px;
            }
            
            .upgrade-section {
                padding: 40px 15px;
                margin: 0 15px 40px 15px;
            }
            
            .help-btn {
                width: 50px;
                height: 50px;
                bottom: 20px;
                right: 20px;
                font-size: 1.2rem;
            }

            .newsletter-form input {
                width: 100%;
            }
        }
    </style>
</head>
<body>

    <nav class="navbar">
        <div class="logo">Stack<span>X5</span> Store</div>
        
        <div class="search-container">
            <input type="text" placeholder="Search for your favorite laptop...">
            <div class="search-wrapper">
                <button class="search-btn">Search</button>
                <span class="tooltip">Search for laptops</span>
            </div>
        </div>

        <div class="nav-links">
            <a href="#">Home</a>
            <a href="#">Laptops</a>
            <a href="#">About</a>
            <a href="#">Contact</a>
            <div class="cart-icon">
                <i class="fa-solid fa-cart-shopping"></i>
                <span class="cart-count" id="cart-count">0</span>
            </div>
        </div>
    </nav>

    <section class="hero-section">
        <div class="hero-content">
            <h1>Find Your Perfect Laptop</h1>
            <p>Discover laptops for studying, working, and gaming. Find the right laptop for your everyday needs.</p>
            <button class="cta-btn">Explore Laptops</button>
        </div>
        <div class="hero-image">
            <img src="https://via.placeholder.com/500x300?text=Laptop+Hero+Image" alt="Laptop Hero">
        </div>
    </section>

    <section class="products-section">
        <h2>Our Laptops</h2>
        <p>Choose your next laptop from our collection.</p>
        
        <div class="products-container">
            <div class="product-card">
                <div class="image-container">
                    <img src="https://via.placeholder.com/300x200?text=HP+Pavilion" alt="HP Pavilion">
                    <span class="label available">Available</span>
                </div>
                <div class="product-info">
                    <h3>HP Pavilion</h3>
                    <p>A great laptop for studying, browsing, and everyday tasks.</p>
                    <span class="price">$550</span>
                    <button class="buy-btn">Buy Now</button>
                </div>
            </div>

            <div class="product-card">
                <div class="image-container">
                    <img src="https://via.placeholder.com/300x200?text=Dell+Inspiron" alt="Dell Inspiron">
                    <span class="label not-available">Not Available</span>
                </div>
                <div class="product-info">
                    <h3>Dell Inspiron</h3>
                    <p>A practical choice for work, online classes, and productivity.</p>
                    <span class="price">$650</span>
                    <button class="buy-btn">Buy Now</button>
                </div>
            </div>

            <div class="product-card">
                <div class="image-container">
                    <img src="https://via.placeholder.com/300x200?text=Lenovo+IdeaPad" alt="Lenovo IdeaPad">
                    <span class="label available">Available</span>
                </div>
                <div class="product-info">
                    <h3>Lenovo IdeaPad</h3>
                    <p>A simple and reliable laptop for everyday use.</p>
                    <span class="price">$600</span>
                    <button class="buy-btn">Buy Now</button>
                </div>
            </div>

            <div class="product-card">
                <div class="image-container">
                    <img src="https://via.placeholder.com/300x200?text=ASUS+Vivobook" alt="ASUS Vivobook">
                    <span class="label available">Available</span>
                </div>
                <div class="product-info">
                    <h3>ASUS Vivobook</h3>
                    <p>A stylish and powerful laptop for work and play.</p>
                    <span class="price">$700</span>
                    <button class="buy-btn">Buy Now</button>
                </div>
            </div>
        </div>
    </section>

    <section class="upgrade-section">
        <div class="upgrade-content">
            <h2>Upgrade Your Setup Today!</h2>
            <p>Find the laptop that matches your needs. Explore our collection and choose your next device.</p>
            <button class="cta-btn">View Collection</button>
        </div>
    </section>

    <section class="why-choose-us">
        <div class="section-header">
            <h2>Why Choose StackX5 Store?</h2>
            <p>We provide the best experience for our customers.</p>
        </div>
        
        <div class="features-container">
            <div class="feature-card">
                <i class="fa-solid fa-laptop-medical feature-icon"></i>
                <h3>Quality Products</h3>
                <p>We offer only the highest quality laptops from trusted brands.</p>
            </div>
            <div class="feature-card">
                <i class="fa-solid fa-tags feature-icon"></i>
                <h3>Great Prices</h3>
                <p>Competitive pricing to ensure you get the best value for your money.</p>
            </div>
            <div class="feature-card">
                <i class="fa-solid fa-headset feature-icon"></i>
                <h3>Customer Support</h3>
                <p>Our dedicated team is here to help you 24/7 with any inquiries.</p>
            </div>
        </div>
    </section>

    <footer>
        <div class="footer-content">
            <div class="newsletter">
                <h3>Stay Updated!</h3>
                <p>Subscribe to receive new arrivals and special offers.</p>
                <form class="newsletter-form" onsubmit="event.preventDefault();">
                    <input type="email" placeholder="Enter your email address" required>
                    <button type="submit">Subscribe</button>
                </form>
            </div>
            <div class="footer-bottom">
                &copy; 2024 StackX5 Store. All Rights Reserved.
            </div>
        </div>
    </footer>

    <button class="help-btn" aria-label="Help">
        <i class="fa-solid fa-question"></i>
    </button>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const buyButtons = document.querySelectorAll('.buy-btn');
            const cartCountElement = document.getElementById('cart-count');
            let cartCount = 0;

            buyButtons.forEach(button => {
                button.addEventListener('click', () => {
                    cartCount++;
                    cartCountElement.textContent = cartCount;
                    
                    cartCountElement.style.transform = 'scale(1.3)';
                    setTimeout(() => {
                        cartCountElement.style.transform = 'scale(1)';
                    }, 200);
                });
            });
        });
    </script>
</body>
</html>
