---
title: "&#305; messed up xorg.conf and there is no back up"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by nodesert on 2007-08-05
i tried to upgrade feisty to gusty.but because of bugs &#305; coundn't do this .But my xorg.conf is changed. then i used "sudo dpkg-reconfigure xserver-xorg" command  but i dont know which settings is right for me.I want kubuntu to detect configuration which is best for my laptop.How can &#305; do this

---

### Post by TBerben on 2007-08-05
You could try booting a kubuntu livecd and copying its xorg.conf file to your hard disk, if the livecd autodetects all your settings correctly, that xorg.conf file should work fine

---

### Post by AlexenderReez on 2007-08-05
if you want your system to detect your hardware for you,please boot boot in livecd and in terminal --->

> sudo gedit /etc/X11/xorg.conf


**copy all its contents**

open another terminal --->

> sudo mkdir /mnt/repair

> sudo mount /dev/*h** /mnt/repair

***h** is your linux partition like sda2 for example**

> sudo chroot /mnt/repair su

> sudo nano /etc/X11/xorg.conf
[B]
delete all in that terminal....then replace with what you have copy just now[/B]

---

### Post by Eddy Dean on 2007-08-05
What's wrong with the good old dpkg-reconfigure xserver-xorg?

Boot up, log in (not through GDM but in a terminal), then sudo dpkg-reconfigure xserver-xorg and answer all questions.
Then type reboot to reboot (o rlyeh?) and if you didn't make any mistakes you'll have an working GUI now.

---

### Post by nodesert on 2007-08-05
thanks Eddy Dean 

 "dpkg-reconfigure xserver-xorg" after this command it asks soomething but  i m not sure which answer is right.So &#305; want autodetect everything.For example &#305; dont answer anything during installation

---

### Post by Dedoimedo on 2007-08-05
Hello,
Could you tell what questions did you get into trouble with?
It would be wise to understand how you can troubleshoot those ... obstacles, allowing you to relatively painlessly reconfigure the xorg in the future, should the need ever arise.
Dedoimedo

---

