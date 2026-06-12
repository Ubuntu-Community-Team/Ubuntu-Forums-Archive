---
title: "Some final problems with my Ubuntu install"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by BijuMathew on 2007-11-09
Hi all,
 Ive recently decided to go the Open Source way and decided to install Ubuntu 7.10 Gutsy Gibbon (AMD64 version) . I was very pleased with the install and everything went smoothly. I first had some problems with sound (My line in wouldnt work) so I followed the troubleshooting thread for sound and recompiled ALSA and it worked fine. Now I only have three more problems and I am good to go on my install. 

1. I have a TV Tuner TechCom SSD-TV 670 (it is based on the Philips 7130 chipset and I can't get it to run. I was able to get video so far by using the commands

sudo rmmod saa7134
sudo modprobe saa7134 card=3 tuner=69

However this does not give audio at all. The funny thing is that once I load the saa7134 module if I were to remove the module using the rmmod command I do get sound :D . But then I lose the video of course. I have so far tried Mythtv, TvTine, XAWtv and the only application I got to work was tvtime but it has the above problems. Ive been thinking of buying a new tv tuner card but the questiopn is whether it would work with Ubuntu too. The ones I have access to are cards from Pinnacle and Pixelview. IM not sure of the Pixelview brand but the Pinnacle ones are called PInnacle PCTV PCI. The dealer doesnt know what chipset it is using and hence I can't give you more information about that. There are USB ones also available but I recall someone saying that it might not work. Any ideas f what I should do? 

2. I have a mobile phone Nokia 6681 which I used to sync with Outlook using their PC Suite. Ive been trying to get similair functionality in Ubuntu. But I seemt o be failing at all my attempts. Ive tried gnokii and wammu. Using Bluetooth I cant connect but using the USB line it does identify the phone and can connect to it, but thats it. It wont do anything beyond that. WOuld appreciate on some insight on what to do to correct this. Using Bluetooth I can connect to the phone. An explorer like view comes up with two folders which say c: and e:. BY the way would Nokia PC Suite work over Wine? 

3. I have a game called Chessmaster 10. I have tried configuring it with Wine and I havent any luck with this. It brings up the beginning menu but half the screen is black and the other half shows the bottom half of the game menu. Definitely I could do without this btu I would love to get the other problems working. 

I could run and post any output as needed on this thread. Hope someone can guide me to get this to work. 

Here is my system specs just in case it helps.

AMD 4400 AM2 
Asus M2N MX-SE
2 GB Ram
SATA 80 GB Drive
IDE 80 GB Drive
TechCom Tv Tuner Card
17 ' LG 700E Monitor
56k External Modem. 

Thanks in advance,
Biju Mathew

---

### Post by Dripbagulhos on 2007-11-09
Hi BijuMathew,

Unfortunatelly I can not help with the two first questions, howhever you could give Cedega ([http://www.transgaming.com/](http://www.transgaming.com/)) a try. Even if Chessmaster 10 is not one of the "official" game supported, there is still a chance it works. If you compile cedega from source it is free of charge, if you whant to install all features you have to pay US$ 5,00/month.

---

### Post by hyper_ch on 2007-11-09
is chessmaster using directx? If not, you could install windows in vmware or vbox and use it there.

---

### Post by Dripbagulhos on 2007-11-09
> **hyper_ch said:**
> is chessmaster using directx? If not, you could install windows in vmware or vbox and use it there.

Hi hyper_ch,

Have you ever tried to do this? :-) I though VMware does not support 3d accelletarion, even if it is OppenGL. I always use to try wine first and then Cedega. But for game purposes I keep a small partition with native windows xp in my machine.

---

### Post by hyper_ch on 2007-11-09
that's why I asked whether it's using DirectX... Ego-Shooters normally do but besides them I don't see why a chessprogram should use it...

---

### Post by BijuMathew on 2007-11-09
> is chessmaster using directx? If not, you could install windows in vmware or vbox and use it there.

Unforutnately it does have the option to use DirectX. but thereis a way to set it to use OpenGL. it uses quite alot of different chess sets and hence the need for better graphics I guess. 

My friend tried cedega and he said that ti closes out before the intro moview unfortunately .

---

### Post by atomkarinca on 2007-11-09
1. [https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia](https://wiki.ubuntu.com/HardwareSupportComponentsMultimedia) on this page you can see a list of compatible tv cards. i couldn't see your tv card brand, but for purchasing a new one, this will help you whether it will work or not. you do not have to know the chipset, just the model of the card.

2. i don't know about synchronization but about nokia pc suite, this site tells that it's not working via wine: [http://appdb.winehq.org/appview.php?iVersionId=4657&iTestingId=2703](http://appdb.winehq.org/appview.php?iVersionId=4657&iTestingId=2703)

3. for chessmaster 10, here's a guide how they got it working: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4502&iTestingId=4748](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4502&iTestingId=4748)

by the way [wine application database]("http://appdb.winehq.org") is a very good source for your wine programs.

---

### Post by BijuMathew on 2007-11-09
> 1. [https://wiki.ubuntu.com/HardwareSupp...entsMultimedia](https://wiki.ubuntu.com/HardwareSupp...entsMultimedia) on this page you can see a list of compatible tv cards. i couldn't see your tv card brand, but for purchasing a new one, this will help you whether it will work or not. you do not have to know the chipset, just the model of the card.

Thank you will check this site out for a new tv tuner card.

> 
2. i don't know about synchronization but about nokia pc suite, this site tells that it's not working via wine: [http://appdb.winehq.org/appview.php?...TestingId=2703](http://appdb.winehq.org/appview.php?...TestingId=2703)


Thanks again that definitely saved me time cause I was about to try installing it on Wine. I would love to get my phone to work in conjunction with Ubuntu. I really dont need the PC Suite . Just somethign that could get my contacts and calendar data. 

> 
3. for chessmaster 10, here's a guide how they got it working: [http://appdb.winehq.org/objectManage...TestingId=4748](http://appdb.winehq.org/objectManage...TestingId=4748)


I did the steps according to what the author and the other posters said. Unfortunately it doesnt work like the user said. Maybe it might have been possible for his distro which he was using I guess . 

Thanks for the suggestions.

---

