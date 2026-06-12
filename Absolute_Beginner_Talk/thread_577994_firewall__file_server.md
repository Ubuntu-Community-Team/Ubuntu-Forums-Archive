---
title: "firewall / file server"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by linuxnoob123456789 on 2007-10-16
i want to make a firewall server and a file share server in on computer. I would like to not do it on the server Ubuntu becase of the complexity of text command ?


:confused::confused::confused::confused::confused::confused::confused:

---

### Post by Capricori on 2007-10-16
Install normal Ubuntu then, the server version is more or less the same, but with less GUI :) With a normal Ubuntu installation, plus a couple of other packages, you could have a server up and running, with a GUI, in no time :)

---

### Post by Orbital75 on 2007-10-16
I wouldn't put both on the same computer.
The File Server will weaken you security...

Take a look at SmoothWall for a FireWall.
That will do the trick as far as a firewall goes.

---

### Post by qpieus on 2007-10-16
There's absolutely no problem using a desktop (normal) installation as a server box. I agree with Orbital75 on not having the file server be your firewall too. Best to get a separate box for that.

---

### Post by linuxnoob123456789 on 2007-10-16
okay then how do i setup  password protected file server in a local network serving windows computers

---

### Post by qpieus on 2007-10-16
If you are serving windows computers, you'll want to use set up a program called samba. I'm not going to tell you how to set up samba here because it's been discussed millions (OK, so I'm exaggerating) of times here in the forums. I would start with the samba how-to here:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Quick summary:
You'll want to set up a fat32 formatted partition on your server (so the windows machines can use it.
You'll then se tup samba to share that partition/directory
Since you want to use passwords, you'll need to set up user accounts on the server AND in samba (I'm not at all fluent on the password part of this setup because my file server doesn't use passwords)

Just search on "samba" and you'll find tons of good info.
Have fun!

---

### Post by linuxnoob123456789 on 2007-10-17
thank you very much :guitar:

also set up a fat32 RAID for samba to use

---

### Post by linuxnoob123456789 on 2007-10-17
can someone tell me how to set up a fat32 RAID for samba to use

---

### Post by linuxnoob123456789 on 2007-10-20
can someone tell me how to set up a fat32 RAID for samba to use plz:confused::confused:

---

