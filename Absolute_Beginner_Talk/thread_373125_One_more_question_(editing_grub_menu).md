---
title: "One more question (editing grub menu)"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Astral Abraxas on 2007-02-28
For some reason it says I have like 4 Ubuntu's and 4 Ubuntu Recovery's and then my Windows XP. I was wondering if I could simply editted them out by cutting out the stuff from /boot/grub/menu.lst?
```

title           Ubuntu, kernel 2.6.17-11-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.17-11-386
boot

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/sda3 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

```
is the end of my /boot/grub/menu.lst file... I just hate seeing it all the time, I have to switch between ubuntu and windows quite frequently (my mom >.>) and it's rather annoying to see.

---

### Post by freebird54 on 2007-03-01
There are at least 2 answers to this - a short one and a better one come immediately to mind.

The short one is 'yes'.

The one I chose was a GrubEd script that I found through searching the forums.  It not only allows all the changes you thought of, but also others you may NOT have thought of - as well providing a good overview of what is safe/possible in there.

Comes with a decent Grub splash screen too, as well as a way to change it to whatever you like..

BTW - Mom might like that better too :)

---

### Post by rsambuca on 2007-03-01
There a quite a few methods to getting rid of the long grub lists.

1.  You can simply delete the entries from your menu.lst
2.  You can place a "#" in front of the lines of the kernels that you don't want to see (the "#" comments out the line so that it is not read by the grub program).  In this case you would place a "#" in front of the Title, Root, Kernel, Initrd, etc.
3.  You can change the line that says "howmany=all" to "howmany=1" to only show the last kernel
4.  You can remove the older kernels from your system once you are sure the new kernel is stable.  The easiest way to do this is to use the Synaptic Package Manager, search for linux-image, and delete the older kernels.  Grub should be automatically updated if you use this method.

If hard drive space isn't an issue, just use method number 2.  Eventually - and you will know when - you will know when to permanently delete them.
Also, after you have made your changes, you can change the line that says "default  0" to default #, where the # is the entry for Windows for your mother.  Just keep in mind that grub starts counting at zero, and includes every line that starts "title".  Thus if you have a title line for a kernel, a title line for the recovery mode for that kernel, a title line for the "other operating systems", and a title line for XP, the number you would want to enter for XP is 3.

Then change the timeout line to 2 or 3 seconds, so that it boots into Windows quickly for your mother, but you have ample time to press an arrow key to stop the timer and select your beloved ubuntu.

---

