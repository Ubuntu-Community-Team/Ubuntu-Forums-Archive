---
title: "NFS help please"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by backflip on 2007-11-26
Hi, I'm tryning to set nfs up on my lappie(server) and desktop(client). I think I've got the server side (lappie) set up but on the client machine when I try............ sudo mount 192.168.5:/home shared  /home/lappie  I get the response "mount.nfs: mount point /home/lappie does not exist" 
The above ip is that of the server and 'shared' is the directory  there.
All I did on the client (desktop)was  install nfs (sudo apt-get install portmap nfs-common) and then mkdir lappie, after which I tried the above failed mount.
Please help, I'm sure it is simple, but not for me..
Thanks

---

### Post by Sqwishy on 2007-11-26
Well with the error your getting, it means you just need to make that folder you're trying to mount it too... try
mkdir /home/lappie

btw check the ip in the mount command your running. You wrote that it says 192.168.5 :S

---

### Post by backflip on 2007-11-26
Thanks for your quick reply. I now get "mount.nfs: 192.168.1.5:/home/shared failed, reason given by server: Permission denied"
I've previously 'right clicked' and added 'shared' to Shared Folders. I've no firewall etc either.

---

### Post by backflip on 2007-11-26
> **Sqwishy said:**
> 

btw check the ip in the mount command your running. You wrote that it says 192.168.5 :S

Sorry about that, it was a typo only and not the problem. Pity it wasn't that simple.:(

---

### Post by Sqwishy on 2007-11-26
Did you do all the right stuff in your /etc/exports file? :S

Try making sure you've done everything in [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) :S

---

### Post by backflip on 2007-11-26
Something really strange has happened, when I opened a terminal to check exactly what was in the /etc/exports file, it wouldn;t let me type a 't' in the terminal window. I was trying to enter gedit but the 't' wouldn;t enter. I tried nano but met the problem again when I tried 'etc/exports, it missed the 't'
Any ideas?

---

