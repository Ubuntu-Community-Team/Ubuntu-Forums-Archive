---
title: "Partition"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-13
Can someone confirm for me one way or the other whether and if, how i can shave some off my hard drive to create, effectively, another partition.

Looked at Qparted but if there is a way of doing that it is not intuitive or obvious to me.

essentially, i'm looking at keeping my present install but want to shave some off to create a dual boot

Many thanks as always,

--
sophtpaw

---

### Post by aysiu on 2005-09-13
[QUOTE=sophtpaw]
Looked at Qparted but if there is a way of doing that it is not intuitive or obvious to me.[/QUOTE] I was going to recommend QTParted, actually. What about it isn't intuitive or obvious?

If I'm remembering correctly, you just right-click the partition you want to resize and then resize it and commit the changes.

[http://qtparted.sourceforge.net/screenshots.en.html](http://qtparted.sourceforge.net/screenshots.en.html)

---

### Post by davmac on 2005-09-13
I've had success doing this with Ranish partition manager available on the Ultimate Boot CD ([http://www.ultimatebootcd.com/)](http://www.ultimatebootcd.com/)).

---

### Post by sophtpaw on 2005-09-13
[QUOTE=aysiu]I was going to recommend QTParted, actually. What about it isn't intuitive or obvious?

If I'm remembering correctly, you just right-click the partition you want to resize and then resize it and commit the changes.

[http://qtparted.sourceforge.net/screenshots.en.html](http://qtparted.sourceforge.net/screenshots.en.html)[/QUOTE]


thanks Aysiu,

i hadn't right-clicked  ](*,)   but i did highlight the hda and then didn't find the relevant icon did anything.

So, you are confirming i can resize my partition in order to create a dual boot without killing my present install?


thanks again, i always appreciate the help

--
sophtpaw

---

### Post by aysiu on 2005-09-13
[QUOTE=sophtpaw]
So, you are confirming i can resize my partition in order to create a dual boot without killing my present install?[/QUOTE] Are you resizing a Windows partition? Because if you are, you should defragment it before you resize it. And whether you're resizing a Windows or Linux partition, you should **always back up your files and settings**. 

Partitioning works about 99% of the time, but you should be prepared for that 1% when it doesn't work. It would really suck to lose all your files.

---

### Post by sophtpaw on 2005-09-13
[QUOTE=aysiu]Are you resizing a Windows partition? Because if you are, you should defragment it before you resize it. And whether you're resizing a Windows or Linux partition, you should **always back up your files and settings**. 

Partitioning works about 99% of the time, but you should be prepared for that 1% when it doesn't work. It would really suck to lose all your files.[/QUOTE]

No, Aysiu, 

I only have Ubuntu on my 80 gig hardrive. I know i should have thought of it before but i just went for the easy default install and didn't bother then with partition. But 80 is extravagant and i would like to be able to test and try other stuff too.

So, to the point. I have ubuntu on hda. i went to qparted right-clicked but the resize function does not highlight hence ( i read) apply? 
the format function does highlight but then what? Could you give me some guidelines here so i don't accidentally delete the whole hard drive

obligado,

--
sophtpaw

---

### Post by az on 2005-09-13
[https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

Yes, you can shrink a partition and dual boot.  It is much simpler to just use the installer to do all your partitioning.

The Breezy installer will default to offering to create some free space for you, rather that you having to do it by hand, as detailed in the link above.

---

### Post by aysiu on 2005-09-13
[QUOTE=azz]It is much simpler to just use the installer to do all your partitioning.[/quote] That's a good point, actually. Almost every Linux distro you try out (to dual-boot with Ubuntu) will probably come with its own partitioner during the install process. I'd personally recommend downloading the first disk of Mandriva just for DiskDrake. I haven't found a better free partitioning tool.

[http://doc.mandrivalinux.com/MandrivaLinux/101/en/Starter.html/diskdrake.html#id2576559](http://doc.mandrivalinux.com/MandrivaLinux/101/en/Starter.html/diskdrake.html#id2576559)

You can always use the "install" process just for DiskDrake and then install another distro instead of Mandriva.

---

### Post by sophtpaw on 2005-09-13
[QUOTE=azz][https://wiki.ubuntu.com/forum/installation/Partitioning](https://wiki.ubuntu.com/forum/installation/Partitioning)

Yes, you can shrink a partition and dual boot.  It is much simpler to just use the installer to do all your partitioning.

The Breezy installer will default to offering to create some free space for you, rather that you having to do it by hand, as detailed in the link above.[/QUOTE]


Thanks Azz,

Howevever, i don't have Breezy yet. I'm waiting for the final release. Also i was wondering whether i coult use Qparted to shave some off my existing installation.

It looks like not,

do please let me know otherwise if that is the case,

many thanks

--
sophtpaw

---

### Post by sophtpaw on 2005-09-13
[QUOTE=aysiu]That's a good point, actually. Almost every Linux distro you try out (to dual-boot with Ubuntu) will probably come with its own partitioner during the install process. I'd personally recommend downloading the first disk of Mandriva just for DiskDrake. I haven't found a better free partitioning tool.

[http://doc.mandrivalinux.com/MandrivaLinux/101/en/Starter.html/diskdrake.html#id2576559](http://doc.mandrivalinux.com/MandrivaLinux/101/en/Starter.html/diskdrake.html#id2576559)

You can always use the "install" process just for DiskDrake and then install another distro instead of Mandriva.[/QUOTE]

Yes, i thought a separate partition had to be already created to be able to install anyother distro. Which is why i was looking at using qparted to create the space

Are you saying, however, i can just install another distro without destroying ubuntu and using the partitioner shave some off ubuntu when i get to that part of the install?

anticipating your response. I have a post about this from some time back. I tried it and eventually just went for the complete reinstall (destroying in the process the previous installation) due to things not looking right, which i wouldn't want to have to do again

many thanks,

--
sophtpaw

---

### Post by aysiu on 2005-09-13
[QUOTE=sophtpaw]
Are you saying, however, i can just install another distro without destroying ubuntu and using the partitioner shave some off ubuntu when i get to that part of the install?[/QUOTE] Yes. You can't actually install the other distro without resizing the Ubuntu partition, but the new distro should have a partitioner included with it (I know Mepis, Blag, Mandriva, and SuSE have this).

I can't stress enough, though, how important it is to back up your data. Most of the time, things will run smoothly, but there is the odd chance that the partitioning tool corrupts some of your Ubuntu partition (even if it's a 1 in 100 chance).

---

### Post by sophtpaw on 2005-09-14
[QUOTE=aysiu]Yes. You can't actually install the other distro without resizing the Ubuntu partition, but the new distro should have a partitioner included with it (I know Mepis, Blag, Mandriva, and SuSE have this).

I can't stress enough, though, how important it is to back up your data. Most of the time, things will run smoothly, but there is the odd chance that the partitioning tool corrupts some of your Ubuntu partition (even if it's a 1 in 100 chance).[/QUOTE]

Well, i have SuSE and tried but got confused so aborted mission.

Back in Ubuntu and trying with qTParted. Why though does it not allow me to resize. it does for extended and swap partitions. and what is extended for? I htought it was root and swap only

Have a look:

---

### Post by aysiu on 2005-09-14
You can't use QTParted on partitions that are mounted, and if you're using it from your already-installed Ubuntu partition, the Ubuntu partition will be mounted (otherwise, you wouldn't be able to use it). You'll need to use QTParted from a live CD--try Knoppix.

Does anyone know if Ubuntu's live CD has a partitioning tool in it?

---

### Post by sophtpaw on 2005-09-14
[QUOTE=aysiu]You can't use QTParted on partitions that are mounted, and if you're using it from your already-installed Ubuntu partition, the Ubuntu partition will be mounted (otherwise, you wouldn't be able to use it). You'll need to use QTParted from a live CD--try Knoppix.

Does anyone know if Ubuntu's live CD has a partitioning tool in it?[/QUOTE]

Oh...I'm getting the picture. Well, i'm getting Linux Magazine through the door next month Next issue comes with Knoppix 4, so, looks like i'll wait. 

As, i said tried using SuSE's partitioner. It was looking like i was resizing hda1 but it was looking that of the now two created partitions it was picking the one that had the ubuntu install rather than what was shaved off to format. And that is a big no, no right now.

thanks again,

--
sophtpaw

---

### Post by aysiu on 2005-09-14
[QUOTE=sophtpaw]
As, i said tried using SuSE's partitioner. It was looking like i was resizing hda1 but it was looking that of the now two created partitions it was picking the one that had the ubuntu install rather than what was shaved off to format.[/QUOTE] Oh, yeah. That's right. I remember the last time I tried installing SuSE, it wouldn't let me choose a particular partition to reformat because it wasn't the last partition in the table. It's weird like that.

---

