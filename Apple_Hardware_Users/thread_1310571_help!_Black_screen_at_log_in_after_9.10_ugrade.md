---
title: "help! Black screen at log in after 9.10 ugrade"
date: 2009-11-01
forum: Apple Hardware Users
---

### Post by Bananaloaves on 2009-11-01
I need major help. I upgraded to 9.10. all was well. Then i logged off by accident, and now im stuck with a black screen. it appears to be single user mode. I have no clue why i am in it, and how to get the gui back. I read alot about xorg.conf, and i edited it to fix my track pad. Now my ubuntu installation is screwed up! cant reinstall because i dont have my cd with me! ahhhhhhhhhh

---

### Post by rjcalifornia on 2009-11-01
hi! quick question: After editing the xorg.conf file do you run this: sudo ybin -v?

---

### Post by Bananaloaves on 2009-11-02
no i did not run sudo ybin -v.

---

### Post by rjcalifornia on 2009-11-02
run it, so it can... how do you say it?? Commit changes??

---

### Post by Bananaloaves on 2009-11-02
so if i run this, even in the single user mode, or whatever is on my screen, this will do what?

---

### Post by rjcalifornia on 2009-11-02
Sorry about the lame answer up there :(


Now back on topic, if I got this right, when you turn ur computer on, you only command line ui, right? well, login, then edit xorg.conf file. 

> sudo gedit /etc/X11/xorg.conf


once there, paste this:

> Section "Device"
Identifier "ATI Rage 128"
Driver "r128"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 60-60
VertRefresh 43-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

save it, exit gedit, and run this:

> sudo ybin -v

---

### Post by Bananaloaves on 2009-11-02
ok, i will try that and let u know. if this doesnt work, can i just reinstall the operating system again.

oh and yes, you are correct. When i log on, i am greeted with a black screen with white writing. I can log on yes. I already tried to enter an xorg file, but i used sudo nano, because sudo gedit did not work :(

---

### Post by Bananaloaves on 2009-11-02
oh well. i just did a fresh install of 9.10 and its working fine. thanks though.

---

### Post by oswaldkelso on 2009-11-02
While this may work on an a PPC imac and possibly PPC ibooks it would need tweeking. It won't work for all macs. With no screen the gedit commands would need to be change to nano or vi. There are good how to's in the archvies on "blessing" the system

> Now back on topic, if I got this right, when you turn ur computer on, you only command line ui, right? well, login, then edit xorg.conf file.

Quote:
sudo gedit /etc/X11/xorg.conf

once there, paste this:

Quote:
Section "Device"
Identifier "ATI Rage 128"
Driver "r128"
BusID "PCI:0:16:0"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
HorizSync 60-60
VertRefresh 43-117
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection
save it, exit gedit, and run this:

Quote:
sudo ybin -v 

---

