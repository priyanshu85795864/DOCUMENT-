# DOCUMENT-<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Krishna Docs</title>
    <style>
        body {
            background: linear-gradient(to right, #ffcc00, #ff9900);
            text-align: center;
            font-family: 'Poppins', sans-serif;
            color: #fff;
            margin: 0;
            padding: 0;
        }
        .welcome {
            position: fixed;
            width: 100%;
            height: 100vh;
            background: linear-gradient(to right, #ffcc00, #ff9900);
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            animation: fadeIn 2s;
            z-index: 999;
        }
        .welcome img {
            width: 200px;
            border-radius: 50%;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.5);
        }
        h1 {
            font-size: 3rem;
            font-weight: bold;
            animation: fadeIn 2s;
        }
        .fade-out {
            animation: fadeOut 2s forwards;
        }
        @keyframes fadeOut {
            100% { opacity: 0; visibility: hidden; }
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .container {
            display: none;
            margin-top: 20px;
            padding: 20px;
            max-width: 600px;
            margin: auto;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.3);
        }
        #krishnaHeader {
            width: 100%;
            max-height: 200px;
            border-radius: 15px;
            box-shadow: 0px 0px 15px rgba(0, 0, 0, 0.3);
        }
        button {
            background-color: #ff6600;
            color: white;
            border: none;
            padding: 12px 20px;
            margin: 10px;
            font-size: 1rem;
            cursor: pointer;
            border-radius: 8px;
            transition: 0.3s;
            font-weight: bold;
        }
        button:hover {
            background-color: #cc5500;
        }
        .login-form, .upload-section {
            display: none;
            margin-top: 20px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.3);
        }
        input {
            padding: 12px;
            margin: 10px;
            border-radius: 5px;
            border: none;
            width: 90%;
            font-size: 1rem;
        }
    </style>
</head>
<body>
    <div class="welcome" id="welcomeScreen">
        <img src="krishna.jpg" alt="Lord Krishna">
        <h1 id="nameAnimation">Priyanshu Mishra</h1>
    </div>

    <div class="container" id="mainContent">
        <img id="krishnaHeader" src="krishna.jpg" alt="Lord Krishna">
        <h2>Welcome to Krishna Docs</h2>
        <button onclick="showLogin()">Login</button>
    </div>

    <div class="login-form" id="loginForm">
        <h3>Login</h3>
        <input type="text" id="username" placeholder="Enter username">
        <input type="password" id="passcode" placeholder="Enter passcode">
        <button onclick="login()">Submit</button>
        <button onclick="forgotPasscode()">Forgot Passcode?</button>
    </div>

    <div class="upload-section" id="uploadSection">
        <h3>Upload Your Document</h3>
        <input type="file" id="documentInput">
        <button onclick="uploadDocument()">Upload</button>
        <h3>Stored Documents</h3>
        <ul id="documentList"></ul>
    </div>

    <script>
        setTimeout(() => {
            document.getElementById('welcomeScreen').classList.add('fade-out');
            document.getElementById('mainContent').style.display = 'block';
        }, 3000);

        function showLogin() {
            document.getElementById('mainContent').style.display = 'none';
            document.getElementById('loginForm').style.display = 'block';
        }

        function login() {
            let username = document.getElementById('username').value;
            let passcode = document.getElementById('passcode').value;
            if (username && passcode) {
                document.getElementById('loginForm').style.display = 'none';
                document.getElementById('uploadSection').style.display = 'block';
            } else {
                alert("Please enter username and passcode.");
            }
        }

        function forgotPasscode() {
            alert("Feature coming soon!");
        }

        function uploadDocument() {
            let fileInput = document.getElementById('documentInput');
            let file = fileInput.files[0];
            if (file) {
                let listItem = document.createElement('li');
                let link = document.createElement('a');
                link.href = URL.createObjectURL(file);
                link.download = file.name;
                link.textContent = file.name;
                listItem.appendChild(link);
                document.getElementById('documentList').appendChild(listItem);
                alert("Document uploaded successfully!");
            } else {
                alert("Please select a file.");
            }
        }
    </script>
</body>
</html>
