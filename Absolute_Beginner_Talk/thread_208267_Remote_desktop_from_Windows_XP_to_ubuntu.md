---
title: "Remote desktop from Windows XP to ubuntu"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by will71110 on 2006-07-03
Does anyone know or can point me in the right direction to remote into my ubuntu from my windows PC?  There is some documation on how to do it to fedora core but it didnt work when I tried to edit the firewall in ubuntu. Its here [http://www.notgotaclue.co.uk/article/art-winandlin.htm]("http://www.notgotaclue.co.uk/article/art-winandlin.htm") The page tells me to use command lokkit.  Also it says use VNC,  but what version do I need? (By the way I am an first time user of Linux so might have to dumb it donw for me)  thanks for any help

---

### Post by lamego on 2006-07-03
Read [here]("http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc+server") on how to install/setup a vnc server.

---

### Post by MatBi on 2006-07-03
Check out freenx!

---

### Post by will71110 on 2006-07-05
I figured it out.  I installed Krfb on ubuntu that was under the add/remove...  Then I used VNC on windows to connect to the computer.  Works like a charm but it is not the fastest I have seen.  Anyways thanks for the advice.

---

### Post by thoffland on 2006-07-05
try 'sudo apt-get install' and try either 'grdesktop' or 'rdesktop' 

That's what I use and it's just like the windows remote desktop connection. The only problem I have with it is that I have to physically log in to my windows pc before I can make a remote connection. It might just be a setting I'm overlooking.

---

### Post by will71110 on 2006-07-07
Does anyone know what port(s) kfrb uses for the remote deskeop?

---

