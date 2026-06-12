---
title: "Ubuntu will only boot into rescue/recovery mode."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by ferunandesu on 2007-06-11
Hello,

I installed Ubuntu 7.04 with the amd64 alternate install cd, but when booting normally, the screen will simply go black and my monitor will eventually switch off. I can boot into recovery fine. My video card is an ati radeon x700 pro 256mb pcie. I've already installed the updated fglrx drivers while in recovery mode and have attempted to reboot but I still have the same problem. I have tried many different things, which includes attempting to use the "vesa" driver as well as what was recommended in the following thread...

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

... as well as tinkering with  "sudo dpkg-reconfigure xserver-xorg"

So far, none of my changes have had any effect on the normal boot process... It does the same thing every time, The screen simply goes blank right after I refuse to boot into the GRUB menu. This, along with the fact that I'm making this post from what appears to be a properly functioning system while in recovery mode, leads me to believe that the problem is... I DON'T KNOW.

Please help.

-Thanks

<update>

Using "radeon" instead of "fglrx" in xorg.conf does not work.

---

### Post by ferunandesu on 2007-06-11
Do I need to edit something in GRUB?

---

### Post by ferunandesu on 2007-06-11
Booted into recovery mode and typed "gdm" rather than "startx". Unlike with startx I was prompted to log in, but I was also greeted with the error "failed to start HAL".

---

### Post by ferunandesu on 2007-06-11
Also, I'm "not allowed to access the system configuration" when I go to System -> Administration -> Network. This is, of course, in recovery mode.

---

### Post by ferunandesu on 2007-06-11
PROBLEM SOLVED. 

I simply edited "quiet splash" out of it's first instantiation after the default options in menu.lst

Being in normal mode solved the access problem as well.

Hooray for me!

---

### Post by ecs_pf5 on 2007-06-21
I've got EXACTLY the same problem.. let's give it a go;

Yeah - big thanks. Does the trick admirably.

---

