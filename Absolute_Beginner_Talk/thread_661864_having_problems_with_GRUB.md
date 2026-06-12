---
title: "having problems with GRUB"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by JewelOfSoul on 2008-01-08
I had winxp and ubuntu on the same hdd, but i had to format my windows partition and reinstall windows again, and now the GRUB won't show. i can't boot ubuntu. i've read this thread:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

but it won't help.

**_i tried this solution:_**

"1. Boot your computer up with Ubunto CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions

/
/boot
swap
.....

5. DO NOT FORMAT THEM.
6. Finish the manual partition"

i can't finish the manual partition because it says i must format the / partition in order to be used.

**_and this one:_**

"1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.
2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.
3. Type "grub" which makes a GRUB prompt appear.
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines."

when i type "find /boot/grub/stage1" and i do get a response: Error 15: File not found.

**_and this last one:_**

"1. Boot with any live CD (I've done it with Ubuntu Live DVD)
2. Get a root shell -> Applications / System Tools / Root Terminal
3. Make a folder -> mkdir /mnt/ubuntu "

and i get this:
mkdir: cannot create directory `/mnt/ubuntu': Permission denied

i'm really confused. please someone help!

---

### Post by taurus on 2008-01-08
```
**sudo** mkdir /mnt/ubuntu
```

---

