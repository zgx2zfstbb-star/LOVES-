<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Wach Katbghini?</title>
<style>
body {
    margin:0;
    padding:0;
    font-family: 'Arial', sans-serif;
    background: linear-gradient(to bottom, #ffe6f0, #ffcce0);
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    height:100vh;
    overflow:hidden;
}

h1 {
    font-size:2.5rem;
    font-weight:bold;
    color:#d42c6b;
    margin-bottom:30px;
    text-align:center;
}

.bear {
    font-size:120px;
    text-align:center;
    animation: bounce 2s infinite;
    margin-bottom:20px;
}

@keyframes bounce {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-20px); }
}

.buttons {
    display:flex;
    gap:20px;
    margin-top:20px;
}

.btn {
    font-size:1.2rem;
    font-weight:bold;
    padding:15px 30px;
    border-radius:50px;
    border:none;
    cursor:pointer;
    color:white;
    display:flex;
    align-items:center;
    gap:10px;
    box-shadow: 0 5px 15px rgba(0,0,0,0.2);
    transition: transform 0.3s, box-shadow 0.3s;
    position:relative;
    overflow:hidden;
}

.btn.ah { background-color:#ff4d6d; }
.btn.la { background-color:#6c6c6c; }

.messages {
    margin-top:30px;
    text-align:center;
    font-size:1.5rem;
    font-weight:bold;
    color:#d42c6b;
    min-height:60px;
}

.heart {
    position:absolute;
    font-size:20px;
    color:#ff4d6d;
    animation: floatUp 4s linear forwards;
    opacity:0;
}

@keyframes floatUp {
    0% { transform: translateY(0) scale(1); opacity:1; }
    100% { transform: translateY(-300px) scale(1.5); opacity:0; }
}
</style>
</head>
<body>

<div class="bear">🧸</div>
<h1>Wach Katbghini?</h1>

<div class="buttons">
    <button class="btn ah">AH ❤️</button>
    <button class="btn la">LA 😢</button>
</div>

<div class="messages" id="messages"></div>

<script>
const ahButton = document.querySelector('.btn.ah');
const laButton = document.querySelector('.btn.la');
const messagesDiv = document.getElementById('messages');

const ahMessages = [
    "ta ana kanbghik ALI 💌",
    "3arfa katsta eliya 😘",
    "ga3 hada hob 💖",
    "ALI hbiba🥹"
];

const laMessages = [
    "Wax Mat2akad🥺",
    "Nslkhek Gol AH"
];

let ahIndex = 0;
let laIndex = 0;

// إنشاء قلب
function createHeart(x,y){
    const heart = document.createElement('div');
    heart.classList.add('heart');
    heart.style.left = x+'px';
    heart.style.top = y+'px';
    heart.textContent = '💖';
    document.body.appendChild(heart);
    setTimeout(()=>heart.remove(),4000);
}

// قلوب تطير
function floatHearts(count=10){
    for(let i=0;i<count;i++){
        const x = Math.random() * window.innerWidth;
        const y = window.innerHeight - 50;
        setTimeout(()=>createHeart(x,y),i*150);
    }
}

// عند الضغط على AH
ahButton.addEventListener('click',()=>{
    // ظهور رسالة واحدة فقط
    messagesDiv.textContent = ahMessages[ahIndex];
    floatHearts(5);

    // تكبير الزر تدريجياً
    let currentScale = Number(getComputedStyle(ahButton).transform.split(',')[3]) || 1;
    ahButton.style.transform = `scale(${currentScale + 0.1})`;

    // زيادة المؤشر
    ahIndex = (ahIndex + 1) % ahMessages.length;
});

// عند الضغط على LA
laButton.addEventListener('click',()=>{
    messagesDiv.textContent = laMessages[laIndex];
    floatHearts(3);

    // تكبير الزر تدريجياً
    let currentScale = Number(getComputedStyle(laButton).transform.split(',')[3]) || 1;
    laButton.style.transform = `scale(${currentScale + 0.1})`;

    laIndex = (laIndex + 1) % laMessages.length;
});
</script>

</body>
</html>
