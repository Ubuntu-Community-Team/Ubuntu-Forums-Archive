---
title: "Can't boot after installing to new Dell"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by perkyj on 2007-07-03
After installing 7.04 to Dell Optiplex 320, N series, it will not boot. Goes to blank screen and the cursor blinks.  This is a new pc with no OS installed.  Is there a bug with Dell?  I've installed it on several other older pc's with no trouble at all but this one is giving us fits and we have 120 more machines to install it to.  512 MB Ram 40GB Sata drive, Celeron 3 GH processor.  The Grub options are:  Ubuntu Kernel 2.6.20.15.generic, ubuntu Kernel (recovery mode), ubuntu, memtest86.  All three options give the same blank screen with blinking cursor.  Any thoughts?

---

### Post by Raineer on 2007-07-03
It sounds like Xorg isn't booting, are you seeing a splash screen before the blanking cursor?

Press Ctrl-Alt-F2 and you should get to a login prompt. Login with your user and password. Now, 
```
sudo dpkg-reconfigure xserver-xorg
```

Follow the prompts and try a different driver, as a last resort use "vesa", which is typically at the bottom of the list.  It will help to know what kind of graphics card (or driver) the Dell uses.

After you run the program type the following:
```
sudo /etc/init.d/gdm restart
```

---

### Post by perkyj on 2007-07-03
No splash screen before cursor.  We'll try your suggestion now.

---

### Post by o0maverick0o on 2007-07-25
same problem here - help.

---

