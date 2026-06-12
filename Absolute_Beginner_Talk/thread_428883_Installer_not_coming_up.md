---
title: "Installer not coming up"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Uber Schwarz on 2007-04-30
I've restarted my computer but the installer won't come up, it just automatically boots Windows XP so what do I do?

---

### Post by apunc1 on 2007-04-30
is your computer set to boot from the cd drive first? check it by looking in your bios. if you need help accessing your bios, try this from [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

> 
Your computer's BIOS must be set to boot from CD first; otherwise, Windows will just load up again. To get into the BIOS settings, you usually have to press one of these keys during boot-up: Escape, F1, F2, F12, or Delete. Usually your computer will tell you.

once your bios is set to boot from the cd drive fist, the unbuntu installer should start.

---

### Post by bobbybobington on 2007-04-30
I take it you have just put the cd in the tray and restarted you computer. If this is the case, you're computer doesn't know to start from the cd drive. But this is easy to change. When you first start up your computer you'll probably see the name of the computer manufacturer and something along the lines of "setup" and a keyboard key to access it. The key you have to press varies among manufacturers. From here will will have to navigate with arrows on your keyboard. what you want to do is change the "boot order" or "boot priorities" so that the cd drive the installation disk is in is set to boot first. If I didn't explain it clearly enough, [this guide]("http://learn.pcc.com/ltspadd/appbios.html") may be better.

---

### Post by Uber Schwarz on 2007-04-30
My computer doesn't show that it just automatically starts Windows. I've tried holding in Esc., F1, F2, F3 and non of them seem to work and now my CD-ROM doesn't want to open. It did bring up the BIOS before when I held down F1 but now my CD-ROM drive doesn't open after that.

---

### Post by apunc1 on 2007-04-30
did you change anything in bios when you were able to access it? is the ubuntu cd still in the cd drive? maybe the cd is stuck???  have you had trouble with the cd drive before?

---

### Post by whee on 2007-04-30
It can also depend on the way you have burned your installation CD, have you burned the .iso as a data file on the CD or have you burned the contents of the .iso on the CD?

---

### Post by Uber Schwarz on 2007-04-30
I got it working now.

The CD I ordered online.

How do I connect to the Internet with Ubuntu?

This is what it gave me in the Help section.

> wget -c [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz) 
gunzip -c scanModem.gz > scanModem 
chmod +x scanModem
sudo ./scanModem 
gedit Modem/ModemData.txt


---

