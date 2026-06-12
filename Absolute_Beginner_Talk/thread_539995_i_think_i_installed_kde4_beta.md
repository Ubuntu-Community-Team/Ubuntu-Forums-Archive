---
title: "i think i installed kde4 beta"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-08-31
i did install it. but i dont seem to find it amongst my session types... how to access it?

---

### Post by seshomaru samma on 2007-09-01
log out
look under "sessions"

---

### Post by Sushubh on 2007-09-01
umm i did that and the kde listed there is version 3.5 something.

---

### Post by seshomaru samma on 2007-09-01
how did you install kde4?

---

### Post by Sushubh on 2007-09-01
[http://kubuntu.org/announcements/kde4-beta1.php](http://kubuntu.org/announcements/kde4-beta1.php)

i did not understand these steps:

# These KDE 4 packages install to /usr/lib/kde4 so run:

    * export LD_LIBRARY_PATH=/usr/lib/kde4/lib
    * export KDEDIRS=/usr/lib/kde4
    * export PATH=/usr/lib/kde4/bin/:$PATH
    * export KDEHOME=~/.kde4

# Run some programmes. Plasma seems to work and will run over kdesktop happily. Good luck.
# To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 & export DISPLAY=:1; xterm and run startkde in the Xerphyr xterm.
# To run it as a full session copy /usr/lib/kde4/share/apps/kdm/sessions/kde.desktop to /usr/share/xsessions/kde4.desktop, edit the Name entry in kde4.desktop to be called "KDE 4", put the four export lines at the top of /usr/lib/kde4/bin/startkde and start a new session in KDM with KDE 4.

---

### Post by Sushubh on 2007-09-01
i ran these commands on terminal:

export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4

nothing showed as a result

---

### Post by aishen on 2007-09-04
install all kde4 related debs
install xserver-xephyr (i use kubuntu but should work for all)
open a shell 
type xhost + (to be able to open display from any shell)
and then 
export LD_LIBRARY_PATH=/usr/lib/kde4/lib
export KDEDIRS=/usr/lib/kde4
export PATH=/usr/lib/kde4/bin/:$PATH
export KDEHOME=~/.kde4
Xephyr :1 -screen 1024x768 & export DISPLAY=:1; xterm &
(it runs a xserver and display a xterm) 
type in the xterm : startke and you see KDE4
(if you have all libs installed otherwise installed them)
type enter (don't close this shell as you will use it :)
if you type kanagram it will run...
(you can just run an application without running xserver-xephyr) 
as long as your exports are done and xhost + ran...
enjoy :)
Henri:guitar:

---

### Post by Sushubh on 2007-09-04
installed that thing... 

but:

> abc@abc-desktop:~$ xhost +
access control disabled, clients can connect from any host
abc@abc-desktop:~$ sudo xhost +
Password:
access control disabled, clients can connect from any host
abc@abc-desktop:~$ 


---

