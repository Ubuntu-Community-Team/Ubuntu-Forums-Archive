---
title: "This is a bit odd."
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by John1744 on 2005-10-05
I installed a dual boot of Xp and Ubuntu, it went through the installation, I had everything set up and when it finished the second round of installations w/o the disc where it loads the packages or whatever. It finished and just showed a black screen with a 

_


So I thought ok... I restarted and it showed the Ubuntu start up screen it went through all the loading it shows below the logo, the showed the same black screen with a single

_


Any ideas?

---

### Post by codejunkie on 2005-10-05
[QUOTE=John1744]I installed a dual boot of Xp and Ubuntu, it went through the installation, I had everything set up and when it finished the second round of installations w/o the disc where it loads the packages or whatever. It finished and just showed a black screen with a 
_
So I thought ok... I restarted and it showed the Ubuntu start up screen it went through all the loading it shows below the logo, the showed the same black screen with a single
_
Any ideas?[/QUOTE]
first thing if you did a server install that dosen't include a gui by default you have to install it manualy if you did a default install and your not seeing the gui it's not detecting your video card properly. list what kind of video card you have, and what version of ubuntu your installing and i'll try and help you.

---

### Post by John1744 on 2005-10-05
Odd, I just restarted again and now its just a black screen. :(

Everything was going so good....

---

### Post by John1744 on 2005-10-05
[QUOTE=codejunkie]first thing if you did a server install that dosen't include a gui by default you have to install it manualy if you did a default install and your not seeing the gui it's not detecting your video card properly. list what kind of video card you have, and what version of ubuntu your installing and i'll try and help you.[/QUOTE]
I have an old ATI 7200 PCI card. I'm using the newest version of Ubuntu available from the main site.

---

### Post by John1744 on 2005-10-05
Tried the recovery command. Keep in mind I know nothing about Linux. It went through a long list of things. I get a fail message on Temporary fail in name resolution.

---

### Post by codejunkie on 2005-10-05
[QUOTE=John1744]I have an old ATI 7200 PCI card. I'm using the newest version of Ubuntu available from the main site.[/QUOTE]
if you have more than one video card installed in the system like onboard video and the ati card you need to go into the bios settings and disable the onboard video make sure that that onboard video is completly disabled then you should reconfigure the ati video card with this command
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and reboot let me know this works out.

---

### Post by John1744 on 2005-10-05
Nope nothing... Hmm, I may just give it a break till tomorrow.

---

