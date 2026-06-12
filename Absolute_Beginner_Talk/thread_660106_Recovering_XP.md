---
title: "Recovering XP"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by tnanek on 2008-01-06
I am a brand new Linux user, and I just installed it on one of my extra hard drives.  The intention was to have a dual boot system alongside my Windows XP Pro installed on a separate hard drive.  Unfortunately I hadn't looked for guidance before hand and I just went ahead and installed Ubuntu.  Now I can only boot in Ubuntu (even in the boot menu when I select the hard drive XP is installed on, it doesn't work), and cannot figure out how to boot to windows (which is still there - I can see the files on the other hard drive, and am archiving them now just in case it comes to having to reinstall XP)

The version I downloaded and installed was named the following:
ubuntu-7.10-desktop-i386.iso
although now I realize the proper version to have installed should have been the alternate one.

---

### Post by PeterJS on 2008-01-06
What happens when it fails? any error messages?

---

### Post by tnanek on 2008-01-06
No error messages - it just boots from Ubuntu as if thats what I wanted it to do.

---

### Post by cartisdm on 2008-01-06
if you manually disconnect the Ubuntu HD and set your XP as the master can you boot using there?  Your GRUB loaders could be conflicting somehow

---

### Post by bumanie on 2008-01-06
Post the output of 
sudo gedit /boot/grub/menu.lst (that is a lower case L)
and someone will be able to guide you as to your next best step.

---

### Post by tnanek on 2008-01-06
All of it that is not notes is below:

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe0c1321-f4e0-426b-ab73-3714b8beba49 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe0c1321-f4e0-426b-ab73-3714b8beba49 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet


---

### Post by tnanek on 2008-01-06
The last one was a little incomplete, below is full:

> 
default		0

timeout		3

hiddenmenu

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe0c1321-f4e0-426b-ab73-3714b8beba49 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=fe0c1321-f4e0-426b-ab73-3714b8beba49 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet


---

### Post by PeterJS on 2008-01-06
That's a single boot ubuntu configuration. So first thing is to comment out the hidemenu line to unhide the boot menu, change the time out something more reasonable like 10 seconds, and lastly add a block to boot XP.
```

title           Microsoft Windows XP Professional
root            (hd0,0) # <-- this bit is going to be different and depends on where windows is installed.
savedefault
makeactive
chainloader     +1

```

The output from:
```

fdisk -l

```
Will tell us about the paritions on your hard drive, and from that finding windows should be pretty easy (it should be the only NTFS parition).

---

### Post by tnanek on 2008-01-06
It works now, thank you so much!

I took a guess as to where Windows was saved (seeing as it is on the D: and the E: is where I have Ubuntu, D: should be bus 0 drive 1, C is bus 0, drive 0, E: is bus 1, drive 0) and I got it right!  Thanks again!

title           Microsoft Windows XP Professional
root            (hd0,1) # <-- this bit is going to be different and depends on where windows is installed.
savedefault
makeactive
chainloader     +1

---

