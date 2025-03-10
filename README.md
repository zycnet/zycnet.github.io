<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>zyc的个人网站</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            background-color: #15202B;
            color: white;
        }
        .container {
            margin-top: 2.5vh;
            padding-left: 5vw;
            padding-right: 5vw;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #15202B;
            padding: 1vh;
        }
        nav a {
            font-size: 1.8vh;
            color: #1DA1F2;
            text-decoration: none;
            margin-right: 10px;
        }
        nav a:hover {
            font-weight: bold;
            color: #FFFFFF;
        }
        .login-register {
            display: flex;
            gap: 10px;
        }
        .btn-login, .btn-register {
            padding: 1vh 3vh;
            border-radius: 5px;
            color: white;
            border: none;
            cursor: pointer;
        }
        .btn-login {
            background-color: #1DA1F2;
        }
        .btn-register {
            background-color: #000;
        }
        .main-content {
            display: flex;
            gap: 40px;
        }
        .sidebar {
            width: 20%;
            background-color: #F9F4E9;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .notes h2, .recent-posts h2 {
            font-size: 2.5vh;
            color: black;
        }
        .note-card {
            background-color: #F9F4E9;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            transition: border 0.3s;
        }
        .note-card:hover {
            border: 1px solid #E1BE97;
        }
        .post-item img {
            width: 500px;
            height: 120px;
            object-fit: cover;
            border-radius: 10px;
        }
        .post-item h3 {
            font-size: 2.5vh;
            color: black;
        }
        .post-item p {
            font-size: 1.5vh;
            color: black;
        }
        .content {
            width: 80%;
            background-color: #F9F4E9;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        .announcement {
            font-size: 2vh;
            color: #664401;
            padding-left: 20%;
            padding-top: 15%;
        }
        .blog-title {
            font-size: 2vh;
            color: #1DA1F2;
            padding-left: 20%;
            padding-top: 15%;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <a href="#home">主页</a>
            <a href="#recommended-websites">推荐网站</a>
            <a href="#recommended-software">推荐软件名称</a>
            <a href="#contact">联系</a>
            <a href="#feedback">问题反馈</a>
            <a href="#my-account">我的</a>
        </nav>
        <div class="login-register">
            <button class="btn-login" onclick="showLogin()">登录</button>
            <button class="btn-register" onclick="showRegister()">注册账号</button>
        </div>
    </header>

    <div id="loginModal" style="display:none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: rgba(0, 0, 0, 0.5); z-index: 1;">
        <div style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); background-color: white; padding: 20px; border-radius: 10px;">
            <h2>登录</h2>
            <input type="text" id="username" placeholder="用户名" required><br><br>
            <input type="password" id="password" placeholder="密码" required><br><br>
            <button onclick="login()">登录</button>
        </div>
    </div>

    <div id="registerModal" style="display:none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background-color: rgba(0, 0, 0, 0.5); z-index: 1;">
        <div style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); background-color: white; padding: 20px; border-radius: 10px;">
            <h2>注册账号</h2>
            <input type="text" id="newUsername" placeholder="新用户名" required><br><br>
            <input type="password" id="newPassword" placeholder="新密码" required><br><br>
            <button onclick="register()">完成注册</button>
        </div>
    </div>

    <div class="container">
        <section class="main-content">
            <aside class="sidebar">
                <div class="notes">
                    <h2>我的笔记</h2>
                    <div class="note-card">
                        <p>纪录1</p>
                        <p>日期：1</p>
                    </div>
                    <div class="note-card">
                        <p>纪录2</p>
                        <p>日期：2</p>
                    </div>
                    <div class="note-card">
                        <p>纪录3</p>
                        <p>日期：3</p>
                    </div>
                </div>
            </aside>
            <article class="content">
                <div class="announcement blog-title">
                    <h1>你好</h1>
                </div>
                <div class="recent-posts">
                    <h2>最近博客</h2>
                    <div class="post-item">
                        <img src="https://via.placeholder.com/500x120" alt="Blog Post Image">
                        <h3>博客标题1</h3>
                        <p>这是一个简短的博客描述。</p>
                    </div>
                    <div class="post-item">
                        <img src="https://via.placeholder.com/500x120" alt="Blog Post Image">
                        <h3>博客标题2</h3>
                        <p>这是另一个简短的博客描述。</p>
                    </div>
                </div>
            </article>
        </section>
    </div>

    <script>
        let users = [];
        function showLogin() {
            document.getElementById('loginModal').style.display = 'block';
        }

        function showRegister() {
            document.getElementById('registerModal').style.display = 'block';
        }

        function register() {
            const username = document.getElementById('newUsername').value;
            const password = document.getElementById('newPassword').value;

            if (users.find(user => user.username === username)) {
                alert("用户名已存在");
                return;
            }

            users.push({ username, password });
            alert("注册成功！");
            document.getElementById('registerModal').style.display = 'none';
        }

        function login() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;

            const user = users.find(u => u.username === username && u.password === password);

            if (user) {
                alert("登录成功！");
                document.getElementById('loginModal').style.display = 'none';
            } else {
                alert("用户名或密码错误");
            }
        }
    </script>
</body>
</html>
