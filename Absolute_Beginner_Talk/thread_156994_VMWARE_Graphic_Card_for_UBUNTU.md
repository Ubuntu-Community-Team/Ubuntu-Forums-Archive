---
title: "VMWARE Graphic Card for UBUNTU ??"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by nemiroff on 2006-04-08
Dear friends, 

I set up ubuntu under VMWare, or I tried to do it because X-server is not working and producing below error. 

[IMG]http://onfinite.com/libraries/850260/42c.jpg[/IMG]

It is obvious that, the problem comes from the wrong video card, ubuntu doesn't know what is VMWARE video card.

Does anyone know how can I fix this ?
where can I fix it ? (from Ubuntu or from VMWare ?)

Thanks. 
Alp

---

### Post by MartinG on 2006-04-09
From the screenshot you seem to be using VMWare Player, rather than the Workstation or Server versions, and AFAIK the Player only works with pre-prepared Virtual Appliances, such as the one available from VMware at:
[http://cdimage.ubuntu.com/vmware/Ubuntu-5.10.zip](http://cdimage.ubuntu.com/vmware/Ubuntu-5.10.zip)

Is this what you are using?  If you are instead trying to install from a CD, I think you'll be out of luck, as the Player (obviously) lacks features available in the Workstation.

---

### Post by ace2005 on 2006-04-09
[QUOTE=MartinG]From the screenshot you seem to be using VMWare Player, rather than the Workstation or Server versions, and AFAIK the Player only works with pre-prepared Virtual Appliances[/QUOTE]

You can install any OS (well 32bit) you want like Windows 2000/XP, there is a very easy guide here:

[http://linux.wolphination.com/?p=18](http://linux.wolphination.com/?p=18)

You can try dpkg-reconfigure xserver-xorg to try and select a different driver for graphics, give vesa a try, it seems to work with most graphics cards, oh and you need to be root when you run this. Either log in as root from a console or do "sudo su" to get root access

---

