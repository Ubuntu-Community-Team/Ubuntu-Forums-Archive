---
title: "22inch viewsonic isnt working"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2007-06-13
How do i get it to work, monitor error message(nothing to do with LINUX)

Out of Range
hFrequency 81
vFrequency 181



 and can you please tell me how to access terminal and how to navigate through folders using it, it tells me im not on root level, and i try and go to root level but i dont know how

---

### Post by tchoklat on 2007-06-13
try in a terminal
 
sudo dpkg-reconfigure xserver-xorg
 
and reenter your driver and monitior info

---

### Post by bbarcelo on 2007-06-13
Your monitor is display an out-of-range error because your computer is sending it faulty information with regards to the proper scanning frequencies of your monitor. I can't tell you for sure how to fix this, but I can help you out with the root access part.

In a terminal you'll want to type "su" or, if just using one command such as wget, you'll want to use "sudo wget". It will prompt you for your root password and you'll need to enter it in the terminal window. It won't echo the text at all as you type. If you're unsure of your root password, it should match your current user password.

---

### Post by Brendan Hart on 2007-06-13
>  and can you please tell me how to access terminal 

I need to know how to access terminal first

---

### Post by bbarcelo on 2007-06-13
Ah, sorry, forgot to mention that. You'll want to just go to the Ubuntu menu in the top left (assuming Gnome) and go to Accessories>Terminal.

---

### Post by NicePics13 on 2007-06-13
**ctrl+alt+F1** (F1 to F6 are text terminals - great if X is broken and you need to fix it. **Ctrl+alt+F7** gets you back to X. You can also quickly restart X with **ctrl+alt+backspace** when you've made changes to xorg.conf)
And to get to the filesystem's root (not the folder /root) just type **cd /**

---

### Post by aquavitae on 2007-06-13
A terminal will be under your menus somewhere.  In KDE its called Konsole, and I think its under Utilities.  In Gnome its gnome-terminal, not sure where, but fairly easy to find.  For a good general help on linux terminal try [http://linuxcommand.org/]("http://linuxcommand.org/").

I had a similar problem with a Samsung LCD screen recently - from looking at the logs (/var/log/Xorg.0.log) and at the configuration file (/etc/X11/xorg.conf) I everntually found that it was a problem with the graphics card reporting incorrect resolutions.

---

### Post by Brendan Hart on 2007-06-13
ah yes but in the terminal how the hell i do i access them

---

### Post by jd65pl on 2007-06-13
[LIST=1]
[*]Re-boot your computer
[*]Choose Boot in recovery mode at the grub screen
[*]Input the command below
[*]```
 sudo dpkg-reconfigure xserver-xorg
```
[*]Choose the options from these setup pages which match your screen
[*]Reboot your computer
[*]```
Sudo reboot
```[/LIST]

---

### Post by jd65pl on 2007-06-13
It may also be useful to know what graphics card you have, as its driver may be causing this issue.

---

### Post by Brendan Hart on 2007-06-13
well ok but ive tried that before, and im not sure exactly all the details on my monitor.

i got a nVidia 6600gt

its working fine for this monitor 17 inch (not widescreen haha)

---

### Post by jd65pl on 2007-06-13
Do you have the nvidia driver installed? Try booting in recovery mode with your 22'' monitor plugged in a running ```
sudo nvidia-xconfig
``` you should have  the monitor you intend to use plugged in other wise the program may misconfigure xorg.conf.

---

### Post by Brendan Hart on 2007-06-13
ok then brb in a tick

---

### Post by Brendan Hart on 2007-06-13
ok i did it, it works but when it comes to screen resolutions supported, how do i add a * next to 1680x1050

---

### Post by jd65pl on 2007-06-13
If you are using  sudo dpkg-reconfigure xserver-xorg then hit the space bar to select a resolution.

---

### Post by Brendan Hart on 2007-06-13
kk brb

---

### Post by Brendan Hart on 2007-06-13
now that ive done that, there aint nothing i cant do!!(hehe can some one help me do java)

---

