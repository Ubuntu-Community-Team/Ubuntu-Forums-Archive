---
title: "Dual booting window$ 2K n Ubuntu Dapper"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Twiggy003 on 2006-09-02
Reacently i got myself a new 250gb westen digital caviar harddrive, and i partitioned it so it had a NTFS partition and space left for ext3 and swap, windows installs fine, boots up fine etc but after i install Ubuntu from the liveCD, Linux boots fine from GRUB but when i select windows it goes through the windows is loading then gives me a sort of BSOD

like so:

*** STOP: 0x0000007B (0x81FF1030,0xC000014F, 0x00000000, 0x00000000)



If this is the first time you've seen this Stop error screen,

restart your computer.  If this screen appears again, follow these steps:



Check for viruses on your computer. Remove any newly installed

hard drives or hard drive controllers. Check your hard drive

to make sure it is properly configured and terminated.

Run CHKDSK /F to check for hard drive corruption, and then

restart your comptuer.



Refer to your Getting Started manual for more information on

troubleshooting Stop errors.


any help would be appreciated, ive looked on this forum already and havent found any luck.

---

### Post by bulldog on 2006-09-02
Well this has nothing to do with grub or Ubuntu.
When Windows start booting up and then fails,it's in your Windows where it's going wrong.
You should check your Windows install and your drivers.

Run the stop code in google and see what's coming out of it.

---

### Post by Twiggy003 on 2006-09-02
thanks.  but this error only happens after Ubuntu and GRUB are installed, i just guessed they had something to do with it, ive tried formatting the whole thing and trying again a few times, all i do install is the basic drivers on windows before installing Ubuntu, but i'll try going through it again carefully. Google seems to find quite a few pages also, thanks again.

---

### Post by Twiggy003 on 2006-09-14
Ok, ive tried putting on windows XP to see if that would be any different...but once again i get a error message, but, if i delete the other partitions windows boots fine.  so im still a bit stuck, any help would be..helpful

---

### Post by youthforlinux on 2006-09-14
This happened to me for a long time until I found a different solution.  Instead of installing Windows first I found that installing Ubuntu first was the better option using the live cd. Then i used gparted in the live cd to use the remaining disk space that i left behind for windows and to make an ntfs partition.  Then i installed Windows on the NTFS partition created with gparted.  Then i used the live cd to restore grub and it worked for me.

P.S. when u are creating your partition table take care to make sure that u create a fat32 to be able to share files between the two operating systems before you install windows 2000.
It worked for me and i hope it works for u.:wink: :wink: :D :D

---

### Post by Twiggy003 on 2006-10-10
When i do that, Window$ recognises it as one partition and the only option i have on there is delete then create new partition, only once it displayed all  partitions but that was onto a unclean NTFS partition, so im still a bit stuck.

---

