---
title: "Need to set up remote access"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Masteroc on 2007-12-01
So here is what i want to do, i want to be able to use another linux distro (on my laptop) to send files to my desktop (ubuntu 7.10) and to run programs and commands in the terminal. I've used the remote desktop feature on windows and something like that would be nice, but not a necesity. I googled this and found out how to do this with the vnc viewer or something, but i want to make sure that i can do this from my laptop which does not run ubuntu. So maybe a bash type of thing would be better than gui because it can be used from any linux distro?

Thanks!!

---

### Post by High Camp on 2007-12-01
Hi

Not sure if you want VNC or not but it can go Linux <-> Linux, Linux <-> Mac, and Linux <-> M$.

Beyond that I can't be much help because I've never played around with ssh.

Hope that solves your problem.

P.S. I use Skype to send files between computers and if they are next to each other I use Synergy to control the desktop and if not I use VNC.

---

### Post by Masteroc on 2007-12-01
will vnc allow me to send files between computers even if they are not on the same network?

---

### Post by scrooge_74 on 2007-12-01
Your answer to yout question is ssh

---

### Post by vikram on 2007-12-01
use ssh for connecting to the linux desktop. you will get the command line interface.

use VNC for GUI interface

you can even use VNC over ssh for security !

to transfer files between computers i suggest ftp.

---

### Post by scrooge_74 on 2007-12-01
ssh has its own command for file transfer scp is more secure than ftp, and you can export your gui using ssh  

open a new console [ctrl+alt+f1]
log in, type
xinit /usr/bin/xterm -- :1
then
ssh -Y username@server

then if using gnome on that PC type gnome-session, if kde startkde, if Xfce4 then startxfce4

---

### Post by High Camp on 2007-12-01
I've got a question. Is ssh secure over the internet? I know I've seen something somewhere that said one of the remote protocols is not but I can't remember which one. I never realized ssh was that easy.

Thanks,

---

### Post by scrooge_74 on 2007-12-01
Your connection becomes a tunnel between your PC and the server

[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

