---
title: "Complete reinstall &amp; still no go"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by garyed on 2007-08-04
I gave up trying to fix Grub so I decide to fixmbr so my Win XP would be like a new installation.
I tested it & XP booted fine.
Then I booted to my Edgy 6.10 installation CD & did a complete new installation on my other HD. 
Two hard drives 0 using FAT32 - full partition & 1 using ext3 full partiotion.
I shut down & booted up & now I still can't get into Ubuntu from grub but if I choose windows from the menu I can get into XP just fine .

This time I get an " error 15:  file not found" immediately after I hit the Linux kernel entry on the menu.

All this on a computer that was dual booting fine with edgy & Win98 until I went to XP.
I am at my wits end on this one.

---

### Post by myk.dinis on 2007-08-04
if you could...let's walk through this...you have xp on hd0 (fat32) and Ubuntu on hd1 (ext2 or 3)...

You overwrote the MBR with grub again...and now it doesn't see your ubuntu...

I'm not trying to be weird but can I have a little more info...

I might be able to help...

---

### Post by myk.dinis on 2007-08-04
>gave up trying to fix Grub so I decide to fixmbr so my Win XP would be like a new installation.
>I tested it & XP booted fine.

-No residual linux?

>Then I booted to my Edgy 6.10 installation CD & did a complete new installation on my other >HD.

-Where did it install grub? Was hd0 marked boot?

>Two hard drives:

>0 using FAT32 - full partition  

>1 using ext3 full partiotion.

-Where's the swap?


>This time I get an " error 15: file not found" immediately after I hit the Linux kernel entry on the >menu.

Look to this post [http://ubuntuforums.org/showthread.php?t=297261](http://ubuntuforums.org/showthread.php?t=297261) for more answers....

---

### Post by Aurdal on 2007-08-04
What you want to do is press 'e' with the linux entry selected in grub, and edit the numbers in the "hd(0,0)" part. I don't know which numbers are correct for you, and if you don't know either you can use the 'try and fail' process and you'll get it eventually. When you manage to boot you'll want to run

"sudo gedit /boot/grub/menu.lst" and edit the same numbers. :)

---

### Post by be4truth on 2007-08-04
PLs post the file /boot/grub/menu.lst

---

### Post by garyed on 2007-08-05
Thanks for everyone trying to help,
I've been at this now for two days with no success.
The problem is I don't know how to get to read my ubuntu drive to post my menu.lst file.
When I boot from the CD  it won't read my hard drive. I don't know how to mount it. I've tried a suggestion about mounting the hard drive but it didn't work. 
My output from find /root/grub/stage1 is   (hd1,0)
So I do  root (hd1,0) & then
setup (hd0)
I get a screen that says its successful. 

I just have 2 HD's  no partitions on either or I should say each is  one full partition
0 =  XP
1 = Ubuntu

---

### Post by garyed on 2007-08-05
> **Aurdal said:**
> What you want to do is press 'e' with the linux entry selected in grub, and edit the numbers in the "hd(0,0)" part. I don't know which numbers are correct for you, and if you don't know either you can use the 'try and fail' process and you'll get it eventually. When you manage to boot you'll want to run

"sudo gedit /boot/grub/menu.lst" and edit the same numbers. :)

I tried your suggestion with just about every combination & nothing worked.
It seems that the first # is the HD & the second is the partition.
Any number other than "0" or "1"  for  the first  digit  returns " Hard Drive does not exist"
Any number other than "0" for the second digit returns  " no such partition"
My only possibile options are therefore (hd0,0) which returns : file not found" or (hd1,0)
which just starts the Ubuntu logo & locks up. 
I'm lost

---

### Post by garyed on 2007-08-05
One more thing I noticed
When I boot with the CD & try to change grub to (hd1,0) like it shows in the find command
it shows successful but when I reboot grub always returns to (hd0,0)

---

