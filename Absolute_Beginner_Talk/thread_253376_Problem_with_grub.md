---
title: "Problem with grub"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by g0nzo on 2006-09-08
Hi!

I've created a new partition in windows and now I can't boot to any system, because I get grub error 17.

It was rather stupid, because creating new partition changed numbers of both linux partitions (/ and swap) and probably that's why it doesn't work.

I've started system from Kubuntu live cd and mounted my linux partition. Which files should I change to fix grub (if that's the real cause of the problem).

Now I've got following partitions:
/dev/sda1 - windows (ntfs)
/dev/sda5 - data (ntfs)
/dev/sda6 - new partition (ntfs)
/dev/sda7 - kubuntu (ext3)
/dev/sda8 - kubuntu (swap)

In boot/grub/menu.lst I've got:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda6 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot


Should I change something in this file, maybe in some other files, or maybe there's a way to automatically configure grub?

Thanks in advance

---

### Post by cotcot on 2006-09-08
Your new partition has shifted the number of all partitions after it with 1 unit.
So in the ubuntu entries you need to replace 

```
root (hd0,5)
```  with ```
root (hd0,6)
```

and

```
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sda6 ro quiet splash
```  with 
```
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sda7 ro quiet splash
```

---

### Post by raldz on 2006-09-08
1. Insert the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. type: "find /boot/grub/stage1"
5. Type "root (hd0,6)", or whatever is the result from number 4
6. Type "setup (hd0)", or whatever your harddisk number is, this will install GRUB in the MBR.
7. Quit grub by typing "quit".
8. Reboot.

---

### Post by djsroknrol on 2006-09-08
I would suggest reinstalling grub. Search for reinstalling grub in the search box. There are a few good ways of doing it and they can be found there.

---

### Post by Rui Pais on 2006-09-08
hi it seems that your problem is the several references on your menu.lst to root (hd0,5). Thats pointing to /dev/sda6.

You could change all from (hd0,5) to (hd0,6). That should solve your problem.

Another solution depends on the correct order of your partitions.

If you make your new sda6 on a space of the disc ***after*** the last one, the kubuntu swap, you can automatically reorder the partitions table by running from a livecd:
```
sudo fdisk /dev/sda
``` 
then press 'x' key
then 'f' key (fix partition order)
and finally 'w' to write and exit.
In that case, if fixed, of course, implies that you would not change your menu.lst.

---

### Post by g0nzo on 2006-09-08
Thanks guys!

The first solution with changing menu.lst manually didn't work.
I had also troubles with the second one, because it kept telling me that the file can't be found.
Then I looked for 'reinstalling grub' and the second solution was almost correct - I had to run 'sudo grub' instead of 'grub'.

Thanks again, now I'll install vista rc1 on my new partition, so these information may become very useful again in the next few minutes :)

---

### Post by raldz on 2006-09-08
> **g0nzo said:**
> Thanks guys!

The first solution with changing menu.lst manually didn't work.
I had also troubles with the second one, because it kept telling me that the file can't be found.
Then I looked for 'reinstalling grub' and the second solution was almost correct - I had to run 'sudo grub' instead of 'grub'.

Thanks again, now I'll install vista rc1 on my new partition, so these information may become very useful again in the next few minutes :)

Sorry I forgot the "sudo" thing.. the solution I posted is a general solution for GRUB.. I have just recently used it on my MEPIS machine, and have forgotten to prepend the sudo as for Ubuntu.. and besides, if you choose the boot in recovery mode in Ubuntu, you won't need sudo..

---

