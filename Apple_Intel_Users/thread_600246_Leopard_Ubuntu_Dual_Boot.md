---
title: "Leopard Ubuntu Dual Boot?"
date: 2007-11-02
forum: Apple Intel Users
---

### Post by digyourownhol3 on 2007-11-02
Hi all,
My first post.
Today i will be getting my MBP with leopard pre-installed. Since it is a clean install, no personal data on it yet, i want to install ubuntu right away as a dual boot.

I have googled and looked around on this site, but i could not find any guides on how to do this. Can people point me to some tutorials?

much appreciated!

---

### Post by alephsmith on 2007-11-02
[https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa)
If the revenant wiki page.

You will need to use bootcamp to shrink your OSX Volume, put in your Ubuntu CD and reboot. Hold down 'c' to boot into the installer.

---

### Post by digyourownhol3 on 2007-11-02
thanks. Now we wait for the UPS guy..

---

### Post by digyourownhol3 on 2007-11-02
oh, wait. What is best, installing 32 or 64 bit ubuntu?

---

### Post by cyberdork33 on 2007-11-02
> **digyourownhol3 said:**
> oh, wait. What is best, installing 32 or 64 bit ubuntu?
Go for the 64bit. There is a lack of certain applications in 64bit Linux, but Gutsy handles running these with the proper 32 bit libraries very well. (Flash, Java)

---

### Post by digyourownhol3 on 2007-11-05
okay so bootcamp expired. So EFI boot menu GUI: rEFIt ( [http://refit.sf.net](http://refit.sf.net)) seems to be an alternative since i want a dualboot Tiger/Ubuntu.
However, in a week i will upgrade to Leopard, Will leopard jeopardize the EFI boot menu (in other words wil it kill it)

---

### Post by cyberdork33 on 2007-11-05
> **digyourownhol3 said:**
> okay so bootcamp expired. So EFI boot menu GUI: rEFIt ( [http://refit.sf.net](http://refit.sf.net)) seems to be an alternative since i want a dualboot Tiger/Ubuntu.
However, in a week i will upgrade to Leopard, Will leopard jeopardize the EFI boot menu (in other words wil it kill it)

Bootcamp and rEFIt are not nearly the same thing. rEFIt is just a GUI for the EFI bootloader, Bootcamp is a GUI for the partitioner and a driver cd.

Installing Leopard will break rEFIt, but you just have to reinstall it after installing Leopard.

PS turning your clock back makes Bootcamp usable again.

---

### Post by digyourownhol3 on 2007-11-05
thanks.... however since i have to install a repartitioner too i'll have to wait till i have leopard in. (dont want to spend mone on repartition software and dont wat to use illegal either)

thanks for the info though

---

### Post by cyberdork33 on 2007-11-05
> **digyourownhol3 said:**
> thanks.... however since i have to install a repartitioner too i'll have to wait till i have leopard in. (dont want to spend mone on repartition software and dont wat to use illegal either)

thanks for the info though
[parted magic]("http://partedmagic.com/") and [gparted]("http://gparted-livecd.tuxfamily.org/") can shrink your Mac OSX partition. gParted is on the Ubuntu Live CD too.

---

### Post by digyourownhol3 on 2007-11-05
can they repartition without hurting my data?

---

### Post by cyberdork33 on 2007-11-05
> **digyourownhol3 said:**
> can they repartition without hurting my data?
Yes,

I just realized that you will have leopard. There is no need then. Leopard comes with Boot Camp. and it's disk utility makes it easy to 'add' a partition to the current hard drive.

---

### Post by digyourownhol3 on 2007-11-06
Dear people,
Just for my understanding, this is the procedure for dualboot?

1 - Use bootcamp in Leopard to make space (a partition) on my HD for Ubuntu.
2 – Reboot the MBP holding ‘c’
3 - Install Ubuntu
4 – After installing Ubuntu I need to tweak Ubuntu for the MBP with the following: [https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa))

--Will this enable the dualboot option?

OR

1 - Use bootcamp in Leopard to make space (a partition) on my HD for Ubuntu.
2 – Start bootcamp and use it too install Ubuntu in stead of Windows
3 - Install Ubuntu
4 – After installing Ubuntu I need to tweak Ubuntu for the MBP with the following: [https://wiki.ubuntu.com/MacBookPro/SantaRosa](https://wiki.ubuntu.com/MacBookPro/SantaRosa))

---

### Post by cyberdork33 on 2007-11-06
First one. You can't really 'install' anything with bootcamp. It only partitions the hard drive and creates a windows driver cd.

after booting the Ubuntu CD, you will choose 'Manual' partitioning. Delete the Windows partition, then use the free space to install ubuntu.

---

### Post by digyourownhol3 on 2007-11-06
okay, i installed Ubunt (after giving it 11 gigs of space. Made a 1gig swap, and a 10 gig ext3, mount point \)

it installed. it rebooted after install. However the MBP boots into osx. Holding down the 'c' makes it go into osx too.

how do i go from here?

---

### Post by cyberdork33 on 2007-11-06
> **digyourownhol3 said:**
> okay, i installed Ubunt (after giving it 11 gigs of space. Made a 1gig swap, and a 10 gig ext3, mount point \)

it installed. it rebooted after install. However the MBP boots into osx. Holding down the 'c' makes it go into osx too.

how do i go from here?

c is used only to boot a cd

hold alt to see bootable devices.

you should install rEFIt in OSX. It will give you a menu on each boot to select what to boot.

---

### Post by digyourownhol3 on 2007-11-07
Works like a charm. Thanks.

Ubuntu seems to run very smoothly on the MBP (as it should spec. wise. But i am used to an old P3, 650 Mhz, with 198Mb memory running Ubunut and later Gentoo).

I'll leave it without the bootloader menu. Like it better this way.

Many thanks for all the answers

---

### Post by LeopoldBloom on 2007-11-07
As far as I know you can resize the Mac partition without damaging your files. I've done it with diskutil VolumeResize but not gparted though.

EDIT: Whoops, didn't see the second page there. Ignore me. ;)

---

### Post by hellfried on 2007-11-08
when i am faced with the option to install ubuntu's boot loader, should i say no or yes?

update - it did not even ask me! however now when i get to the refit menu and i select ubuntu, it just says that there is no bootable device or something. am i doing something wrong?

---

### Post by cyberdork33 on 2007-11-08
> **hellfried said:**
> when i am faced with the option to install ubuntu's boot loader, should i say no or yes?

update - it did not even ask me! however now when i get to the refit menu and i select ubuntu, it just says that there is no bootable device or something. am i doing something wrong?

I would guess that grub did not install correctly for some reason. Boot the LiveCD and you can install it again manually:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

---

### Post by hellfried on 2007-11-08
since i am using rEFIT, should i install grub on the linux partition itself?

---

### Post by cleentrax on 2007-11-08
I just got a new MacBook with Leopard. I resized the partition with Boot Camp, installed rEFIt, and then booted/installed Ubuntu Studio.

I didn't need to do anything with Grub, and now rEFIt gives me booting options when I turn on my MacBook. It was all surprisingly easy.

---

### Post by cyberdork33 on 2007-11-08
> **hellfried said:**
> since i am using rEFIT, should i install grub on the linux partition itself?
It really doesn't matter unless you have windows installed as well, but yes.

---

### Post by hellfried on 2007-11-09
thanks for the input. will try it when i get home.

---

### Post by Zettt on 2007-11-09
Hi,

I got one problem with the installation. 
I can't press Enter on the (main) installation screen. 

It is the menu where i am asked to install Ubuntu, or OEM or whatever...
The funny thing is that i can press enter on the item which says to boot from the first partition on harddrive (or so) 

What's up??? :confused::confused::confused:

---

### Post by cyberdork33 on 2007-11-09
> **Zettt said:**
> Hi,

I got one problem with the installation. 
I can't press Enter on the (main) installation screen. 

It is the menu where i am asked to install Ubuntu, or OEM or whatever...
The funny thing is that i can press enter on the item which says to boot from the first partition on harddrive (or so) 

What's up??? :confused::confused::confused:

so your keyboard is working... you can move around a such, you just cannot press enter on certain items? That's new.

---

### Post by hellfried on 2007-11-09
> **cyberdork33 said:**
> I would guess that grub did not install correctly for some reason. Boot the LiveCD and you can install it again manually:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing-GRUB-natively)

did that but get the same error message. in the live cd environment when i do 'grub> find /boot/grub/stage1' in terminal i get 'root (hd0,2)'. i then do 'setup (hd0)' and finallt 'quit'.
anything wrong here?
i have also noticed something weird in boot camp assistant. when i try to run it, it says that this startup disk is not supported. what does it all mean?

---

### Post by cyberdork33 on 2007-11-09
> **hellfried said:**
> did that but get the same error message. in the live cd environment when i do 'grub> find /boot/grub/stage1' in terminal i get 'root (hd0,2)'. i then do 'setup (hd0)' and finallt 'quit'.
anything wrong here?
i have also noticed something weird in boot camp assistant. when i try to run it, it says that this startup disk is not supported. what does it all mean?

you can't use bootcamp assistant after you change the partition layout of the disk. It expects the disk to be one OSX partition, or an OSX partition + a windows partition. That is normal.

when you do the find command, it will tell you the partition that you need to set the root to. I am guessing that the root was set incorrectly for some reason.

after doing the find command, use the result to set the root before using the setup command:
```
grub> root (hd0,2) 
grub> setup (hd0)
grub> quit
```

---

### Post by hellfried on 2007-11-09
> **cyberdork33 said:**
> you can't use bootcamp assistant after you change the partition layout of the disk. It expects the disk to be one OSX partition, or an OSX partition + a windows partition. That is normal.

when you do the find command, it will tell you the partition that you need to set the root to. I am guessing that the root was set incorrectly for some reason.

after doing the find command, use the result to set the root before using the setup command:
```
grub> root (hd0,2) 
grub> setup (hd0)
grub> quit
```

i did exactly as u mentioned above but to no avail. i followed this [guide]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by cyberdork33 on 2007-11-09
> **hellfried said:**
> i did exactly as u mentioned above but to no avail. i followed this [guide]("http://ubuntuforums.org/showthread.php?t=224351").

Ok, I just want to verify.
Are you installing on the internal hard drive, not trying to boot from an external drive?

Can you post the output of:
```
 sudo parted /dev/sda print
```
and
```
sudo fdisk -l
```

---

### Post by hellfried on 2007-11-09
> **cyberdork33 said:**
> Ok, I just want to verify.
Are you installing on the internal hard drive, not trying to boot from an external drive?

Can you post the output of:
```
 sudo parted /dev/sda print
```
and
```
sudo fdisk -l
```
[B]
'sudo parted /dev/sda print'[/B]

Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI system partition  boot 
 2      210MB   309GB  309GB   hfs+         Customer                   
 3      309GB   320GB  10.7GB  ext3         Untitled                   

Information: Don't forget to update /etc/fstab, if necessary.  

**'sudo fdisk -l'**

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003516

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38914   312571223+  ee  EFI GPT

---

### Post by cyberdork33 on 2007-11-09
> **hellfried said:**
> [B]
'sudo parted /dev/sda print'[/B]

Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI system partition  boot 
 2      210MB   309GB  309GB   hfs+         Customer                   
 3      309GB   320GB  10.7GB  ext3         Untitled                   

Information: Don't forget to update /etc/fstab, if necessary.  

**'sudo fdisk -l'**

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003516

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38914   312571223+  ee  EFI GPT
Are you sure that is all on the last command? 

If so, then I think your partition tables are out of sync (for some reason).
In the refit menu there is a option in the bottom row to sync partitions. Try that.

---

### Post by Zettt on 2007-11-09
> **cyberdork33 said:**
> so your keyboard is working... you can move around a such, you just cannot press enter on certain items? That's new.
Yes exactly. 
But on the menu entry which does boot the first partition i CAN press enter...but after that nothing happens.

---

### Post by cyberdork33 on 2007-11-09
> **Zettt said:**
> Yes exactly. 
But on the menu entry which does boot the first partition i CAN press enter...but after that nothing happens.
I would verify the disc / image file first, but that is something new that I have not seen before. 

The LiveCD will have a timeout on that screen to boot the default option.

---

### Post by hellfried on 2007-11-09
> **cyberdork33 said:**
> Are you sure that is all on the last command? 

If so, then I think your partition tables are out of sync (for some reason).
In the refit menu there is a option in the bottom row to sync partitions. Try that.

i don't see that option at all. there's one to start partitioning tool which i selected. then i am asked to do some function which i cannot remember. i select 'yes' and go back to the main menu. now when i select the linux option the penguin just sits there and does nothing!

---

### Post by Zettt on 2007-11-09
> **cyberdork33 said:**
> The LiveCD will have a timeout on that screen to boot the default option.
If it could be so easy. I saw the countdown first. When pressing Enter the first time it disappears. So i thought "Well, OK. I reboot and just do nothing." 
After the counter finished...yeah...nothing happened. ;)

---

### Post by cyberdork33 on 2007-11-09
> **hellfried said:**
> i don't see that option at all. there's one to start partitioning tool which i selected. then i am asked to do some function which i cannot remember. i select 'yes' and go back to the main menu. now when i select the linux option the penguin just sits there and does nothing!

That was the one.

Boot from your Ubuntu CD and give the output of those two commands again.

Curious, how did you initially partition your drive? Whatever you used seemed not to do things correctly.

---

### Post by hellfried on 2007-11-09
> **cyberdork33 said:**
> That was the one.

Boot from your Ubuntu CD and give the output of those two commands again.

Curious, how did you initially partition your drive? Whatever you used seemed not to do things correctly.

 **sudo parted /dev/sda prin**t

Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI system partition  boot 
 2      210MB   309GB  309GB   hfs+         Customer                   
 3      309GB   320GB  10.7GB  ext3         Untitled                   

Information: Don't forget to update /etc/fstab, if necessary.      

**sudo fdisk -l**

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003516

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26       37576   301618480   af  Unknown
/dev/sda3           37592       38897    10485760   af  Unknown


i used disk utility in leopard to partition the drive.

---

### Post by Zettt on 2007-11-09
> **cyberdork33 said:**
> I would verify the disc / image file first, but that is something new that I have not seen before. 
Oh no...the file was the wrong one...argh

---

### Post by hellfried on 2007-11-09
> **hellfried said:**
> **sudo parted /dev/sda prin**t

Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI system partition  boot 
 2      210MB   309GB  309GB   hfs+         Customer                   
 3      309GB   320GB  10.7GB  ext3         Untitled                   

Information: Don't forget to update /etc/fstab, if necessary.      

**sudo fdisk -l**

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00003516

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  EFI GPT
/dev/sda2   *          26       37576   301618480   af  Unknown
/dev/sda3           37592       38897    10485760   af  Unknown


i used disk utility in leopard to partition the drive.

yes! i did it! am typing this from within ubuntu. thanks cyberdork, you're the man!:)

---

### Post by cyberdork33 on 2007-11-09
> **hellfried said:**
> yes! i did it! am typing this from within ubuntu. thanks cyberdork, you're the man!:)

What did you do? I was about to show you how to set the Ubuntu partition as bootable.

---

### Post by hellfried on 2007-11-09
> **cyberdork33 said:**
> What did you do? I was about to show you how to set the Ubuntu partition as bootable.

i just followed my previous [guide]("http://ubuntuforums.org/showthread.php?t=224351") on installing grub from a live cd. maybe you have another way of doing it. would love to know it.

---

### Post by cyberdork33 on 2007-11-09
> **hellfried said:**
> i just followed my previous [guide]("http://ubuntuforums.org/showthread.php?t=224351") on installing grub from a live cd. maybe you have another way of doing it. would love to know it.

ok. That kind of makes sense after you have synced the partitions. I was going to suggest something totally different. Glad you got it working.

---

### Post by Zettt on 2007-11-09
OK...now i got a new problem. I used the GUI installation and my Partition, intented for Linux, isn't showing up in the list.

Can anyone help again?

Thanks

---

### Post by hellfried on 2007-11-09
> **cyberdork33 said:**
> ok. That kind of makes sense after you have synced the partitions. I was going to suggest something totally different. Glad you got it working.

i know this is a bit much to ask but how do i get my leopard partition to auto mount and show up on my ubuntu desktop?

---

### Post by cyberdork33 on 2007-11-09
> **hellfried said:**
> i know this is a bit much to ask but how do i get my leopard partition to auto mount and show up on my ubuntu desktop?

I would actually not recommend that you do that just to avoid having something happen. You can mount it on-the-fly by opening "Computer" and then double-clicking the appropriate partition. 

There are some hurdles accessing HFS+ partitions anyway. If you still want it to automount, you will have to add an entry to your /etc/fstab.

[http://ubuntuforums.org/showthread.php?t=478881](http://ubuntuforums.org/showthread.php?t=478881)
[http://ubuntuforums.org/showthread.php?t=489278](http://ubuntuforums.org/showthread.php?t=489278)
[http://ubuntuforums.org/showthread.php?t=509432](http://ubuntuforums.org/showthread.php?t=509432)
[http://ubuntuforums.org/showthread.php?t=554179](http://ubuntuforums.org/showthread.php?t=554179)
[http://ubuntuforums.org/showthread.php?t=406504](http://ubuntuforums.org/showthread.php?t=406504)

---

### Post by hellfried on 2007-11-09
> **cyberdork33 said:**
> I would actually not recommend that you do that just to avoid having something happen. You can mount it on-the-fly by opening "Computer" and then double-clicking the appropriate partition. 

There are some hurdles accessing HFS+ partitions anyway. If you still want it to automount, you will have to add an entry to your /etc/fstab.

[http://ubuntuforums.org/showthread.php?t=478881](http://ubuntuforums.org/showthread.php?t=478881)
[http://ubuntuforums.org/showthread.php?t=489278](http://ubuntuforums.org/showthread.php?t=489278)
[http://ubuntuforums.org/showthread.php?t=509432](http://ubuntuforums.org/showthread.php?t=509432)
[http://ubuntuforums.org/showthread.php?t=554179](http://ubuntuforums.org/showthread.php?t=554179)
[http://ubuntuforums.org/showthread.php?t=406504](http://ubuntuforums.org/showthread.php?t=406504)

thanks for the advice. am just curious about the alternate way that u have to make my linux partition bootable that u mentioned earlier.
on a separate matter, i have to say that ubuntu looks butt-ugly on my imac!

---

### Post by cleentrax on 2007-11-09
> **hellfried said:**
> thanks for the advice. am just curious about the alternate way that u have to make my linux partition bootable that u mentioned earlier.
on a separate matter, i have to say that ubuntu looks butt-ugly on my imac!

Ubuntu Studio looks great on my MacBook. I just wish I could get it working. No luck with sound, wifi or touchpad customization.

---

### Post by cyberdork33 on 2007-11-09
> **hellfried said:**
> thanks for the advice. am just curious about the alternate way that u have to make my linux partition bootable that u mentioned earlier.
on a separate matter, i have to say that ubuntu looks butt-ugly on my imac!

On legacy systems, you have to mark partitions as 'bootable' in order to actually boot from them. This can be done in any partitioner. It is not necessary though apparently.

You can make it look however you want.
This is the moomex theme on my current desktop.
[http://gnome-look.org](http://gnome-look.org)

---

### Post by rfdparker2002 on 2007-11-10
Today I was following the instructions from the Ubuntu Wiki for the MacBook to install Ubuntu (64bit) on a friend's MacBook, however, at 5%, when creating the root partition it stops, and then throws up, the mac partition was shrunk using Leopard's Boot Camp 2, and the windows partition deleted in place for the new root partition. In the past the machine has had Ubuntu (32bit) install fine with BootCamp beta on tiger (but was later wiped).

Does anyone have any ideas?

btw, the running gparted from the live cd, also has trouble creating partitions, but not deleting them

---

### Post by hellfried on 2007-11-10
> **cyberdork33 said:**
> On legacy systems, you have to mark partitions as 'bootable' in order to actually boot from them. This can be done in any partitioner. It is not necessary though apparently.

You can make it look however you want.
This is the moomex theme on my current desktop.
[http://gnome-look.org](http://gnome-look.org)

i have yet to dress up my gibbon but i noticed that the fonts are all blurry and generally the graphics just looks washed out. i have not activated the graphics driver for compiz.
anyways the reason that i absolutely must have ubuntu around is because so i can use deluge for torrents. my isp throttles torrent traffic and thats the only client that gives me full speed. until there is a proper mac version of deluge i will have to switch between os'es.

---

### Post by cyberdork33 on 2007-11-10
> **hellfried said:**
> i have yet to dress up my gibbon but i noticed that the fonts are all blurry and generally the graphics just looks washed out. i have not activated the graphics driver for compiz.
anyways the reason that i absolutely must have ubuntu around is because so i can use deluge for torrents. my isp throttles torrent traffic and thats the only client that gives me full speed. until there is a proper mac version of deluge i will have to switch between os'es.

Get those drivers, they will make things look better.

You can change how fonts are rendered in System > Preferences > Appearance

You can also use your Mac color profile in Ubuntu:
[http://ubuntuforums.org/showthread.php?t=491138](http://ubuntuforums.org/showthread.php?t=491138)

---

### Post by sabamanga on 2008-05-26
Ahh :s
How do I boot to Ubuntu?
I've got all I need, rEFIt and all that business, and that works, I can see both the Macintosh HD and the Linux Penguin Dude HD at the boot menu..
But when I try to boot, it says something about how it's not able, and I need to insert a Boot Disk, and press any key.
"Boot Disk" is a bit vague.. So I just put in the Ubuntu 8.02 disk and nothing happens when I press the keys.
So I hold down the power button to restart, and from the Boot Menu I get Macintosh HD, Linux HD, and Ubuntu install disk...
But I still can't boot into Ubuntu.
Am I doing something wrong..? :S
It's 2 in the morning over here, so I'm pretty gnarked. I install it on my sisters old PC this afternoon and it worked fine... More than fine actually.. Better than the previous Windows XP...
Any ideas..?
:/

---

### Post by cyberdork33 on 2008-05-26
Known issue... Please go to the new Apple users' forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

Your specific issue is addressed here:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by sabamanga on 2008-05-27
Thanks :)
I got that working.
Now I'm just having a hell of a lot of fun trying to install the drivers :|
The first one I need to do before I go anywhere is the wireless card. But to install the drivers for that the internet is required, for me to type in
sudo apt-get <whatever the driver package is>
My ethernet isn't diagnosing anything when I plug it in.. All the addresses are set to 0.0.0.0; not very useful.
I think it'd be pretty much straight forward once the wireless is sorted... 
Does anyone know how do install them properly?
I'm a complete Linux n00b :S

EDIT: I found a bunch of useful stuff here.. That's where I got the driver URLs from... I've been navigating around for ages and it seems to be fruitless :( 
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

---

### Post by cyberdork33 on 2008-05-27
> **sabamanga said:**
> Thanks :)
I got that working.
Now I'm just having a hell of a lot of fun trying to install the drivers :|
The first one I need to do before I go anywhere is the wireless card. But to install the drivers for that the internet is required, for me to type in
sudo apt-get <whatever the driver package is>
My ethernet isn't diagnosing anything when I plug it in.. All the addresses are set to 0.0.0.0; not very useful.
I think it'd be pretty much straight forward once the wireless is sorted... 
Does anyone know how do install them properly?
I'm a complete Linux n00b :S

EDIT: I found a bunch of useful stuff here.. That's where I got the driver URLs from... I've been navigating around for ages and it seems to be fruitless :( 
[https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688](https://help.ubuntu.com/community/MacBook#head-e4a1f2cde8ad66bc01c97bfdadc85996ad80f688)

IDK why your ethernet is not working.... you can edit your sources.list file to add the Ubuntu cdrom and install several packages from there. Then you can download the source on another machine, and transfer it to your Mac somehow. 

You will get a lot more help from people if you post in the newer forum instead of replying to this thread. This is in the archive section now.

---

### Post by sabamanga on 2008-05-28
Alright, thanks for the help anywho :)

I'm still wondering how on Earth I can start a new threat in this forum :S

---

### Post by cyberdork33 on 2008-05-28
> **sabamanga said:**
> I'm still wondering how on Earth I can start a new threat in this forum :S
You didn't... you replied to an existing thread.

---

