---
title: "dual boot failure"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-12-27
hello

i have a problem with my ubuntu 7.10 install on my new dell. i installed using the alternate CD alongside windows xp home. everything was pretty much straight forward until the partition setups. i used the manual set up because i was tryin to install ubuntu on a specific partition.

unfortunately, Dell has a bunch of partitions which i havent deleted yet so it gave me problems. there is a FAT16 partition that is about 50 MB and then my C: drive and then another FAT32 3 gig partitation. i manually made a new partition for ubuntu. the setup looked clean but then ubuntu started complaining about how the cluster sizes werent correct and that the sizes did not match. i went ahead and clicked 'ignore' hoping it wont give me too much of a problem.

then it did install correctly until it got to the GRUB part. it identified the windows xp but it failed to install to 'hd0'. i tried installin it a few times, but i got the same error. so i installed lilo instead and it did that correctly. however, when i restarted the computer, it just loaded linux and there was no option to select windows. argh.

please help. i want access to both but if that wont happen i want to at least not lose my windows xp install. thank you to all that try to help. ill be patiently refreshing this post. =]

---

### Post by Moop on 2007-12-27
It shouldn't be a problem getting both OS's to boot. The SuperGrub disk works great.

Take a look at this page. [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Miroku on 2007-12-27
> **Moop said:**
> It shouldn't be a problem getting both OS's to boot. The SuperGrub disk works great.

Take a look at this page. [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

yes, that website is awesome, i frequent it several times. i was able to get into my windows partition with supergrub disk and i did read some info concerning GRUB, but here is the question, can i install GRUB now that i have installed lilo? if so, how? thx.

---

### Post by meierfra on 2007-12-27
> can i install GRUB now that i have installed lilo?
Yes.

Did you install lilo? Or did SuperGrub just fix the MBR?

Are you able to boot into Ubuntu? (with help of  SuperGrub or any other way) 

If not,  do you have  a Ubuntu Live CD and can successfully boot from the LifeCD?

---

### Post by Miroku on 2007-12-27
> **meierfra said:**
> Yes.

Did you install lilo? Or did SuperGrub just fix the MBR?

Are you able to boot into Ubuntu? (with help of  SuperGrub or any other way) 

If not,  do you have  a Ubuntu Live CD and can successfully boot from the LifeCD?

yes, i installed LILO when GRUB failed to install the first time around. i did not use supergrub to fix anything, i just used it to boot back into windows.

i am able to boot into ubuntu (it uses LILO) and there is no option to boot windows.

i do have a ubuntu 64 bit 7.10 live cd.

---

### Post by Miroku on 2007-12-27
Bump.

cuz im waitin for hellpppp.

---

### Post by Tango_Down on 2007-12-27
SO, you want to know how to add windows to the LILO boot list? 

Try adding this stanza to your lilo.conf, which can be found in the /etc/ directory:
other=/dev/hda1
label=Win2k
table=/dev/hda

---

### Post by Miroku on 2007-12-27
well, being impatient got the best of me. using supergrubdisk, i did fixmbr, so now to access linux, i must use the boot disk. which i will do until i can get GRUB somehow. i am much more comfortable with GRUB because thats the only one have i have fiddled with for the past year. using LILO was just a last resort kind of thing.


if it comes down to it, ill just format the full 250 gigs and set up the partitions how i want and GRUB should not give me a problem.

thx for the LILO info Tango_Down -- but i need help gettin GRUB and being able to choose between the two OSes when i boot up my comp.

i dont understand why GRUB would not install in the first place, but i can only blame this retarded Dell Utility partition that is positioned before the main NTFS partition.

TIA.

---

### Post by meierfra on 2007-12-27
Sorry for the delay (but I still have a little bit of a real life left)

I need some information, before I  can tell you how to get Grub to work. Boot into ubuntu and post the output of the following commands:


```
sudo fdisk  -l

ls  /boot/grub

cat /boot/grub/menu.lst
```

---

### Post by Miroku on 2007-12-28
> **meierfra said:**
> Sorry for the delay (but I still have a little bit of a real life left)

I need some information, before I  can tell you how to get Grub to work. Boot into ubuntu and post the output of the following commands:


```
sudo fdisk  -l

ls  /boot/grub

cat /boot/grub/menu.lst
```

hey, sorry for the delay

so i was trying to log back in using supergrub disk, but apparently the linux partition is not being recognized for some reason

i dont want to deal with the headache of a bad install so i think i will have to format the drive and get rid of these other partitioins.

i attached the layout of my partitions just for reference. i plan on gettin rid of the H: partition at the beginning of the drive and shifting the C: back to the beginning. so hopefully it will just be partition C:, F:, and G:. i will use the F: as my linux partition and the G: as fat32. GRUB shouldnt give me a problem, should it?

the only reason i think GRUB gave me a problem before was because of that first fat16 H: partition.

well onto reinstalling XP, then ubuntu. argh. but man if GRUB gives me a problem after this, i will have a real issue with this junk!

[IMG]http://img80.imageshack.us/img80/9053/39030080ud9.jpg[/IMG]


it would be awesome if i could just install linux without playing around with these partitions. Thanks for helping.

---

