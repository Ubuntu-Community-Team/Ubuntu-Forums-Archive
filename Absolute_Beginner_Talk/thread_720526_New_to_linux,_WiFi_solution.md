---
title: "New to linux, WiFi solution?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Col. Mustard on 2008-03-10
Hi all, I'm pretty new to linux, and honestly,  I can't do much of what I need my PC to do without internet access... And it seems that getting WiFi to work in linux is nothing short of sorcery! :-k Going from the simple 100% graphical interface of windows XP and vista, where I've never had to touch a single line of code, to looking online about how to get WiFi working and seeing these guides explaining compiling tar, using terminal windows, manually editing and coding things with text-only windows like old DOS stuff. is it really this difficult to just connect to the internet? Well... anyways, let me explain my problem. I have a PC that I built myself, with a 320GB SATA drive running Vista Ultimate, nVidia gforce 8800GT 512 pci-e x16 GPU, core2 duo 1.86 ghz per core, SB X-Fi xtreme gamer sound card, Asus mobo and 4GB of DDR2 667. Also, the wireless adapter I use is a Belkin USB adapter, model F5D9050. I've tried installing openSUSE 10.3, Mandriva One, and Kubuntu 7.10... the closest thing was using Kubuntu, which I really liked BTW, and it just recognised my adapter and I was able to get internet access working by disabling my network encription and making it open. but then I turned my PC off and started it up the next day, and it wouldn't boot into Kubuntu, something about nvidia... I then reinstalled SUSE instead, and I'm now trying to get that to work... I've gone into the control panel-like thing and added a network card, picked wireless, entered my SSID, etc. but it won't pick up internet access. I keep reading something about ndiswrapper, but when I try to read how to install it my head starts to spin... I figured this forum being called "Absolute Beginner Talk" would be a good place for me to start! Anyone that offers any assistance would be greatly appreciated... I would love to be able to use linux, and from what I've used of it, I really like it, but a PC is just useless to me without internet... so hopefully this is a fixable issue [-o< Thanks for reading!

---

### Post by EnergySamus on 2008-03-10
I had a Wi-Fi issue when I first installed Ubuntu. I can help, but I need to know what type of wi-fi it is (broadcom, etc.)

Boot into the Live CD in Ubuntu and access the terminal from the Applications menu. Once you are in the terminal, type in: lspci
(No Caps or Periods)

If you see anything that says broadcom, come back and tell me.

Good Luck!
EnergySamus

P.S. Ubuntu is easier than you think, you just have to get used to it... I was a beginner, I know what you mean!!!
P.S.S. If you know that your Wi-Fi is Broadcom, here is a link to get it your Wi-Fi working:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

---

### Post by kwacka on 2008-03-10
is [http://ubuntuforums.org/showthread.php?t=400236&highlight=F5D9050](http://ubuntuforums.org/showthread.php?t=400236&highlight=F5D9050)

any use?

---

### Post by Col. Mustard on 2008-03-10
Well the strange thing is, the first time I installed Kubuntu, I somehow managed to get the wireless working... I was finally able to get google.com open and it worked like a charm, but it was 6:30AM and I don't remember anything I did to get it to work, as I was up for almost 10 hours straight reading guides and searching google. Even now, I can type in iwconfig and I get info about 802.11g and ip addresses and whatnot, but when I open the browser it says "unknown host google.com" or whatever I try to load. Also, the light on my wireless adapter is on... I'm assuming that Kubuntu recognizes it, but I can't figure out why I can't actually get online :s Thanks guys for your help!

---

### Post by EnergySamus on 2008-03-10
Glad that I could help!
?: Did that link help?

EnergySamus

---

### Post by Col. Mustard on 2008-03-11
Thanks for your help, and yes, I'm pretty sure it helped... my wifi connection works now, after more hours of seemingly meaningless tinkering. though it still doesn't seem right... I have internet access, and thats what I was after :p

---

### Post by EnergySamus on 2008-03-11
No Problem man, always love to help!

EnergySamus

---

