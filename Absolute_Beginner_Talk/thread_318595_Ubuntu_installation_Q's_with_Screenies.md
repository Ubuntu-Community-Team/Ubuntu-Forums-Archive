---
title: "Ubuntu installation Q's with Screenies"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by gingerj on 2006-12-14
Hi all I've just prepared my Hard Drive in windows using partition magic, when I created my two partitions one for linux and the other for the swap, I tried to use the ext format but it wouldn't let me so I created two FAT32 partitions are they OK to install Ubuntu on? 

I'm now using the Live CD, and during the partition sections of the Ubuntu installation the two new partitions have like "!" by them is that really bad?

I've pressed the forward button and it's taken me to this screen.

[http://img215.imageshack.us/my.php?image=screenshotpq4.png](http://img215.imageshack.us/my.php?image=screenshotpq4.png)

HDA5/6 are my Ubuntu ones, but the previous one's need to be kept how they were before I ran the installation as they're the partitions with my Windows XP / recovery drive (it's an Acer Laptop they've got partitions with random stuff used to recover the laptop).

If I check the HDA 5/6 to reformat;  to clean them just incase, and press forward with the other partitions left unchecked will they go unnoticed? 

Also does the installation process detect my windows xp partion and boot record, and sort out the dual booting itself? So that when I turn the laptop on I get the choice of what O/S to use and if I don't do anything it just boots into windows itself? (I had Red Hat 6 installed many many years ago by someone and they installed Lilo which did just that, does the setup do this for me also?).

Oh one more thing once I install Ubuntu does anyone have any tips on getting it to look great as right now in the Live CD it looks awful especially the fonts.

[http://img246.imageshack.us/my.php?image=screenshot1do8.png](http://img246.imageshack.us/my.php?image=screenshot1do8.png)

Can this issue be fixed or am I just unlucky and this is how all Ubuntu font's are rendered?

Hopefully this post makes sense,
many thanks! :D

---

### Post by peterj on 2006-12-14
Beryl is really nice 'eye candy' you can find instructions to download it in the ubuntu guide. this link is for ATI graphics cards, if you use nvidia scroll to the top and you'll find the link

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29")

I'd rather someone else advised you on the partitioning but it's straight forard you shouldn't mount anything to your windows partitions; reformatting the partitions you will use for ubuntu will make them ext3 which is what you want. Mount / and /media but as I said, someone else can give you the details!

---

### Post by bodhi.zazen on 2006-12-14
> **gingerj said:**
> Hi all I've just prepared my Hard Drive in windows using partition magic, when I created my two partitions one for linux and the other for the swap, I tried to use the ext format but it wouldn't let me so I created two FAT32 partitions are they OK to install Ubuntu on? 

I'm now using the Live CD, and during the partition sections of the Ubuntu installation the two new partitions have like "!" by them is that really bad?

HDA5/6 are my Ubuntu ones, but the previous one's need to be kept how they were before I ran the installation as they're the partitions with my Windows XP / recovery drive (it's an Acer Laptop they've got partitions with random stuff used to recover the laptop).

Go ahead and format the Linux partitions (use the check box).

As you say leave the other partitions unchecked (do not format). You may want to have no mount point for these partitions in which case you will have no access to them in Ubuntu after the install, although they can be added later. If you are not sure keep the defaults.....

> If I check the HDA 5/6 to reformat;  to clean them just incase, and press forward with the other partitions left unchecked will they go unnoticed? 

HDA 5/6 will be formatted, the others will not, they will be mounted.

> Also does the installation process detect my windows xp partion and boot record, and sort out the dual booting itself? So that when I turn the laptop on I get the choice of what O/S to use and if I don't do anything it just boots into windows itself? (I had Red Hat 6 installed many many years ago by someone and they installed Lilo which did just that, does the setup do this for me also?).

Yes. Ubuntu uses GRUB and it will sort itself out....

> Oh one more thing once I install Ubuntu does anyone have any tips on getting it to look great as right now in the Live CD it looks awful especially the fonts. Can this issue be fixed or am I just unlucky and this is how all Ubuntu font's are rendered?

That is a matter of opinion. I like the default install just fine. 

As with any OS there are a large number of customizations you can do post-install including fixing your font issue, changing backgrounds, etc.

Search the forums for such things, ask if you have questions.

---

### Post by rich.bradshaw on 2006-12-14
FAT32 isn't ok for Linux to be installed on - it's normally better to use Windows to make Windows partitions, and Linux to make Linux partitions, if you get what I mean.

In the Ubuntu partition manager, look at what letters (hda2 etc) correspond to the partitions you want Ubuntu and the Swap to be installed to, then just choose those in the screen you took a pic of. Ubunut will probably reformat them to ext2 instead of Fat32 automatically for you.

---

### Post by rich.bradshaw on 2006-12-14
Oh, and you probably only need at max 512Mb for swap - 3GB is way too much!

---

### Post by gingerj on 2006-12-14
Cheers everyone for all your help, just to confirm before I go complete this bit:

1) That partition Screen I sent, basically check the two linux partitions to be reformatted,
2) The windows ones keep blank for the checkbox bit,
3) For now set no mount points for those drives that have something to do with windows, I.E everyone one but hda5/6.
4) FAT32 aint cool to install Ubuntu on but checking those reformat bits for HDA5/6 will hopefully change the partition type,
5, 'GRUB' will sort out my boot issues during installation,

Cheers everyone again!

---

### Post by bodhi.zazen on 2006-12-14
That 's it. 

rich.bradshaw has a great point about swap, 1 Gb max size ...

---

### Post by gingerj on 2006-12-14
i read u needed double ur ram is there such a thing as 2 much swap space?

Also when trying to go forward from the screen where you set what partition to do what I've set the two linux ones and left the windows ones blank but I get an error message saying:

No Mount point selected for Partition 1 Disc, IDE/ATA 1 Primary HDA1

Where do I tell it to mount as it's got nothing to do with Linux, I checked the official Ubuntu book and it fire's a blank :(

---

### Post by Carlos Santiago on 2006-12-14
1) Leave the mountpoints of your windows partitions (namely /media/hda2 and /media/had3) as they are on the screenshot. This way you will have immediately access to them from Ubuntu.
2) However you could remove the mountpoint for /media/hda1, if it is the recovery partition. You should not need to have access to it.
3) Dont worry, if you dont check the format box, they will not be touched.
4) Check the format box ONLY for '/' and 'swap'
5) Format '/' as EXT3, NOT as FAT32.
6) Format 'swap' with the 'swap' specific filesystem.
7) The setup will take care of the boot selection for you. On boot you will be presented with a menu. The default will be the last used system.
8) I agree that 3GB of swap is too much, but you can leave it as is. It doesnt arm your system, is just a wast of space.

---

### Post by dbd on 2006-12-14
I don't think there is any need to have more than a gig. I don't think you can have "too much", but if you have lots of RAM anyway then there is little need for a large swap partition, you'd just be wasting hard disk space.

It is asking you to set a mount point so that when you are in linux you can read the data in that partition, and possibly write to that partition too. It's worth mounting it somewhere like /media/win_c (assuming it is your windows C partition), but is is not necessary if you don't want to access your windows partition when in Linux. You could always mount sometime after installing if you changed your mind,

---

### Post by bodhi.zazen on 2006-12-14
> **gingerj said:**
> i read u needed double ur ram is there such a thing as 2 much swap space?

Yes, RAM X 2 is outdated and carries over from days of lower RAM. It is unlikely you will need more the 521 Kb, 1 Gb Max.

[http://www.linux.com/guides/sag/swap-allocation.shtml](http://www.linux.com/guides/sag/swap-allocation.shtml)

[http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)


> Also when trying to go forward from the screen where you set what partition to do what I've set the two linux ones and left the windows ones blank but I get an error message saying:

No Mount point selected for Partition 1 Disc, IDE/ATA 1 Primary HDA1

Where do I tell it to mount as it's got nothing to do with Linux, I checked the official Ubuntu book and it fire's a blank :(

You can ignore this error message. As a result your windows partitions will not be accessible after the install. They can be added later if you would like...

---

### Post by gingerj on 2006-12-14
Many thanks to everyone who helped me on this thread, I've now using Firefox on my freshly installed Ubuntu :p 

Many thanks again!

---

