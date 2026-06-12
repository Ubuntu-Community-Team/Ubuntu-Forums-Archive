---
title: "Remote Desktop Via Windows Xp Machine"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by tc3racer on 2006-07-26
Hi all

i am new to linux and have never used it before i am thinking of building a webserver however i am only having a base unit and not a monitor. However i am also puzzuled about wether i can remotly logon to the linux machine through a windows if there is a way is is it easy

please help

Phil:confused:

---

### Post by risbac on 2006-07-26
For remote connection, you can easily enable a vncserver on the linux machine, and access it from any VNC client installed on windows. So yes, it's possible. If you want a command line access, you can install a SSH Server on the Linux machine, and use Putty on the windows machine to connect.

---

### Post by tc3racer on 2006-07-26
will this all be command prompt intaface if i use putty. because i prefer gui or is there another one that is easy to install

---

### Post by tc3racer on 2006-07-26
is there any remote desktop software that is free and has lets you see in gui for linux that you can remote from on an xp machine if so please could the be listed as im still not quiet sure what i have to do

---

### Post by digivation on 2006-07-26
*Ususally* webservers run headless (no monitor) and use a commandline (no GUI) for admin stuff. After all, a webserver needs to spend its processing power serving up your scrips, not displaying a GUI that no one will ever see...

However, if you want the desktop GUI, you can use VNC. I believe that [this thread]("http://www.ubuntuforums.org/showthread.php?t=122402") might help you out. Finding a free VNC viewer for Windows shouldn't be that hard.

**Edit:** I believe the viewer I used last time was [TightVNC]("http://www.tightvnc.com/download.html"). Have fun.

---

### Post by AsYouWish on 2006-07-26
The thread linked to above did it for me. Its easier than it looks. I use [RealVNC Viewer]("http://www.realvnc.com") on my XP box once the Ubuntu box is set up. This works well enough for my needs. 

I also set up SSH, just in case, and it has come in handy a few times.

---

