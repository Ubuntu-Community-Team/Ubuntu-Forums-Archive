---
title: "Error 17 on Dapper Drake rebooting on Dell Inspiron"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by amersault on 2007-05-29
i'm new to the forums (and Linux), so please forgive me if this has already been posted elsewhere. i recently resurrected my dusty old Dell Inspiron 5000 and loaded it w/ UBUNTU (Dapper Drake). everything worked flawlessly, wireless out of the box, and no complaints. however ran into a small glitch on shut down yesterday, where it didn't complete the cycle last night and i opted to hit the power switch instead. 

rebooted this evening and got the following error:

    BOOTING FROM LOCAL DISK...

    GRUB LOADING STAGE 1.5

    GRUB LOADING, PLEASE WAIT...

    ERROR 17

so far running on the Live CD boots to desktop w/ no problems. is there a way to restore from the CD or should i just reinstall instead?

---

### Post by sankarv on 2007-05-29
try to install grub again with the live cd. that might work. also if possible check if the boot directory and others are there with the live cd in the linux partition u installed in your harddisk.

search the forums. u  can get solution from there....

---

### Post by EdThaSlayer on 2007-05-30
You might have to restore grub. 
Use this guide, you will need to use the livecd. 
I got this guide from:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)
> 
If you've installed GRUB into the Root Partition instead of the MBR, the commands are a little different. Here's are the instructions that I have for my system:

How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

Hope this helps. Since I use Norton Ghost to make regular backups and restores (I do a lot of testing), I do this all the time...

-Warr

or visit this thread for a proper guide :)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

or better yet :D 
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

---

### Post by amersault on 2007-05-30
thanks for the replies! Ed, i tried what you suggested (quotes) but i got this in reply running Grub:
[INDENT]
grub> find /boot/grub/stage1

Error 15: File not found[/INDENT]

i guess i should try to reinstall, then?

---

### Post by sankarv on 2007-05-30
check if the linux partition exists and then try installing grub. its no use without the linux system directories (/boot and partly others) existing in the partition.

---

### Post by sankarv on 2007-05-30
putin the live cd of ubuntu and check if its mounting those things (manual/auto) and see if the /boot dir (also others) exists in the linux partition ...

---

### Post by amersault on 2007-05-30
thanks, Sankarv. stupid beginner question - how do i do that? are there any commands i can run through terminal once the LiveCD loads? might need a step by step process guide here... hehe

---

### Post by amersault on 2007-05-30
actually, we can close this thread. i tried pulling info by typing in fdisk -l in Terminal and it brought up nothing (just another error). 

so opted for a complete reinstall instead - less of headache and problem solved.

---

