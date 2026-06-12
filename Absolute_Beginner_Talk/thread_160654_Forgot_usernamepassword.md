---
title: "Forgot username/password"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by halcyon_errant on 2006-04-15
I am very new to Linux (the sum total of my knowledge consists of a few basic commands like cd and ls).  For a class project, I installed VMWare on my computer and installed the server version of Ubuntu on the virtual machine.  Unfortunately, my partner and I somehow crashed our virtual machine and had to reboot it, but neither of us remembers the username/password we created (it was like 3 months ago, and we always just saved the state of the virtual machine before).  Is there any way to find my username/password so that I can log back into Ubuntu and access the programs and files I have in there?

---

### Post by bscbrit on 2006-04-15
Hopefully not!  If you could, it wouldn't be a very secure system, would it?  Unless you can boot into recovery mode and have root access then you can forget logging back into it.  And I don't know enough about VMWare to say whether you can recover your data.  Sorry.

---

### Post by mostwanted on 2006-04-15
Can you login via the resque/whatever it's called mode? That should grant you root privileges AFAIK so you can set new passwords for users.

On a regular Ubuntu install both normal modes and the resque mode are available from the GRUB boot menu.

---

### Post by aysiu on 2006-04-15
Boot into recovery mode.

Type ```
adduser halcyon admin
passwd halcyon
```

---

### Post by halcyon_errant on 2006-04-15
What's a GRUB boot menu?  When I reboot, it doesn't give me any menus.  It prints a whole bunch of stuff to the screen as it boots up, then asks for the login name and password.

---

### Post by r4ik on 2006-04-15
Try,

[http://www.ubuntuforums.org/showthread.php?t=133102&highlight=howto+password](http://www.ubuntuforums.org/showthread.php?t=133102&highlight=howto+password)

Good luck !

---

### Post by halcyon_errant on 2006-04-15
Thank you so much, everyone!  You just saved me several day of setting up a new VM and reinstalling all the software!

---

