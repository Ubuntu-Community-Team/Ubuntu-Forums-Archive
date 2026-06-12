---
title: "HP Scanjet 3800 - How to make it work"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-17
Hi, I have a HP Scanjet scanner which I would like to use in Ubuntu. The problem is that it won't work for me. I have tried using xsane but it was a bit confusing and it kept recognizing a scanner called Medion 7134 and I dont know what that is. My PC is a Medion PC but the scanner is from HP.

I then tried to install another program caleld scanner utility, that also recognized the medion scanner, but it also recognized my all-in-one hp printer, that also has a scanner built in.

Does anyone know what the problem is. I guess it's a driver problem, bur how do I find out?

---

### Post by dhruva023 on 2007-06-17
try to use HPLIP Tool box.

it should be in your menu.

if its not then, edit you menu,  you will see the option to add it.

---

### Post by maddog39 on 2007-06-17
Yes, the HPLIP tool is under System > Administration. I know its under the system menu for sure, just take a gander and see where it is. :P

---

### Post by kasperbs on 2007-06-18
Thank you very much for your replies. I tried to acces HPLIP but it could only see my all in one printer. When I try to scan for new devices, my scanner is making a sound like it is resuming from standby or something, but HPLIP doesn't recognize it! The same happens when I go to setup new device from within HPLIP and I also get a message saying that no new devices were found. I can add it manually from that dialog box but it requires me to enter the usb bus id and the device id, but I don't know where to find that, and I dont know if it will work..

Hope you got some sugestions

Thanks

---

### Post by phytophile on 2007-06-19
The 3800 is not in the list of supported scanners in HLIP. But it is in the SANE list and you can download a debian package from [http://sourceforge.net/projects/hp3900-series/](http://sourceforge.net/projects/hp3900-series/). Once installed, xsane can see and work the scanner, but the images are all scrambled. The SANE site says "works at resolutions less than 600 dpi" but it wouldn't work even at 50 dpi. I guess I'll just have to wait for the next  version, or beat HP around the head to get them to release details of how the 3900 series works. (Unless anyone has any other ideas)

Martin

---

### Post by kasperbs on 2007-06-20
thanks did the job

---

### Post by Ghydda on 2007-06-24
Tried the 3900-series with my 3800 flatbed and I now got basic scanning capability. Instant recognition of the scanner and it just works.

Have yet to explore what features, if any, are broken or buggy or missing.


But so far I'm a happy camper :p


/Ghydda

---

### Post by visarz on 2007-07-15
Dude I installed those 3900 drivers for my 3800, obviuously it recognizes it but I have trouble with the basic commands for scanning :S 
can anyone please tell me how can I scan now?

---

