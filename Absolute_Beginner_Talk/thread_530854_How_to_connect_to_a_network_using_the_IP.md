---
title: "How to connect to a network using the IP"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by jorgecarrillo150990 on 2007-08-20
So my school has a network in which in Windows I have to put \\125.0.0.1 (example) in the window of "Run".
Is there anyway to do the same in Ubuntu?

---

### Post by gunderwood on 2007-08-20
What you're doing there is connecting to a Windows SMB shared directory. You can quite easily do this on Ubuntu by using Samba. Ensure that Samba is installed, this can be accomplished through Synaptic or from a command line.

```

apt-get install samba

```

Once you're sure you have got the proper software installed select your Places menu and select "Connect To Server"

In server type in the IP address 125.0.0.1 and any Login information that you would generally have to enter. If it is an open share you'll be able to connect by leaving everything blank. Enter a name for the connection because it's going to create a shortcut to this share for you on your desktop. 

Once that's done you should be able to browse the share by double clicking on it just as you would any local folder.

G

---

### Post by AcworthJack on 2007-08-20
If I remember - that opens up a folder showing shared folders on the Windows target box.

short answer: not really

long answer: sure - but you need to install samba on your Ubuntu box :)

Please take a look at this thread - it discusses peer-to-peer networking between Ubuntu and Windows via samba.
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Good luck,
John

---

### Post by jorgecarrillo150990 on 2007-08-21
thank you ppl but now I have another problem, in the server I have to use a password and a username, but I dont know where to put it

---

