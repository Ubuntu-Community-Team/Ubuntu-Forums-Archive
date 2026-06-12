---
title: "Configure the boot splash screen?"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by kpjoyce on 2007-05-03
Where do I configure the splash screen?  It looks great the way it is, but I'd like to see the system messages too.

thanks.

---

### Post by obbe on 2007-05-03
did you mean the loading screen? take a look [here]("http://www.gnome-look.org/")

---

### Post by jpatton on 2007-05-03
I'm not sure how, but I think he means he wants to see the services and stuff as the OS starts, like other linux distro's do.

---

### Post by Fire on 2007-05-03
I am at work and am not using linux right now.. but I believe that the way to change this would be to open a terminal

sudo gedit /boot/grub/menu.lst

when this opens scroll down until you find something that looks like this:

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro single splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

Remove splash from the line above and when it boots it will show you the system messages.

---

### Post by kpjoyce on 2007-05-03
Thanks.  The grub config information is what I needed.

---

### Post by jpatton on 2007-05-03
Is there a way to get it to display that information over a background image? Or perhaps display it like you can in Fedora?

---

### Post by qaturn on 2007-05-06
My splash screen is about an inch or 2 off of the screen, is there any way to fix this ?

---

### Post by skrimpy on 2007-05-06
> **qaturn said:**
> My splash screen is about an inch or 2 off of the screen, is there any way to fix this ?

This thread helped me fix that problem right up ^.^

[http://ubuntuforums.org/showthread.php?t=317888&highlight=no+splash+screen+while+booting](http://ubuntuforums.org/showthread.php?t=317888&highlight=no+splash+screen+while+booting)

---

