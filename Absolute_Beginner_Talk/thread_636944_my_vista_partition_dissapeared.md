---
title: "my vista partition dissapeared?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by nicolito on 2007-12-10
Greetings. I have encountered an odd problem. I do not know if it's due to vista or something ubuntu did.
While using ubuntu one day my vista partition disappeared. It literally vanished from my desktop while I was looking at it. Now I can't boot into vista. It only gives me "windows could not startup" and insists in using its lousy problem solver that does nothing. 
The MBR seems alright when cheking with testdisk except for a "incorrect nu ber of heads/cylinders" message. 
The partition is still there (checked with gparted). I can mount it but it isnt readable.
I have looked everywhere for a similar problem and read horseloads of stuff about multibooting, but I am getting nowhere...
Does anyone have ANY idea of what might have happened?:confused:

All ideas are greatly appreciated

This is what testdisk tells me

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1 16099 108 25  258637201 [HP]
 2 P HPFS - NTFS          29738  90  1 30400 239 63   10644480 [Recovery]
 3 P Linux                16100   0  1 29360 254 63  213037965
 4 E extended             29361   0  1 29737 254 63    6056505
 5 L Linux Swap           29361   1  1 29737 254 63    6056442








*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

---

### Post by nikoPSK on 2007-12-10
I think it died. :( try this:

```
sudo fdisk -l
```

---

### Post by njparton on 2007-12-10
The Master Boot Record (MBR) may have been deleted.

Search google for the many freeware recovery software out there.

---

### Post by TheLions on 2007-12-10
you must shut down vista properly if you want see that partition in ubuntu!

---

### Post by meborc on 2007-12-10
this is not something that would happen without somekind of human interference :) sorry

so can you retrace your steps... were you deleting some files? were you using the terminal while being root?

it has to be something as simple as this (or it is a physical error, then there is nothing much to do)

---

### Post by Ub1476 on 2007-12-10
Your Vista partition is there, but you need to make it "visible": [Super Grub Disk]("http://supergrub.forjamari.linex.org/") will fix it for you. You need to burn it to a CD and boot it.

---

### Post by nicolito on 2007-12-11
thanx for the replies.

MBR is still there and intact. Checked that. I am sure it was something I did, but it was too long ago for me to remember exactly what I did. I do remember I reformatted my external drive with Gparted right before it disappeared, but I cannot understand how that could  affect the partitions my harddrive?:confused: 

I don't believe anything is gone either because I can see every file and directory of my vista partition using testdisk and gparted reports the used and free space correctly.

If super grub disk helps I would gladly try that. I already have a copy on a cd. How exactly do I use it for this particular problem?

---

