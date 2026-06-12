---
title: "Can't create ./root, even if I sudo"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by drowner on 2007-05-11
G'day all

I'm attempting to install DamnSmallLinux to a USB pendrive.

I have done everything that I need to, except when i go to put the .iso to the USB drive i get the following error:

[http://paste.linux-noob.com/index.php?query=2018](http://paste.linux-noob.com/index.php?query=2018)

Particularly: tar: 

./boot: Cannot mkdir: Permission denied
./boot/isolinux/
tar: ./boot/isolinux: Cannot mkdir: No such file or directory

The initial advice i got was to log in as root, but i don't really want to do that, so I sudoed the tar command, but i still got the above error.

Any thoughts on why I can't make the directory as root?

---

### Post by BarfBag on 2007-05-11
Try sudo su.  It gives the terminal root permissions, but doesn't log you in as root.

---

### Post by drowner on 2007-05-11
I will do that

But wouldnt sudo give the terminal root permissions?

And you mean:

sudo su

THEN

tar... etc?

---

### Post by BarfBag on 2007-05-11
Sudo gives the command following it root permissions, not the terminal.  Sudo su sometimes works for me when sudo does not.  Yes, that's what I meant.  sudo su, press enter, then your tar commands.

---

### Post by drowner on 2007-05-11
Ok here goes.

I'll let you know when it doesn't work :P

---

