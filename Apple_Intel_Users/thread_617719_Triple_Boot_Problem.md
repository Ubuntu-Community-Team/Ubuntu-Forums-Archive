---
title: "Triple Boot Problem"
date: 2007-11-19
forum: Apple Intel Users
---

### Post by Black Mage on 2007-11-19
Hey, I 've been running a dual boot of Mac OS X and Linux for a while. I had three partitions all along and today I decided to make my third partition windows xp. I had actually had 5 partitions: an 60 gig for mac os x, a 17 for ubuntu, a 15 that was unused, a 200 meg with an unknown format and a 128 unused. I had to delete the 200 meg in order to install XP on the 15 gig because it kept saying maximun number of partitions.

The problem now is I can't get back to my Linux Partition. I;m using reFit and my linux partition has completely disappeared. When I booted back into OS X, 3 partitions where there, OS X, Windows and Linux, and I saw this using diskutil in the command line.

So how do I get back to my Ubuntu OS? Please help.

---

### Post by cyberdork33 on 2007-11-19
> **Black Mage said:**
> Hey, I 've been running a dual boot of Mac OS X and Linux for a while. I had three partitions all along and today I decided to make my third partition windows xp. I had actually had 5 partitions: an 60 gig for mac os x, a 17 for ubuntu, a 15 that was unused, a 200 meg with an unknown format and a 128 unused. I had to delete the 200 meg in order to install XP on the 15 gig because it kept saying maximun number of partitions.

The problem now is I can't get back to my Linux Partition. I;m using reFit and my linux partition has completely disappeared. When I booted back into OS X, 3 partitions where there, OS X, Windows and Linux, and I saw this using diskutil in the command line.

So how do I get back to my Ubuntu OS? Please help.

Windows has over written the bootcode in the MBR (which is OK). You will need too reinstall Grub. See the "multibooting correctly" guide in my signature.

---

### Post by Black Mage on 2007-11-19
But I can't boot into my Linux, only windows and mac. How do I install it from there?

---

### Post by cyberdork33 on 2007-11-19
> **Black Mage said:**
> But I can't boot into my Linux, only windows and mac. How do I install it from there?
boot from live cd to complete the operation.

---

### Post by Black Mage on 2007-11-19
Ok, everything went ok with the grub, i got an hd(0,1) only, set in grub i did the root and then setup and it said succed. Then I quit grub and reboot and the Linux came up, expect when I tried to boot in Linux I got an error 17: partition cannot be booted or selected. I pressed enter to continue and it showed the Kernels but whatever kernel I choose, it didn't boot.

What could be causing this error?

---

### Post by cyberdork33 on 2007-11-19
> **Black Mage said:**
> Ok, everything went ok with the grub, i got an hd(0,1) only, set in grub i did the root and then setup and it said succed. Then I quit grub and reboot and the Linux came up, expect when I tried to boot in Linux I got an error 17: partition cannot be booted or selected. I pressed enter to continue and it showed the Kernels but whatever kernel I choose, it didn't boot.

What could be causing this error?
you set the wrong partition somehow. Normally, (hd0,1) would be your OSX partition.

can you give the output of:
```
sudo parted /dev/sda print
```

```
sudo fdisk -l /dev/sda
```

---

### Post by Black Mage on 2007-11-19
I sorta fixed the problem. I changed the /boot/grub/media.list and changed all the (hd0,2) to (hd0,1), since grub find vmlinuz gave hd0,1 and not hd0,2. So it booted but couldn't find find a UUID and thus booted to root in command prompt. But when I did the command "reboot" as root, it rebooted into the normal Ubuntu.

And thats where I'm at now, a really strange boot up.

---

### Post by cyberdork33 on 2007-11-19
> **Black Mage said:**
> I sorta fixed the problem. I changed the /boot/grub/media.list and changed all the (hd0,2) to (hd0,1), since grub find vmlinuz gave hd0,1 and not hd0,2. So it booted but couldn't find find a UUID and thus booted to root in command prompt. But when I did the command "reboot" as root, it rebooted into the normal Ubuntu.

And thats where I'm at now, a really strange boot up.

Yea for some reason some application detects drives incorrectly on the Mac Pros. I am not sure what is the cause.

---

