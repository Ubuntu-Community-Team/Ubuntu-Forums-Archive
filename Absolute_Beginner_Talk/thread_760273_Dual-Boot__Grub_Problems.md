---
title: "Dual-Boot / Grub Problems"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by indiecast on 2008-04-20
I was running 7.10 perfectly, but decided to add WIN2000 to my system. i  was completely aware that i would have to reinstall grub, and i have done this before.  i wasn't expecting to get this tho...


grub> find /boot/grub/stage1

error 15: File not found


help? anyone? this is kinda urgent

---

### Post by zvacet on 2008-04-20
See if [this]("http://users.bigpond.net.au/hermanzone/p15.htm#15") can help you.

---

### Post by indiecast on 2008-04-20
sry, that's too vague for me

im trying this

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by indiecast on 2008-04-20
ok wait....

am i supposed to automatically have a /boot partition??????????

cause i dont

if so how do i get this back??


it seems like there is no /boot/grub/stage1 located on my computer


how do i fully install grub? cause i think this is what i need to do

---

### Post by indiecast on 2008-04-20
bump 

nothing is working here ahhhh

---

### Post by bodhi.zazen on 2008-04-20
can you list your partitions ? Boot the Ubuntu live CD and post the output of :

```
sudo fdisk -l
```

---

### Post by indiecast on 2008-04-20
ive got one other thing i want to try, and if that doesnt work ill post my results and list my partitions.

im not at home right now but i have them  memorized pretty much


/dev/sda2  windows 2000 ntfs  boot   6 GB
/dev/sda1  ubuntu 7.10    ext3           30GB
/dev/sda~  extended
--> /dev/sda~ swap

this is how it shows up in gparted as best as i can remember

"~" means im not sure what the number is here, its either 5 or 6 i think.

the main problem seems to be that the grub prompt cannot find the grub files when i try to restore grub to the MBR

---

### Post by indiecast on 2008-04-20
ok 

ive done an fsck

all the files are there


but it still cant find the files

the only thing different than before (when it worked), is that the windows and ubuntu partitions are  rearranged.  so im going to try to put them back the way they were. i think thats because the grub stuff wants to be where they were first installed.

if this doesnt work ive downloaded and burned a copy of the supergrubdisk

any have any ideas?

---

### Post by bodhi.zazen on 2008-04-20
You can likely fix the problem by editing /boot/grub/menu.lst and /etc/fstab on your ubuntu partition.

You will need to boot a live CD and edit those two files entering the proper partition information.

---

### Post by indiecast on 2008-04-21
ive seen stuff about /etc/fstab, and im wondering what fstab is.


EDIT: I looked up fstab and it looks like that could be the problem. Should i make sure all the mount points are correct or what?


2nd Edit:  Could this be the problem....

when everything worked my partitions were as follows:

/dev/sda1   ubuntu                 ext3     /    30 GB 
/dev/sda2   windows2000       NTFS         6   GB
/dev/sda~  extended
--> /dev/sda~ swap


now, after playing with things.... (when nothing is now working):

/dev/sda2   windows2000    NTFS           6   GB
/dev/sda1   ubuntu              ext3      /     30 GB
/dev/sda~ extended
--> /dev/sda~ swap


the first two partitions have been rearranged by me, but still have the same identifiers  (sda2 and sda1) is it possible that fstab is causing grub to look at the wrong partition to find its files?  or is "sda1" with ubuntu on it being hidden from grub somehow?

cause as i said before, the files are there, but when i try to reinstall grub through the grub prompt, they cannot be found

---

### Post by bodhi.zazen on 2008-04-21
Yes, you need to point both /boot/grub/menu.lst and /etc/fstab to the correct partitions.

Each file uses a slightly different syntax.

See if this link explains it :

[http://ubuntuforums.org/showthread.php?t=316237](http://ubuntuforums.org/showthread.php?t=316237)

Again, not exactly what you are doing, but similar enough it should apply ...

You can mount your partitions by UUID or label in /etc/fstab, but menu.lst must use grub terminology 

root (hdx,y)

---

### Post by indiecast on 2008-04-21
sweet thank you thank you thank you!

ill try that next!

---

### Post by indiecast on 2008-04-21
ahahahahahahahahahahahahahahaha


i changed the weird ID stuff to just the /dev/sda1 stuff and switched it around and stuff and nothing worked!

in the end i dont think those files were messed up at all...i mean its possible...but...



i simply ran that first grub command

```
sudo grub
```

instead of just

```
grub
```

and OMG I REALIZED THAT I WASTED TWO DAYS OF NOT USING MY FAVORITE DESKTOP BECAUSE I WAS TOO STUPID NOT TO RUN "grub" as ROOT!!!!!!!!!!!

i forgot that i did that the last time i fixed my grub.

to all of you out there that may be re-installing their grub....

ALWAYS REMEMBER TO ENTER THE GRUB PROMPT AS ROOT!!!!

once again, the code is....

```
sudo grub
```


haha this just made my day the second time...the first time was my girlfriend/bestfriend saying something cute, and the second was this!!!



thank you all those who tried to help, and im sorry im such a dunce,

indiecast

---

### Post by johnfarrow on 2008-05-16
[B]Hello,
I tried to install Hardy ona 8gb Flash drive on my laptop.  When I got through, I get grubb error 21. Here si what I get from sudo fdisk -l.

Partition 3 does not end on cylinder boundary.
/dev/sda4           11290       11435     1172745    5  Extended
/dev/sda5           11290       11435     1172713+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         935     7510356   83  Linux
/dev/sdb2             936         983      385560    5  Extended
/dev/sdb5             936         983      385528+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 4116 MB, 4116709376 bytes
11 heads, 10 sectors/track, 73094 cylinders
Units = cylinders of 110 * 512 = 56320 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              75       73095     4016128    b  W95 FAT32
john@npgcable:~$ 

Any ideas what I should do?  I had originally 7.10 and XP dual boot working ok before my mistake[/B]

---

