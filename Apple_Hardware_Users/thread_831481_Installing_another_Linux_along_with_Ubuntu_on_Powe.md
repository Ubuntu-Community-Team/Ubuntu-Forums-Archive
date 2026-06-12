---
title: "Installing another Linux along with Ubuntu on PowerBook"
date: 2008-06-16
forum: Apple Hardware Users
---

### Post by mfox on 2008-06-16
I presently have a Tiger/Ubuntu 8.04 dual boot set up on my PowerBook G4/1.33 15" Al, and I would like to try another Linux distro on the same machine without harming my other installations.  I have my HD partitioned into two volumes.  Could I put the other distro on free space on the second volume and have access to all three distros at boot-up?  Is there something special I would have to do to the bootloader to make this possible, or would the installation automatically add itself to the present bootloader?  In case it matters, the other distro I would like to try is YDL 6.0.

---

### Post by stream303 on 2008-06-17
I don't see why it wouldn't work.  I have no experience with YDL, but I assume that it would detect the other two installations and direct yaboot to configure itself properly.  You could always go in and edit /etc/yaboot.conf manually if things go awry I suppose.

---

### Post by oswaldkelso on 2008-06-20
From memory I had to edit the yaboot.conf file 

search this forum for yaboot and ybin 

[http://ubuntuforums.org/showthread.php?t=812475](http://ubuntuforums.org/showthread.php?t=812475)

[http://www.my2bits.org/?p=49](http://www.my2bits.org/?p=49)

---

