---
title: "[SOLVED] A hell of a lot of problems:  no login screen, no ubuntu desktop, can't acce"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by marmaladeskies on 2007-12-31
So, I basically had Ubuntu up and running fine for a few months, when I decided to install xubuntu-desktop.  So I did (I think I tried both "sudo apt-get install xubuntu-desktop" and "sudo aptitude install xubuntu-desktop" at some point).  Then, and if you'll please not ask me why, I removed ubuntu-desktop (without checking if xubuntu was working first :)).  Then when I restarted, I saw grub starting, then a blank screen (and that's all I can get now).  I've heard of people who can type in their user name and password on the blank screen and get in, but that didn't work for me.  So, right now I've booted with the ubuntu live CD to see if my files were saved.  After mounting the "54.5 gb volume" when I try to open a folder inside my /home folder, I get the popup "The folder contents could not be displayed.  You do not have the permissions necessary to view the contents of "folder"." (and the icon for the folder has a little x on it's upper right).  Same goes for every file/folder in /home.  (Thanks for wading through all that.)  So, how can I keep all my files (and get the permissions to access them) and login to ubuntu, xubuntu, or any linux environment so that I don't need to use the live cd every time (or install ubuntu again if need be)?  Thanks so much!

---

### Post by dstew on 2007-12-31
> Then when I restarted, I saw grub starting, then a blank screenDo you see the grub menu before it goes blank? If so, select recovery mode. That should get you a text-based login. If it disappears too fast, try ctrl-alt-F1 to get to the first virtual terminal.

---

### Post by marmaladeskies on 2007-12-31
Yes, I can press esc and go into recovery mode.  What should I do now?

---

### Post by PmDematagoda on 2007-12-31
Once you get to boot Ubuntu in Recovery Mode, execute:-
```
sudo aptitude install ubuntu-desktop
```
to install GNOME, that should fix your problem.

---

### Post by marmaladeskies on 2007-12-31
Thanks - I did that, but I'm getting all these errors, e.g. "Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main xsane 0.99+0.991-3ubuntu5  Could not resolve 'archive.ubuntu.com'"  I got about 10-20 errors like that (is it because I'm not connected to the internet?  If so, how do I connect to the net?).  I gave it a try anyways, but it's the same old blank screen after grub.

---

### Post by PmDematagoda on 2007-12-31
Are you connected to the internet? What type of connection and equipment do you use to connect to the internet?

---

### Post by marmaladeskies on 2007-12-31
I have a wireless connection through my router, which is a "Linksys Wireless G Broadband Router", Model No. WRT54G v.3.  The connection is just called "linksys".  If it matters at all, when I was on the live CD, in order to get a connection, I had to click on the connections in the notification area and then choose linksys.  Thanks for the quick responses.

---

