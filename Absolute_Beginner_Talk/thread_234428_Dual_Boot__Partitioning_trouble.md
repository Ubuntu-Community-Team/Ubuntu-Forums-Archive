---
title: "Dual Boot / Partitioning trouble"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by elchinovi on 2006-08-11
Hi guys!
I really need your help! this may sound more like a windows problem, but I'll ask anyways, If I'm mistaken, receive my apologies!
I'm new to the Linux world and I got the bug not long ago and I've decided to install Ubuntu. I have a WD 40GB as HD. On the c: partition had XP Pro (20 gb) and 2gb swap and 18 gb ext3 for Ubuntu.
Maybe during the installation, I might have messed up the MBR, because afterwards I was not able to modify the grub to make the XP available, nor access c: in any way.
After a few tries, I decided to repartition and reformat everything, but after that I have not been able to install XP anymore... I have no problems installing and running Ubuntu, but every time that I try to install XP it gives me this "stop 0x0000007B" error after it boots up from the cd, loads all the drivers and when tries to read the HD, it hangs up and I get that error.
I've looked it up on the microsoft knowledge data-base and it says that it could be a boot virus, or a corrupted MBR. I've scanned the system from Ubuntu and I can't find anything, and I've tried all sorts of things to fix the MBR, "fdisk /mbr" included...
I'm running out of options, and I really want it to work!
To all of the "dual booters" out there, if you had something like this happen to you, let me know how you solved it. So any kind of help that I might get would be really appreciated!
I'll describe my system so you have something else to grab on to...
AMD Athlon XP +2100 (1.74 GHz)
1GB ddr ram (2x256mb + 512mb)
WD 40 gb 7.2Krpm
128mb ATI radeon 9600 se

Again, many thanks in advance!

---

### Post by neogeo on 2006-08-11
It sounds like you may have used the Ubuntu install disc to repartition and format the whole drive.
Ubuntu uses ext3 rather than NTFS or Fat32 file systems.
Xp doesn't see ext3
Did you use the disc.
I'm new myself

---

### Post by xpod on 2006-08-11
kNOWING what to do is a bit beyond me(new too)but i gather when you dual boot from one hd you have to have your xp first...i suppose you have but it`s just a thought.
Your lucky you have an xp cd to reinstall with...im one of those lucky ones with a copy in the 1386 directory as apose to A CD.

Slipstreaming it with sp2 onto a cd has eluded me so far...

mabey you should just put your xp on the first half then point your ubunto the second half once you run the live cd....it should do it all automatically should it not?

---

### Post by klytu on 2006-08-11
> **elchinovi said:**
> Hi guys!
I really need your help! this may sound more like a windows problem, but I'll ask anyways, If I'm mistaken, receive my apologies!
I'm new to the Linux world and I got the bug not long ago and I've decided to install Ubuntu. I have a WD 40GB as HD. On the c: partition had XP Pro (20 gb) and 2gb swap and 18 gb ext3 for Ubuntu.
Maybe during the installation, I might have messed up the MBR, because afterwards I was not able to modify the grub to make the XP available, nor access c: in any way.
After a few tries, I decided to repartition and reformat everything, but after that I have not been able to install XP anymore... I have no problems installing and running Ubuntu, but every time that I try to install XP it gives me this "stop 0x0000007B" error after it boots up from the cd, loads all the drivers and when tries to read the HD, it hangs up and I get that error.
I've looked it up on the microsoft knowledge data-base and it says that it could be a boot virus, or a corrupted MBR. I've scanned the system from Ubuntu and I can't find anything, and I've tried all sorts of things to fix the MBR, "fdisk /mbr" included...
I'm running out of options, and I really want it to work!
To all of the "dual booters" out there, if you had something like this happen to you, let me know how you solved it. So any kind of help that I might get would be really appreciated!
I'll describe my system so you have something else to grab on to...
AMD Athlon XP +2100 (1.74 GHz)
1GB ddr ram (2x256mb + 512mb)
WD 40 gb 7.2Krpm
128mb ATI radeon 9600 se

Again, many thanks in advance!

Unfortunately I have never experienced this exact problem, but maybe the questions below will help you somewhat.

Are you installing WinXP from an OEM disk - one that came with a computer that had WinXP preinstalled? If so, when you reformatted everything you may have destroyed the back-up partition that your OEM installation disk uses. If this is what happened you will need to obtain a retail WinXP installation disk.

If this is not the case, did you try installing WinXP first (before installing Ubuntu)? If so, did you get the same error?

---

### Post by elchinovi on 2006-08-11
It SHOULD, but it's not happening...
I've read in some threads that you can have ubuntu first and then XP...
If that was the case, I don't mind deleting everything and installing a fresh copy of both, that's why I have this pc, to  things a try...
But what kills me is not being able to install XP anywhere!
I've tried that XP cd with my laptop, and it runs with no problems... so I guess that is something wrong with the HD, but not THAT wrong, to allow me to run Ubuntu.
I'll keep trying, I'm a bit hardheaded...
](*,) 

Thanks for your comments!

---

### Post by elchinovi on 2006-08-11
My XP cd is one that a friend has given me... I guess is a copy of a retail one, but it's the same that I've always used, and  i never had a problem.
And I've tried several times to install XP, being the first or second OS in the drive, I always end up getting the same error...
I'm not new to computers, only to linux, and this is driving me crazy!
Thanks for your efforts!
=D>

---

### Post by neogeo on 2006-08-11
If the old machine has a floppy try downloading the XP Pro boot floppy file and creating the 6 boot floppy discs.
Then use them to delete the partitions and create a new one.

---

### Post by PaulFXH on 2006-08-11
Hi
You have not said in what condition is your HD right now; how many partitions? formatted as what?
It seems, however, from what you have described that you're going to have to start over.

My advice would be:
1. Create a liveCD copy of GPartEd
2. Format your HD so you have, as a minimum, a (roughly) 20GB ntfs partition for WinXP, 2GB SWAP (linux) and a third partition as ext3 of 18GB
3. Install WinXP on the 20 GB ntfs partition FIRST
4. Then install Ubuntu loading grub into the mbr.

If this doesn't work, perhaps there is a problem with your computer but nothing you have said so far confirms this.

Good luck
Paul

---

### Post by elchinovi on 2006-08-11
Neogeo: I've tried that before and it didn't work. I'll try to get a boot disk for XP pro SP2 and see if it works.
PaulFXH: that souns good, I'll try that if I get nothing with the xp disks.
About the Live GPartEd CD, I'll look for it (or is included on the Ubuntu live cd?)

As of now, my HD is partitioned as follows: 2gb swap, 18 gb ext3 with Drapper and 20 gb of free space (reserved for XP).
Unfortunatelly, I can't try nothing now because I'm at work, but tonight I'll stay up trying all this out.
Thank you guys for your help and for your patience!:mrgreen: 
I'll let you know how everything goes!

Elchinovi.

---

### Post by PaulFXH on 2006-08-11
GpartEd, which is a really great partitioner (and not just 'coz it's free), should be available in the repositories.
You can also download it from here:

> [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

In my experience, it's better to use the LiveCD version.

Paul

---

### Post by PaulFXH on 2006-08-11
Just noticed something else about your partition table; I think it might be better to have your Windows on the FIRST partition as Windows is quite "picky and choosey".
Then, you might find it best to do as follows:

1. Reformat your complete HD (i.e. wipe everything) and format as ntfs.
2. Install Windows
3. Check that Windows works
4. Resize your single partition down to 20 GB with GPartEd
5. Also with GPartEd, creat a 2GB Swap (second partition) and an 18GB ext3 partition (third partition)
6. Install linux

Good luck
Paul

---

### Post by elchinovi on 2006-08-11
Thanks for the link, Paul.
Downloading now...
I'll try it in a little while.
Thanks!

---

