---
title: "How can I make my computer boot into Windows by default?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Johannvr on 2007-05-19
It's actually my mothers working computer. I just figured that KUbuntu looks excellent, so I repartitioned the disc and installed KUbuntu successfully. My only problem is that I dont know how to minipulate the Grub so that I can make Windows boot by default.

I already tried to minipulate the /boot/grub/menu.lst file, but I cant seem to be able to write to it. 

I will appreciate it if anyone can help.

---

### Post by rich.bradshaw on 2007-05-19
sudo nano /boot/grub/menu.lst

the change default to what ever number is Windows, numbering starts at 0.

sudo lets you edit as root.

---

### Post by Karl S. on 2007-05-19
*I already tried to minipulate the /boot/grub/menu.lst file, but I cant seem to be able to write to it.*

What command did you use? If you haven't, try

sudo gedit /boot/grub/menu.lst

---

### Post by aysiu on 2007-05-19
> **rich.bradshaw said:**
> sudo nano /boot/grub/menu.lst Considering how important this file is, it's probably a good idea to back it up first: ```
sudo nano **-B** /boot/grub/menu.lst
``` > **Karl S. said:**
> sudo gedit /boot/grub/menu.lst That actually should be ```
gksudo gedit /boot/grub/menu.lst
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

A detailed HowTo on changing the default OS is here:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

