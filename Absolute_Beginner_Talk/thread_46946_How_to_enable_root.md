---
title: "How to enable root?"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by Umbra on 2005-07-06
How do i enable super user?

I tried:

sudo passwd root

then i specified the pass and switched to root, but this only works in the console, the rest of the system still doesnt allow me to configure many many things.

If i try to run program using the "run as" mode, it always says me the root pass in incorrect, but works in console. 

Im very confused. Im using Kubuntu

---

### Post by Kvark on 2005-07-06
You can enable it if you want to but try to get used to the idea of not needing a special account for root.


To run a command or a command line program as root, just add sudo in front of it.

To run a graphical program as root, start it from the terminal and add gksudo in front of it.

So to edit a text file with gedit as root "gksudo gedit file". 

(sudo works for graphical programs too but can have side effects, so use gksudo for graphical things)

---

### Post by aysiu on 2005-07-06
See this thread:

[http://www.ubuntuforums.org/showthread.php?p=243767#post243767](http://www.ubuntuforums.org/showthread.php?p=243767#post243767)

---

### Post by bootlinux on 2005-07-06
Im very confused. Im using Kubuntu

I am using kubuntu also; (KDE desktop). Commands gedit and gksudo didn't work for me, (command not found).  I'm guessing there for Gnome. I don't really know as I'm not much on shell commands. Here's how I managed to workaround a root log in so I could edit my grub menu.lst. 
Open up a shell Konsole.
Set up root account with command "Sudo passwd root" then enter.
It will ask for your user password then let you enter a new password for root.
Now reboot or log out. 
At the bottom of the logon screen is an option to log on in console mode. 
Pick that one and log in as root. 
Once your logged on you can type "startx" at the command line then enter. 
KDE desktop will start up as root.
There you have it. You can do all those house keeping chores in good old GUI fashion.
 

Personally I don't see what the big deal is about using root to keep house. It's so much easier. If I'm going to crash my system I could do it just as easy with sudo, couldn't I?

---

### Post by Umbra on 2005-07-07
That's exactly what im refering to.

I thinks is a little stupid to disable root login.

---

### Post by Leliel on 2005-07-07
Umbra, not so much silly, as the first step towards the insecure windows method of having only one account, as both admin, and for day to day use

---

