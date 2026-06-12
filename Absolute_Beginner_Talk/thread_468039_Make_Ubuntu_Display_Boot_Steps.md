---
title: "Make Ubuntu Display Boot Steps"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by ghost_ryder35 on 2007-06-08
I keep getting stuck at a certain point in my boot.  Since I have the pretty little splash screen I have no idea what step it is so I would like to make Feisty display the steps just like in Fedora.  Thanks.

---

### Post by pnix on 2007-06-08
I'm not sure. You can try, at boot menu try edit the kernel line change "splash" to "nosplash"

---

### Post by ghost_ryder35 on 2007-06-08
i remember reading something about quite and loud or something like that, anyone shed some light on this.  I really would love to start Ubuntuing again ;)

---

### Post by dstew on 2007-06-08
At the grub menu screen, press 'e' to get into edit mode, and remove the word "quiet" and change "splash" to "nosplash" on the kernel line.

---

### Post by forestpixie on 2007-06-08
saw this in a thread earlier

[http://ubuntuforums.org/showthread.php?t=467709&highlight=quiet+splash](http://ubuntuforums.org/showthread.php?t=467709&highlight=quiet+splash)

posts 2 and 9 should help you

---

### Post by forestpixie on 2007-06-08
not quite quick enough
:)

---

### Post by ghost_ryder35 on 2007-06-08
> **dstew said:**
> At the grub menu screen, press 'e' to get into edit mode, and remove the word "quiet" and change "splash" to "nosplash" on the kernel line.
thanks, will try this right now

---

### Post by ghost_ryder35 on 2007-06-08
yea i tried that, but every time i reboot it doesnt work, the quiet line is still there.  How do I save the changes?

---

### Post by ghost_ryder35 on 2007-06-08
oh yea I see nothing about splash and no splash, just quiet

---

### Post by meatpan on 2007-06-08
If you ever want an alternative to closesly observing the boot/init output, consider running the 'dmesg' command.  dmesg essentially parses the system logs for the boot/init output.  Very useful for debugging an issue.

---

### Post by sabrewolf2006 on 2007-06-08
you could
apt-get purge usplash

That did the trick for me ;)

---

### Post by digitalbenji on 2007-06-08
To make this solution permanent.  Do this:
sudo gedit /boot/grub/menu.lst
and remove "quiet" from the kernel line.  You can also remove splash here, but I like to leave splash on and remove quite, this way you get the best of both worlds.

---

### Post by ghost_ryder35 on 2007-06-08
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d7751425-7061-4bd0-81f3-b28a517376b4 ro splash
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d7751425-7061-4bd0-81f3-b28a517376b4 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d7751425-7061-4bd0-81f3-b28a517376b4 ro splash
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d7751425-7061-4bd0-81f3-b28a517376b4 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


thats what it looks like now, is that good?

---

### Post by dstew on 2007-06-08
That is good.

---

