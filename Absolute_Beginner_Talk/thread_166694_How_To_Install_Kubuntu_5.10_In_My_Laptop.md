---
title: "How To Install Kubuntu 5.10 In My Laptop"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by traxion3 on 2006-04-26
hi i'm really2 sux beginner in linux..

i'm using acer 5502NWXMi
spec:
intel pentium m 1.73Ghz
14.1" WXGA widescreen
Ati Mobility Radeon X700 Pci xpress
80GB
512MB DDR2

las week i've installed kubuntu in my laptop.everything went well..but as everything boot up, my screen went blank(black screen) nothing appear on my lcd..i read many thread as well..then i tried to fix by using another monitor..i've pluged in to another monitor.fortunately, kubuntu is appeared to the monitor..then i sudo ./ati-driver-installer-8.24.8-x86.run in terminal...everything went well...and the installation of driver went through in xwindows..then i answer all the questions and exit the installation...but when i tried to run this commad in terminal cd /usr/X11R6/bin ... then sudo ./aticonfig .... but a error msg came out... i'm not sure wat the error said..but i just like a file was missing in another folder(lib...shared...image)...

someone could help me to fix this problems? please..i really2 want to try ubuntu using my own lcd...

---

### Post by Mr Fat Bat on 2006-05-18
Have a look at this site about installing the fglrx driver:

[http://ubuntuforums.org/showthread.php?t=143283&highlight=fglrx+X700]("http://ubuntuforums.org/showthread.php?t=143283&highlight=fglrx+X700")

I had a lot of trouble getting this to work in previous versions but it worked instantly when I upgraded to Dapper!

Good luck ;)

---

