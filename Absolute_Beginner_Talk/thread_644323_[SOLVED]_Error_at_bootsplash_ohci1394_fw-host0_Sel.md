---
title: "[SOLVED] Error at bootsplash ohci1394: fw-host0: SelfID received outside bus reset se"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by neanderthalman on 2007-12-18
Hello everyone!

I'm returning to Linux after a year long hiatus.  Long story short, I installed SuSE 10.1 about a year and a half ago, dual boot with XP.  It was my first linux install, and it was not without it's speedbumps, particularly with grub.  After the initial headaches, the system ran great until last February, when I suffered from a HD failure and lost my linux install.  I needed windows at the time to run some proprietary simulators, but now I'm wanting to get linux back.  This time, I've decided I'd like to try Ubuntu.  I liked SuSE, but I hear a lot of good things about Ubuntu these days.

I had no major problems with the install, though grub was the same headache as it was when I installed SuSE.  Fortunately, I was familiar enough with Error 17, so I had an idea what the fix was.  I just needed a little research to find out where the file was and how to edit it.  It felt good to get back into the terminal again.

Anyhow, grub is fixed.

Ubuntu will now *try* to boot, and it makes it about two seconds into the bootsplash screen.  It abruptly turns to a black screen, then outputs the following:

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) [    78.158766] ohci1394: fw-host0: SelfID received outside of bus reset sequence
```

I thought it may have something to do with firewire, from the presence of the number 1394 and this thread: [http://ubuntuforums.org/showthread.php?t=156709](http://ubuntuforums.org/showthread.php?t=156709).  Turns out I was right, as disabling firewire in my bios eliminates the error.

It still halts the bootsplash screen at the same point as before, but now when it does so, the screen now reads

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)
```

I don't even have an error message or any keywords to search for.  I'm totally at a loss now, so I would really appreciate any assistance the community could provide.


System specs:

AMD Athlon XP 2600+
Asus A7N8XE-Deluxe
2 x 512gB DDR
ATI radion 9550

hda: 250gb maxtor (IDE)
hda1: 20gb, ntfs, windows
hda2: 20gb, ext3, ubuntu
hda3: 2gb, swap
hda4: ~200gb, fat32

hdb: 500gb Seagate (IDE, disconnected to protect my data from any 'oops' moments)
hdb1: 500gb, ntfs, archived data.  (Data to be moved to hda4, then hdb1 reformatted to fat32)


Edit - should probably add: md5 sum on iso and "CD check" are both fine.  Disk and image are perfect.

---

### Post by neanderthalman on 2007-12-18
ok, I have run memtest86, ram checks out (thank god)

I tried running in "recovery mode" and I got more information.  Instead of a bootsplash, it showed me what it was actually doing.  Here are the errors it generated before freezing.

```

kinit: no resume image, doing normal boot...
Done.
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init




BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

```

This gives me something else to search for.  Hopefully I can come up with something.  Again, if anyone has any idea what I could try, it'd be appreciated.

---

### Post by neanderthalman on 2007-12-18
Turns out was the UUID in menu.lst.  I changed

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=**UUID=9070C7B070C79AFC** ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=**UUID=9070C7B070C79AFC** ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
```

to

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=**/dev/hda2** ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=**/dev/hda2** ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
```

and it booted right up.  No more problems.

I hope that maybe this might help someone else in the future.

---

