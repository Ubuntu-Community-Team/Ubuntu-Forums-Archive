---
title: "dual boot windows/ubuntu with ubuntu on an external hard drive?"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by Roland Bouman on 2005-12-28
Hi folks, 

I've got a desktop personal computer that's currently running windows XP. I might switch to Ubuntu (or andother Linux) fully in the future, but right now, I want to have a dual boot system so I can explore Ubuntu while still being able to do my work on windows. 

Now, I probably could make a new partition on the harddisk and install ubuntu there. But what I really want is to install ubuntu on a (USB) external hard disk.

So, I ran the installation, and told the installer to install ubuntu on that disk. I also had it install grub into the master boot record to setup the boor menu.

The first phase of the installation finishes without any problems, and I arrive at the point where I'm asked to remove the installation media. The system reboots, and I'm offered a boot menu. :D 

When I choose to boot Linux, I see some messages being printed on the screen, the Ubuntu logo appears, some more messages appear there ("Loading modules"  etc.)

Then, the logo dissappears, and I see the following messages:

  Booting 'Ubuntu, kernel 2.6.12-9-386 '

root   (hd1,4)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sda5 ro quiet splash
    [Linux-bzImage, setup=0x1c00, size=0x1224b1b]
initrd /boot/initrd.img-2.6.12-9-386
    [Linux-initrd @ 0x1fb3a000, ox4b568a bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
Loading, please wait...
ALERT! /dev/sda5 does not exist. Dropping to a shell!


BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't access tty; job control turned off
#


Now, I understand that the last couple of lines and the last error message have to do with the shell (I don't really expect it to work as we're in the middle of installing the OS). Also, I understand that the first error message ("ALERT! ...") is what really matters. 

I also learned that /dev/sda5 has to do with the (supposedly created) partition on the external hard drive, and that this is actually some sort of directory Linux wants to use to address the device. 

Clearly, the OS cannot address the hard drive, at least not at this stage of the OS loading process.

I also gather, that reverting to a shell is some sort of means that could be of use to fix the problem at that point. However, I haven't got a clue from this point on. 

Oh yeah, I did do a check using the shell:

# pwd
/
# ls dev/sda5
ls: dev/sda5: No such file or directory

(So, yeah, it really does not exist at this point)

Can anybody give me some advice? I really don't know what I should do now :(

---

### Post by aysiu on 2005-12-28
Maybe this?
[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

---

### Post by Roland Bouman on 2005-12-28
Thanks! 

This was exactly what I needed :D 

(I'm posting this from my freshly installed firefox that ships with Ubuntu :cool: )

---

