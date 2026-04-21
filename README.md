THE STANDARD - PDF Compressor 📄⚡️

ระบบย่อขนาดไฟล์ PDF สำหรับใช้งานภายในองค์กร THE STANDARD (เฉพาะผู้ที่มีอีเมลโดเมน @thestandard.co) โดยระบบถูกออกแบบมาให้เน้น "ความปลอดภัยของข้อมูลสูงสุด" ผ่านการประมวลผลบนเครื่องของผู้ใช้ (Client-Side) 100% โดยไม่มีการอัปโหลดไฟล์เอกสารใดๆ ขึ้นสู่เซิร์ฟเวอร์

✨ ฟีเจอร์หลัก (Features)

🔒 Secure by Design: ประมวลผลและย่อขนาดไฟล์ผ่านเบราว์เซอร์ของผู้ใช้ (Client-Side) ข้อมูลไม่รั่วไหล

🔐 Google Authentication: จำกัดสิทธิ์การเข้าใช้งานเฉพาะบุคลากรที่มีอีเมล @thestandard.co เท่านั้น

🎛️ Adjustable Quality: สามารถเลือกระดับคุณภาพของการย่อไฟล์ได้ 3 ระดับ (ย่อให้เล็กที่สุด, แนะนำ/สมดุล, เน้นความคมชัด)

📱 Modern & Responsive UI: หน้าจอใช้งานง่าย ลากและวางไฟล์ (Drag & Drop) ได้ทันที ธีมสีแดง (CI: #e62227)

⚡️ Single-File App: โค้ดทั้งหมดจบในไฟล์ index.html เดียว ไม่ต้องมีเซิร์ฟเวอร์ Backend หรือฐานข้อมูล

🛠️ เทคโนโลยีที่ใช้ (Technologies)

Frontend: HTML5, JavaScript (ES6+), CSS3

Styling: Tailwind CSS (ผ่าน CDN)

Icons: Lucide Icons

PDF Processing:

PDF.js (อ่านและ Render ไฟล์ PDF ต้นฉบับ)

jsPDF (สร้างและบีบอัดไฟล์ PDF ใหม่)

Authentication: Google Identity Services (Google API)

🚀 การติดตั้งและการใช้งาน (Installation & Setup)

เนื่องจากระบบนี้เป็น Single-File Application คุณสามารถนำไปใช้งานได้ทันทีโดยไม่ต้อง Build หรือลง Dependencies ใดๆ เพิ่มเติม

1. การเตรียมไฟล์

คัดลอกไฟล์ index.html ไปวางไว้บน Web Hosting ของคุณ (เช่น GitHub Pages, Vercel, Netlify, Nginx, Apache หรืออัปโหลดเข้าเซิร์ฟเวอร์ภายในองค์กร)

2. การตั้งค่า Google OAuth (สำคัญ)

ปัจจุบันระบบมีการฝัง CLIENT_ID ของคุณไว้แล้ว แต่หากต้องการเปลี่ยนแปลง หรือนำไปใช้กับ Domain อื่นๆ ต้องดำเนินการดังนี้:

ไปที่ Google Cloud Console

สร้าง Project ใหม่ หรือเลือก Project ที่มีอยู่

ไปที่เมนู APIs & Services > Credentials

สร้าง OAuth client ID (ประเภท Web application)

ในช่อง Authorized JavaScript origins ให้เพิ่ม URL ของเว็บไซต์ที่คุณนำไฟล์นี้ไปโฮสต์ (เช่น https://tools.thestandard.co)

นำ Client ID ที่ได้มาแก้ไขในไฟล์ index.html บรรทัดที่ประมาณ 160:

const GOOGLE_CLIENT_ID = "ไอดีของคุณ.apps.googleusercontent.com";


3. การเปลี่ยน Domain องค์กร (ถ้ามี)

หากในอนาคตต้องการเปลี่ยนโดเมนที่อนุญาตให้เข้าใช้งาน สามารถแก้ไขตัวแปรนี้ในโค้ด (บรรทัดใกล้ๆ กับ GOOGLE_CLIENT_ID):

const ALLOWED_DOMAIN = "@thestandard.co";


⚙️ หลักการทำงานของการย่อ PDF (How it works)

Read & Render: ระบบจะใช้ pdf.js อ่านเอกสาร PDF ต้นฉบับ และแปลง (Render) แต่ละหน้าให้ออกมาเป็นรูปภาพ (Canvas)

Compress: ทำการดึงภาพจาก Canvas ออกมาในรูปแบบ JPEG โดยใช้อัตราส่วนการบีบอัด (Quality/Scale) ตามที่ผู้ใช้เลือก

Rebuild: นำรูปภาพที่ถูกบีบอัดแล้ว ไปสร้างเป็นหน้า PDF ใหม่ทีละหน้าด้วย jsPDF

Export: รวมเป็นไฟล์ PDF ใหม่ให้ผู้ใช้ดาวน์โหลด

(หมายเหตุ: วิธีนี้จะแปลงข้อความที่คลุมดำได้ใน PDF เดิมให้กลายเป็นรูปภาพ ซึ่งเหมาะสำหรับลดขนาดและป้องกันการก็อปปี้เนื้อหา)
