---
title: "Remotedesktop"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by luis12 on 2006-09-07
help on geeting this going. what needs to be done

---

### Post by mattisking on 2006-09-07
What are you trying to do? You want to remotely control another desktop (what OS?) or you want to remote control your own desktop from somewhere else (from what OS to Ubuntu)?

---

### Post by Omnios on 2006-09-07
Hi I tryed this before with two Linux machines. First on the machine you want to remote desktop you need to go intio
 menu / system / Preferences / Remote Desktop, 
 Now you will have a choice to allow other users to view you desktop.
Also anothr good idea will be to make a password for it in require a  password. 
 Now another aspect is the users can view your deskktop using this command:
vncviewer localhost:0

 Anyways I do not have two computer right now as my old P2 that I was using to explore this stuff died.

 I also Remember that I had to add a port to the end of the connect to be able to connect otherwise it would not connect and also I had to download a program to view the remote desktop,

---

### Post by jonny on 2006-09-07
I don't bother with VNC.  Normally I just want to run a single application on the remote machine and there's a much simpler and more elegant solution that I described some time ago in [this How-To]("http://ubuntuforums.org/showthread.php?t=169966").

My solution isn't good over an insecure network, though.

---

