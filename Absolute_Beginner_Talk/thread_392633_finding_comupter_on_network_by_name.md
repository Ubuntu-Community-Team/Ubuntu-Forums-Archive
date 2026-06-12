---
title: "finding comupter on network by name"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by FITorion on 2007-03-24
Ok I'm setting up a server... that last step is getting it to broadcast its name.

Samba is set up

SSH is set up

winbind is installed

I can see the computer on the network when I search by IP

I can't see the computer on the network when I search by name.


This is a mixed network.  most computers that are looking for it will be running windows.  I do not have access to these computers so changing their settings is not an option.

---

### Post by Mister.Vash on 2007-03-25
If the network that you are connecting to allows it, you can follow the steps in this post to send your hostname to the dns server.  Then the other machines should be able to resolve your machines name

[http://www.ubuntuforums.org/showthread.php?t=367974](http://www.ubuntuforums.org/showthread.php?t=367974)

---

### Post by FITorion on 2007-03-25
Yes the problem is that this computer is on a collage network and I don't think that they allows computers to set their own dns names. 
I want the client computers to be able to type in my computer's name into their browser and have them sent to the sever.

---

