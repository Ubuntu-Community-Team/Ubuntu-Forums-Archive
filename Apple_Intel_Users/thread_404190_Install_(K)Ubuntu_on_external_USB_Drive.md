---
title: "Install (K)Ubuntu on external USB Drive"
date: 2007-04-08
forum: Apple Intel Users
---

### Post by koni2005 on 2007-04-08
Am I really the only one trying to install (K)Ubuntu on an external USB Drive? There seems to be noone who either has an idea how to do it or is willing to share his knowlegde...

Or am I simply to stupid to do it?

I have a 2.16 Ghz CoreDuo MacBook Pro with OSX and XP installed on the internal HD, refit is installed also.

What must I do, to install Ubuntu onto an external HD? It worked for a friend of mine, but he used opensuse, which supports EFI. Fedora Core 6 also seems to work - I havent tried it though.

Please!!!! Someone help me.

I also have problems booting or intsalling a feisty DVD or CD (both Kubuntu and Ubuntu).

In the MacBook Guide it said one should use the boot parameter lpj=8000000 for a 2 Ghz CoreDuo MacBook. What does lpj stand for? And what would be the appropriate value for a MacBook Pro - 2.16 Ghz CoreDuo (NOT Core2Duo!)

Thanks....

---

### Post by kvarley on 2007-04-08
I would love to do this too so that I could take Ubuntu into school.
This is how I would do it.

1. You will need a CD of Ubuntu. (the iso can be downloaded.)
2. You will need to boot from the CD. (Boot Settings)
3. You will next need to change your Bios settings so that the ext USB drive is see as the main drive.
4. Next you need to install Ubuntu. (It will install on the ext USB Drive because of the Bios settings.) 

Hope it works! :) 

-Vitium-

---

### Post by Chrisj303 on 2007-04-09
^There is no bios setting on a mac, mac's use EFI.

What problems are you (OP) having regarding booting off the Live CD/DVD? If you have rEFIt installed, that should pick it up. If it won't even boot by holding down C, then it sounds like a problem with your disc. I would try re-downloading it - it might just be corrupt.
How are you burning the .ISO? - I drag it into TOAST, then mount, then burn - should be fine.

---

### Post by koni2005 on 2007-04-10
Yes, I burn the ISO Images with Toast 8 - seems to work fine.

As for the booting problems, I do get to the menue where I can choos all the different options and the install / or start of the life CD runs smoothly in the beginning (Kubuntu Logo with moving strip below) After a while the graphics seem to get corrupted and there is a line of tiny green dots in the middle of the screen. It looks like fairly small scaled text messages or something, but they are not readable. Whe running the install process in text mode, the insaller freezes with Kernel Panik somewhere in the process.

Which would be the boot parameters for me to use for my configuration (MBP 2.16Ghz CoreDuo 2Gig of Ram (not Core2Duo) 100 Gig internal HD, ATI X1600 256MB. As external Drive I use a USB2 LACIE 2,5''.

Any help would be greately appreciated!!

Konrad

---

### Post by cyberdork33 on 2007-04-10
As far as I can tell (and I did some looking around), the lpj parameter is only for the MacBook, not MacBook Pro. I haven't seen anyone using it to boot a MacBook Pro. Have you tried booting without it?

---

### Post by cyberdork33 on 2007-04-10
Ok, I really looked hard and didn't find much.

I estimated (based on 7330000 = 1.83GHz and 8000000 = 2.0Ghz) that 8640000 = 2.16 GHz
I will not guarantee that this will fix it but you can try....

I had a little confirmation of this number from this post:
[http://82.211.81.186/showpost.php?p=1867460&postcount=5](http://82.211.81.186/showpost.php?p=1867460&postcount=5)

where the lpj is calculated during boot (like it should be) at 8645184

---

