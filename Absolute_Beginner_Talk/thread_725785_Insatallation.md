---
title: "Insatallation"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by mahela007 on 2008-03-16
hi.i finally got the ubuntu CD. 
i'm running windows Xp and have a hard disk partitioned in to two parts which are C and D.
I'm planning to install ubuntu into drive D. but there is just one program that is there on drive D which I cannon move or reinstall on drive C.

when I'm installing ubuntu on drive D is there an option that will allow me to keep that program on drive D without deleting it ?

I checked out a tutorial of installing ubuntu. 
there was an option saying" resize disk" or something like that. Will selecting this option prevent the program on drive d form being erased?

---

### Post by Oldsoldier2003 on 2008-03-16
> **mahela007 said:**
> hi.i finally got the ubuntu CD. 
i'm running windows Xp and have a hard disk partitioned in to two parts which are C and D.
I'm planning to install ubuntu into drive D. but there is just one program that is there on drive D which I cannon move or reinstall on drive C.

when I'm installing ubuntu on drive D is there an option that will allow me to keep that program on drive D without deleting it ?

I checked out a tutorial of installing ubuntu. 
there was an option saying" resize disk" or something like that. Will selecting this option prevent the program on drive d form being erased?

you will not be able to install Ubuntu on that partition and save that program. what you will need to do is defrag the "d"drive and resize (shrink) it using Gparted.  You can the istall Ubuntu in the unallocated space on the drive.

---

### Post by mahela007 on 2008-03-16
the ubuntu installation has an option called "resize". do you think it will work?

---

### Post by sandysandy on 2008-03-16
here is the link to gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

download it and burn it as isoimage on CD to get bootable CD.

then boot into it.

u can then resize the D;/ partition as suggested by Oldsoldier2003 and in the free space make two more partitions. Format the bigger partition to ext3 (for root) for ur main ubuntu installation. second partition should be SWAP which is generally twice ur RAM size.

regards

---

### Post by sandysandy on 2008-03-16
> **mahela007 said:**
> the ubuntu installation has an option called "resize". do you think it will work?

resize should work. but defragment the drive u want to resize to avoid loss of data.

here are some links to dual booting

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by gobbles414 on 2008-03-16
> **mahela007 said:**
> hi.i finally got the ubuntu CD. 
i'm running windows Xp and have a hard disk partitioned in to two parts which are C and D.
I'm planning to install ubuntu into drive D. but there is just one program that is there on drive D which I cannon move or reinstall on drive C.

when I'm installing ubuntu on drive D is there an option that will allow me to keep that program on drive D without deleting it ?

I checked out a tutorial of installing ubuntu. 
there was an option saying" resize disk" or something like that. Will selecting this option prevent the program on drive d form being erased?

Resizing is a simple way of saying that you're partitioning a hard drive that already has data on it. In my experience, the creates more problems than it solves and should be avoided at all costs. Sadly, Ubuntu and Windows use different hard drive formats. Ubuntu can read Windows hard drive formats. But Windows cannot read Ubuntu hard drive formats. So unless you want to create a third partition by resizing your D drive -- which is potentially dangerous but would allow you to keep the program -- you'll need to uninstall the software in question. But most programs today allow you to backup your data. So you should be able to safely uninstall the program from your D drive, and then reinstall it on your C drive.

You may also want to think about running Windows in a virtual machine. [VirtualBox]("http://www.virtualbox.org/") is a popular virtual machine for Ubuntu. Or, your Windows programs might run in Ubuntu by way of a program called [Wine]("http://www.winehq.org/").

Does this help?

PS: What is the name of the program you're worried about?

---

### Post by sandysandy on 2008-03-16
>  Resizing is a simple way of saying that you're partitioning a hard drive that already has data on it. In my experience, the creates more problems than it solves and should be avoided at all costs. 

i have never faced problems with it.

de-fragmenting the concerned drive is necessary prior to resizing.

regards

---

### Post by bumanie on 2008-03-16
I also have never had a problem with resizing, moving or copying partitions with gparted. Problems can occur, but they are rare. If you burnt a live gparted cd as sandysandy suggests, defrag and then see if you can remove or copy the program in question. If not, you could try to shrink your d:\ to a size that allows just enough room for your program. Gparted can copy entire partitions, therefore if d:\ were shrunk, you could copy it somewhere ie external device or make a new small logical partition (the same size as your shrunk d:\) within c:\ to accomodate the d:\ copy.

---

### Post by gobbles414 on 2008-03-16
> **sandysandy said:**
> i have never faced problems with it.

de-fragmenting the concerned drive is necessary prior to resizing.

regards

I'll admit that doing a defrag (and error check) in Windows minimizes the possibility of a resizing-related problem. I also realize that users who don't have access to a Windows operating system installation disk sometimes must use the resizing option when installing Ubuntu, because system recovery utilities seldom allow partitioning. But I stand by my original statement that resizing should be used as a last resort.

---

### Post by Oldsoldier2003 on 2008-03-16
> **bumanie said:**
> I also have never had a problem with resizing, moving or copying partitions with gparted. Problems can occur, but they are rare. If you burnt a live gparted cd as sandysandy suggests, defrag and then see if you can remove or copy the program in question. If not, you could try to shrink your d:\ to a size that allows just enough room for your program. Gparted can copy entire partitions, therefore if d:\ were shrunk, you could copy it somewhere ie external device or make a new small logical partition (the same size as your shrunk d:\) within c:\ to accomodate the d:\ copy.

Its rare but sometimes GParted can screw up a partition resize or move. No worries though, fsck to the rescue when it happens.

---

### Post by gobbles414 on 2008-03-16
> **bumanie said:**
> I also have never had a problem with resizing, moving or copying partitions with gparted. Problems can occur, but they are rare. If you burnt a live gparted cd as sandysandy suggests, defrag and then see if you can remove or copy the program in question. If not, you could try to shrink your d:\ to a size that allows just enough room for your program. Gparted can copy entire partitions, therefore if d:\ were shrunk, you could copy it somewhere ie external device or make a new small logical partition (the same size as your shrunk d:\) within c:\ to accomodate the d:\ copy.

I believe that mahela007 is likely to encounter problems with the registry in Windows if he/she tries to simply copy the program in question from the D drive to the C drive. I'm not an expert on the registry. But I know enough about the registry to know that it's very fragile.

I'm not trying to be a killjoy. But all one has to do is search these forums to learn how problematic resizing a partition can be. IMHO, it's best for one to take a few hours and configure his/her operating systems from scratch.

---

### Post by forestpixie on 2008-03-16
> I believe that mahela007 is likely to encounter problems with the registry in Windows if he/she tries to simply copy the program in question from the D drive to the C drive.
+1

If you can't reinstall the program to C:\ you will have to resize the partition - why can't it be installed to the drive?

As far as resizing problems - go it can happen, lose power halfway through and it's grrrr.. - you're dealing with partitions so make sure you've got suitbale backups and then it's at least retrievable.

---

### Post by sandysandy on 2008-03-16
here are a few links on resizing

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

regards

---

