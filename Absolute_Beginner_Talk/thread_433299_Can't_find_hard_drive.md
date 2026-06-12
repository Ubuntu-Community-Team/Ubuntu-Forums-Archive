---
title: "Can't find hard drive"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by strikeback03 on 2007-05-04
I had to use the "all_generic_ide" option to get the Feisty LiveCD to boot.  It installed, but often will not boot from the hard drive now.  trying in recovery mode, it at least says what it is doing, and eventually throws ```
 ALERT! /dev/disk/by-uuid/(full uuid) does not exist.  Dropping to a shell!
```

how do I get it to consistantly find my hard drive?

---

### Post by ajmorris on 2007-05-05
> **strikeback03 said:**
> I had to use the "all_generic_ide" option to get the Feisty LiveCD to boot.  It installed, but often will not boot from the hard drive now.  trying in recovery mode, it at least says what it is doing, and eventually throws ```
 ALERT! /dev/disk/by-uuid/(full uuid) does not exist.  Dropping to a shell!
```

how do I get it to consistantly find my hard drive?

edit /boot/grub/menu.lst, then remove the UUID entry from the current kernel.

Also alternatively, you could edit /etc/fstab and get the UUID from there and replace the one in /boot/grub/menu.lst.

---

### Post by strikeback03 on 2007-05-05
anytime I have been able to boot Feisty (through LiveCD or install) the UUID of the drive matches the one in that error.  When it throws the error I can't interact at all to see what the UUID has changed to.

If I remove the UUID from menu.lst, will it just boot from the location name (/dev/sda3 in this case)?

---

### Post by paechan on 2007-05-13
Im having the same problem, except i can never get it to boot. I have tried checking the fstab uuid with the menu.list uuid and they are the same. Its really strange because i can see the entire filesystem when i boot with livecd, but it somehow doesnt exist when i try to boot through grub. 

I tried booting with livecd and doing a e2fsck -y /dev/hda6 but nothing has changed.

Any ideas?

---

### Post by Herman on 2007-05-14
Hello paechan,
Try booting up a LiveCD and get a list of your file systems and their UUID numbers by typing the following command (or copying and pasting this one), in a terminal,
```
ls /dev/disk/by-uuid/ -alh
```Then do something like what is described in the following link to mount your Ubuntu partition and edit your menu.lst.  [                                  Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
Copy and paste your current UUID for the Ubuntu partition over the existing UUID if it is not the same. You may also need to edit your /etc/fstab file as well.

If the file system UUID has been changed somehow, (maybe you used some partitioning software recently?), then both the menu.lst and the /etc/fstab will still have the old UUID numbers, so both will need to be updated.
Please don't be shy to ask if you need any more help,
Regards, Herman :)

---

