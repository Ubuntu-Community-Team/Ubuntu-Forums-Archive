---
title: "Dualboot XP + Ubuntu problem"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Canadaboy on 2007-08-22
Hello I have made a partition using Partition Magic in Windows XP and I ahve made 2 NTFS partitions. ~150 GB for windows and ~100 GB free left for Ubuntu.

When I try to install Ubuntu with live CD, I go into maual and it wont let me resize the 100 GB partition into a swap.

Am I doing something wrong ?

---

### Post by Hobo Joe on 2007-08-22
Use GParted for partitioning, it's on the liveCD.

---

### Post by Jimmyfj on 2007-08-22
100 GB swap file ? That's a lot - If you have 2 GB RAM in your computer you only need 4 GB swap space. Just let the installer do the partitioning. But before you install Ubuntu you must remember to defrag your Windows partition. And then let the installer make the EXT3 partitions you need.

---

### Post by Canadaboy on 2007-08-22
I alrdy separated my HD into two disks in XP, drive C and I

---

### Post by Monoxide on 2007-08-22
> **Canadaboy said:**
> Hello I have made a partition using Partition Magic in Windows XP and I ahve made 2 NTFS partitions. ~150 GB for windows and ~100 GB free left for Ubuntu.

When I try to install Ubuntu with live CD, I go into maual and it wont let me resize the 100 GB partition into a swap.

Am I doing something wrong ?


Note: 
> 
I ahve made 2 NTFS partitions


That could be a problem to start. one NTSF, one EXT3, one swap (approx double your ram size)

---

### Post by Canadaboy on 2007-08-22
wat should I do about my 2 partitions!

O ya and thx gusy for teh quick responses, I am rly surprised!

---

### Post by A$h X on 2007-08-22
You made TWO NTFS partitions? Surely you only need one for windows. Then rest of the space should be unpartitioned. BTW I used partiton magic and I had no problems. 
After installing windows (I made a 10gb partition for XP using the in-built tool when you install), 
I used partition magic to make a 10gb ext3 partiton for ubuntu, a 1gb swap partition, and a 95gb FAT32 partition to use as shared space for XP and ubuntu. No problems there, everything worked fine. But you can use Gparted live cd as stated. Both work equally well.

EDIT: Beaten to the punch by Monoxide!

---

### Post by Canadaboy on 2007-08-22
> **Monoxide said:**
> Note: 


That could be a problem to start. one NTSF, one EXT3, one swap (approx double your ram size)

I thought I could make one partion to keep windows  on, and then install Linux on the second partition (100GB)

---

### Post by Monoxide on 2007-08-22
A$S why did you create the fat32 when you could have just install the ntsf drivers in ubuntu then installed the ext3 drivers in windows

---

### Post by Canadaboy on 2007-08-22
> **A$h X said:**
> You made TWO NTFS partitions? Surely you only need one for windows. Then rest of the space should be unpartitioned. BTW I used partiton magic and I had no problems. 
After installing windows (I made a 10gb partition for XP using the in-built tool when you install), 
I used partition magic to make a 10gb ext3 partiton for ubuntu, a 1gb swap partition, and a 95gb FAT32 partition to use as shared space for XP and ubuntu. No problems there, everything worked fine. But you can use Gparted live cd as stated. Both work equally well.

EDIT: Beaten to the punch by Monoxide!

so I should change the second NTSF to EXT3 ?

---

### Post by Monoxide on 2007-08-22
canada boy, you have to create your one NTSF for your windows, then creat an ETX3 Partition for your Linux install and tell it to mount that as the root partition in gparted for install, then  make a swap partition about double the size of your ram

---

### Post by Canadaboy on 2007-08-22
This is what it looks like in manual:

[IMG]http://img329.imageshack.us/img329/3733/screenshotoi8.png[/IMG]

---

### Post by Canadaboy on 2007-08-22
> **Monoxide said:**
> canada boy, you have to create your one NTSF for your windows, then creat an ETX3 Partition for your Linux install and tell it to mount that as the root partition in gparted for install, then  make a swap partition about double the size of your ram

Yes i can change the NTSF into a ETX3 but...

how do I mount that as the root partition in gparted for install

 then  make a swap partition about double the size of your ram

I am confused because this is manual

---

### Post by mrfelker on 2007-08-22
> **Canadaboy said:**
> Hello I have made a partition using Partition Magic in Windows XP and I ahve made 2 NTFS partitions. ~150 GB for windows and ~100 GB free left for Ubuntu.

When I try to install Ubuntu with live CD, I go into maual and it wont let me resize the 100 GB partition into a swap.

Am I doing something wrong ?

You certainly don't need a 100GB swap file!  People differ on how large a swap file should be.
Since I have 8GB of memory I don't use any.  Mulitasks just fine.  Other people recommed 1.5 times the size of memory - not HD.  Use PM to create a small swap file and another partition for Ubuntu

---

### Post by amneziac on 2007-08-22
he never meant a 100gb swap file, what he meant is that he wants to adjust the size of his ntfs partition in order to make a swap partition but when he does, he gets an error that doesnt allow him to change the size of the ntfs partition

---

### Post by Canadaboy on 2007-08-22
> **amneziac said:**
> he never meant a 100gb swap file, what he meant is that he wants to adjust the size of his ntfs partition in order to make a swap partition but when he does, he gets an error that doesnt allow him to change the size of the ntfs partition

kenan txh for all ur help and txh 2 eevyone here but i messed up that partition and cant merge it so i give up

---

### Post by Monoxide on 2007-08-22
just hold still, ill go install it on a VPC then show you how

---

### Post by Canadaboy on 2007-08-22
> **Monoxide said:**
> just hold still, ill go install it on a VPC then show you how

The problem is I created 2 partitions that I cannot undo..

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
canand boy i can fix just give me a min to rember how

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
parden my spelling
ok boot live cd
open a turminal
type 
[PHP]sudo gparted[/PHP]
then gparted opens up you should be able t figure it out

just use gparted to set up the partions how they need to be 

you will have 3 part one WINDOWS one ext3 and one swap 

i would just delete the second portion
right click on it then click delete 
then make a new ext3 partion by clicking new 
then select ext3 in the file sytem pull down menu 
and make sure to leave anuf room for the swap wich i think should be about the size of your ram but they say double 
   (personly i know my computer almost never uses the swap part but it is needed) 
then clic add

then new agin fill the rest of the space with it  dont for get to select linux-swap from the file system pull down then click add
if every thing looks good click apply 
quit gparted then start the installer when it ask how you would like to partion the drive say manual then the only thing you have to change
is the mount point on the ext3 part it will be /media/hda5 or something like that it needs to be / then you should be set contiune with install

good luck tell me how it goes

---

### Post by Canadaboy on 2007-08-22
> **<<joe>> said:**
> parden my spelling
ok boot live cd
open a turminal
type 
[PHP]sudo gparted[/PHP]
then gparted opens up you should be able t figure it out

just use gparted to set up the partions how they need to be 

you will have 3 part one WINDOWS one ext3 and one swap 

tell it to go then switch to the installer  if you dont under stand i will explan more just ask

Will this help the fact that I have 2 NTSF partitions that I cannot merge?

---

### Post by mrfelker on 2007-08-22
> **amneziac said:**
> he never meant a 100gb swap file, what he meant is that he wants to adjust the size of his ntfs partition in order to make a swap partition but when he does, he gets an error that doesnt allow him to change the size of the ntfs partition

Sorry if I misunderstood.  Actually if he has PM he could easily resize a partition -  of course he can only have 4 partition but one of them could be extended and hold as many volumes as wants.  Linux doesn't care if you give it a volume on an extended partition (or perhaps he could use a volume for his swap and another for volume for Ubuntu and keep his Windows on a primary partition.  I don't see what problem you are having resizing an NTFS partition.  Like many others say, if you don't have PM you can use gparted (comes with a bootable Knippix I think)

---

### Post by Canadaboy on 2007-08-23
I have successfully combined both partitions into one NTFS drive!

Now where do I go from here, are your steps still valid?

---

### Post by Canadaboy on 2007-08-23
I am defragging right now just like I was told

But after I do it, can I go into install and if I go into automatic and use the slider tool for creating a partition, will that delete windows or take a space of C drive to create linux?

---

### Post by Canadaboy on 2007-08-23
Ill let it defrag over night but I need to know when selecting partitonaly if u use the slider during installation will i still have XP?

---

### Post by Canadaboy on 2007-08-23
I made two NTFS partitions b4 but that was a bad idea...

So I made it back into one drive w/ windows on it. I also defragmented it.

I tried Googling this but there is so much different and confusing methods.

I have the Live CD and I would like to know how to dual boot install Ubuntu onto my NTFS drive.

(where/how should I create the partitions, unless the installation would do it for me?)

---

### Post by Hobo Joe on 2007-08-23
There is a partitioning program on the liveCD called GParted. It's located under System > Administration.

You need to make 2 partitions. 
1. The partition that the OS and all your data is located on. Size according to how much you think you'll put on Ubuntu. Format as ext3.
2. The swap partition. This needs to be about 1 or 2 GB. Format as Linux Swap.

---

### Post by steve.horsley on 2007-08-23
Use the guided partitioning to reduce the size of the NTFS Windows partition. This will leave room for the other partitions that the installer needs to create for Ubuntu. 

The other partitions will not be NTFS - one wil be ext3 and the other will be a swap partition, and both will probably be placed inside an "extended" partition. But you don't need to know these details, just choose the option to shring the Windows partition to make room.

---

### Post by Canadaboy on 2007-08-23
> **Hobo Joe said:**
> There is a partitioning program on the liveCD called GParted. It's located under System > Administration.

You need to make 2 partitions. 
1. The partition that the OS and all your data is located on. Size according to how much you think you'll put on Ubuntu. Format as ext3.
2. The swap partition. This needs to be about 1 or 2 GB. Format as Linux Swap.

So I just resize the NTFS drive. (Keep NTFS, resize it for a ext3, and another reize for a swap?)

---

### Post by Canadaboy on 2007-08-23
> **steve.horsley said:**
> Use the guided partitioning to reduce the size of the NTFS Windows partition. This will leave room for the other partitions that the installer needs to create for Ubuntu. 

The other partitions will not be NTFS - one wil be ext3 and the other will be a swap partition, and both will probably be placed inside an "extended" partition. But you don't need to know these details, just choose the option to shring the Windows partition to make room.

Sick! You mean the sliding watchamacallit?

---

### Post by Hobo Joe on 2007-08-23
> **Canadaboy said:**
> Sick! You mean the sliding watchamacallit?

Yeah, forget what I said. I had forgotten that the install has an auto-partitioner.

---

### Post by Canadaboy on 2007-08-23
I keep on getting an error in Gparted and in the auto-partiioner, it wont let me resize:

Gpart:
[IMG]http://img524.imageshack.us/img524/1525/screenshotto4.png[/IMG]

---

### Post by porcorosso on 2007-08-23
There is another possibility, though I'm not necessarily recommending it over repartitioning and doing a dual boot using GRUB --

If you take a look at [ the Wubi installer]("http://wubi-installer.org/") you'll see that there's a way for you to do an Ubuntu installation that runs on emulated partitions on your ntfs file system. It's an actual installation of Ubuntu, but running on emulated disks -- not under a virtual machine environment. The boot loader doesn't change, so you wind up using the Windows boot loader to choose between Windows and Ubuntu at boot time.

There are a couple of provisos:

1. I don't think you can use a Live CD as the Ubuntu installation source. If you're connected to the Internet in Windows when you install Wubi it will go out and grab the generic Ubuntu .iso for you. If you download that file ahead of time and put it in the same directory as the Wubi installer the Wubi will use it instead of downloading.

2. The HAL in the Ubuntu installation is somewhat "crippled", for want of a better word. No suspend or hibernate -- which you probably shouldn't do on a dual boot system anyway. But you also can't, apparently, update the HAL in the Ubuntu installation under Wubi. Or, actually, you can, but it breaks stuff like network connectivity.

Wubi is pretty good for purposes of evaluation of Ubuntu, but probably not for a permanent install -- IMO.

I just thought I'd mention it because it's something that would probably work for you under your circumstances.

---

### Post by Canadaboy on 2007-08-23
> **porcorosso said:**
> There is another possibility, though I'm not necessarily recommending it over repartitioning and doing a dual boot using GRUB --

If you take a look at [ the Wubi installer]("http://wubi-installer.org/") you'll see that there's a way for you to do an Ubuntu installation that runs on emulated partitions on your ntfs file system. It's an actual installation of Ubuntu, but running on emulated disks -- not under a virtual machine environment. The boot loader doesn't change, so you wind up using the Windows boot loader to choose between Windows and Ubuntu at boot time.

There are a couple of provisos:

1. I don't think you can use a Live CD as the Ubuntu installation source. If you're connected to the Internet in Windows when you install Wubi it will go out and grab the generic Ubuntu .iso for you. If you download that file ahead of time and put it in the same directory as the Wubi installer the Wubi will use it instead of downloading.

2. The HAL in the Ubuntu installation is somewhat "crippled", for want of a better word. No suspend or hibernate -- which you probably shouldn't do on a dual boot system anyway. But you also can't, apparently, update the HAL in the Ubuntu installation under Wubi. Or, actually, you can, but it breaks stuff like network connectivity.

Wubi is pretty good for purposes of evaluation of Ubuntu, but probably not for a permanent install -- IMO.

I just thought I'd mention it because it's something that would probably work for you under your circumstances.

Thanks alot for mentioning it but my friend already showed me a video on how to use wubiand unfortunately i am not interested in have to download Ubuntu and only being able to put it on 30GB max.

---

### Post by porcorosso on 2007-08-23
I'm sure you'll be happier in the long run with a more standard installation. Good luck!

---

### Post by sailor2001 on 2007-08-23
if you are going to dual boot.....with the live disk , click on install icon and then select "use continuous free space" the next window should then bring up a slider for that freespace...set it for size you want. Do not select e "entire disk" or however that is worded..Everything else is pretty much automatic except for setting username & password and time zone and language

---

### Post by Canadaboy on 2007-08-23
Error while partitioning:

[IMG]http://img503.imageshack.us/img503/4498/screenshot1ql1.png[/IMG]

---

### Post by steve.horsley on 2007-08-23
Did it ever suggest that you can't shrink it below a certain size? 
I think Windows normally puts some unmoveable files smack in the middle, so you usually can't shrink it to less than maybe 60% of the original partition size.

---

### Post by Canadaboy on 2007-08-23
> **steve.horsley said:**
> Did it ever suggest that you can't shrink it below a certain size? 
I think Windows normally puts some unmoveable files smack in the middle, so you usually can't shrink it to less than maybe 60% of the original partition size.

I made it 65% and I got the same error.

---

### Post by xpod on 2007-08-23
You could try downloading the gparted live cd which can sometimes  do a much better job in many cases....not all,but many:)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Canadaboy on 2007-08-23
> **xpod said:**
> You could try downloading the gparted live cd which can sometimes  do a much better job in many cases....not all,but many:)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I dont think the problem is Gparted, it is the harddrive itself because none of the installtion partition methods work.

---

### Post by louieb on 2007-08-23
Just wondering have you prepared your NTFS partition?  There some stuff you can do on the Windows side to make shrinking the partition go smooth. Things like removing unused programs, cleaning out temporary files ...  Heres a good guide:    [See the prep Win partition Section here]("http://www.linuxdevcenter.com/lpt/a/6554")

---

### Post by ashishgoel on 2007-08-26
what i think is U need to run scandisk (with automatically correct errors) and defrag in windows and then try to install.

Or what you can do is use any partitioning utility for windows and resize windows partition to a smaller one so that u free up some space (what ever u want) and don't format that free space. Then install ubuntu and when  it comes to PREPARE THE DISK - use the manual option and select the free space and automatic options.

So the bottom is - Ubuntu will not install if the disk have errors/dirty (NTFS) and Linux/ Ubuntu won't install on NTFS as it needs separate file system - like ext3 / swap ect.. (except if u decide to use Wubi) 

That should solve your problem.

---

### Post by obscur156 on 2007-08-26
First of all,make a backup before if you have valuable data.
I have used a tutorial from how to forge and it works great.
I have managed triple boot xp/feisty/gutsy with this tuto even without knowing anything with partitioning, grub or bootloader.

Follow this link
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

Posts your results so others can use it.
Good luck budy,best regards.

---

### Post by Duck2006 on 2007-08-26
When you get your system to partition ok, try

15Gb for /    root
1Gb for swap
and the rest for your home partition so if you have to reinstall at any time you don't lose all your files.

---

