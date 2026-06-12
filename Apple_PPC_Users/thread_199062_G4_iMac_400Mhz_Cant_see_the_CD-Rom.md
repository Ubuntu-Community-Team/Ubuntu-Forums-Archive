---
title: "G4 iMac 400Mhz Cant see the CD-Rom"
date: 2006-06-18
forum: Apple PPC Users
---

### Post by bcnme on 2006-06-18
I am trying to install to my iMac but keep running into issues. Has anyone successfully installed on a G4 iMac 400Mhz?

..Bill

---

### Post by bcnme on 2006-06-18
This problem was my own error. When you put the cd in reboot and hold down option. Then it worked for me with no problems at all. 

When I ran "live" my screen went blank after the install. if you exit out by using cntrl-opt-F1 you drop to the command line. 

Type "sudo vi /etc/X11/xorg.conf then do a searh for the horizontal lines and vertical. use  HorizSync 60-60 VertRefresh 43-117

then stop and start the gdm with sudo /etc/init.d/gdm stop
then do  sudo /etc/init.d/gdm start

then startx

you shoudl be up now.. Way Cool!!

---

