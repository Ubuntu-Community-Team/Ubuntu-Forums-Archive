---
title: "Ubuntu will not boot up..."
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Gasmask14 on 2007-12-30
Hello, I installed Ubuntu on my desktop about 3 weeks ago (see sig) and it worked wonders with everything (compiz, wireless keyboard, wireless network, etc) but I recently moved it into my bedroom and put it under my desk. The only problems I had with it was the fact that it would never truly restart and the wireless stoped working suddenly (D-Link WDA-1320). It would only hang at the begining of startup after restarts and I had to maually turn it off or just shut it down from my desktop screen and turn it back on.  It worked for about a week in my room and now it will not even boot up.

When I turn it on I get a blue HP screen and then the screen turns black and enters the GRUB loader. Then it says:

Starting up...
[              18.406635] Kernal panic - not syncing : VFS : Unable to mount root fs on Unknown-block(0,0)

It stalls after that and then my moniter shows optimal resolution notifierscreen of 1280x1024 in the center of the screen in a bluebox and then disappears (don't know if it has anything to do with it). The only way to get out of this loading screen is to manually turn it off by the front button (cold shutdown). It will boot of of my Gusty Live CD but tells me I do not have permission to see my files on my hard drive (but acknowledges they are there).

I have no idea how fix it and would gratefully accept any assistance. Thanks.

---

### Post by philinux on 2007-12-30
Gutsy had a kernel upgrade recently that seemed to mess with the grub loader. so your system is intact just grub thats slightly messed up.
Not sure if your problem is the same but take a look at these see if they help.

[http://ubuntuforums.org/showthread.php?t=648201](http://ubuntuforums.org/showthread.php?t=648201)
[http://ubuntuforums.org/showthread.php?t=645116](http://ubuntuforums.org/showthread.php?t=645116)

---

### Post by Gasmask14 on 2007-12-30
Okay so what do i need to change once I get into the Grub menu? From the menu it gives me the three boot options (Ubuntu, Ubuntu Recover, memtest86+) so I entered the first with the "e" command. It shows 4 options: rot (hd0,0), kernal, initrd, and quiet. I ented the root  with the "e", so what now?

---

### Post by philinux on 2007-12-30
Ok from what I can see.

It you do these two commands and compare the uuid's 

cat /etc/fstab

cat /boot/grub/menu.lst

The uuid I guess is not the same in grub as in fstab. If it's the same then something else the problem

you need to copy and paste the correct uuid from fstab into grub for your linux boot so they match.

> My Grub
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9024104a-fa2f-4f85-bb6d-385637bdee48 

My fstab
# /dev/sda1
UUID=9024104a-fa2f-4f85-bb6d-385637bdee48

Back up your menu.lst first though

---

### Post by Gasmask14 on 2007-12-30
Okay, when I type the first command (cat /etc/fstab) it gives me what I think are the two partitions (the actual space,ext3, and the swap partition). 

When I type the second command (cat /boot/menu/.lst) it tells me:

Error 15: File not found

So I think I have two questions

1. How do I back up my menu.lst?

2. How do I copy and past the UUID(is this the partition)?

---

### Post by philinux on 2007-12-30
Ok your command is wrong you used

cat /boot/menu/.lst instead of

cat /boot/grub/menu.lst.

to backup

sudo cp /boot/grub/menu.lst       /boot/grub/menu.lst.backup

Copy and paste the commands to save typo errors. Lets see if the uuid's match eh?

---

### Post by Gasmask14 on 2007-12-30
Alright

My grub looks like this using cat /boot/grub/menu.lst.

title                                                                     Ubuntu 7.10, kernal 2.6.22-14-genaric
root                                                                    (hd0,0)
kernal                                                                 /boot/vmlinuz-2.6.22-14-genaric root=UUID=f6a5a90b-4a32-4a0f-a47e-f5d568e166c6 ro quiet splash
initrd                                                                   /boot/initrd.img-2.6.22-14-genaric
quiet

When I use cat /etc/fstab I get:

UUID=f6a5a90b-4a32-4a0f-a47e-f5d568e166c6 /

then to the right and directly elow I get defaults,errors=remount-ro 0

---

### Post by Gasmask14 on 2007-12-30
bump

---

### Post by Gasmask14 on 2007-12-31
double bump

---

