---
title: "[SOLVED] Ubuntu 6.06.1 (Desktop Live CD i386 version) doesn't see my IDE Promise 2027"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Banacek on 2007-10-20
Okay, I just had a quick gander at the [FakeRaid]("https://help.ubuntu.com/community/FakeRaidHowto") guide. It seems like a bit of a convoluted process but I need to keep my IDE Promise RAID as it is since I'll be doing a dual boot with winBLOWS (alas, I cannot as of yet entirely ditch MS crap). How good is this guide? Is it up to date? Is it missing any relevant information?

I have a Gigabyte GA-7VAXP mainboard (Dual BIOS) with onboard IDE Promise 20276 RAID MBFastTrak133 Lite controller and it's using an AMD Athlon Thunderbird 1.8 GHz CPU with 1Gig DDR400 SDRAM. Is my RAID fakeRAID or not? The mainboard CD comes with *some* Linux drivers. would it be easier to just use one of those drivers and if so, which package do I use? (In something comparable to how with a winBLOWS 2000 or XP installation you press "F-6" at the startup screen to load any needed control drivers.) The Red Hat rhsmp-ftb20.zip, Red Hat rhup-ftb20.zip, the SUSE suse80-ftb22.zip or do I need to look elsewhere for something like Novell or FreeBSDE drivers? Is there anything I need to do to prepare these drivers? What is the process to load the drivers for an Ubuntu install?


Also, should I go ahead and spring for the Ubuntu 7 download?  I've tried Fedora 7 and it has the MBFastTrak133 Lite drivers already loaded within the install DVD. It just sees my IDE Promise RAID (without having to do any special loading of drivers) with all my partitions just the way I set them up and just installs with full support for my RAID as is but Fedora just seems to run a bit clunky or overloaded even with a minimum install. I have heard that Ubuntu runs better and I wanted to try it out.

---

### Post by jonnymongoose on 2007-10-21
I felt your pain just a couple days ago :) You need to take a little from the "fakeraid" guide and the other one you see at the bottom in the 7.04 section. Let me get all the info I gathered  rounded up and I'll make a better post. Just wanted to let you know I'll help ya

---

### Post by jonnymongoose on 2007-10-21
This whole process was a nightmare for me. Sadly No "Press F6" anywhere. It just saw my RAID as 2 drives, and the twit that I am figured that the OS would know what its doing so I let it install. That was my first dead windows install. Then I tried just using the guide [http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758) ..........that was my second dead windows install. Good thing I just bought a 500GB external drive and backed up my "saves" partition before I started all this. First of all make sure you use the "dmraid" program. Then I used the "fdisk" and the file mounting steps from the "fakeraid" guide. I just made a  / , /boot , /swap , and a /home partition. You only have to worry about the /,/boot, and /swap in the file mounting step but you can mount ext3 
to your /home if you want. I'm not sure if you need help with this or "fdisk" , but just ask if you need help with fdisk. We are now on the 2nd guide.  Once everything is mounted use the install from the CD(remember to use manual setup in the disk section). Follow the instructions from the guide.Then follow the instruction for Grub set up. I'm not gonna lie to ya and say you wont have a problem, but after 3 trys I got it up and running. Post here if you run into any trouble.

---

### Post by Banacek on 2007-10-21
Ai yi yi! I was hoping I could just get the right drivers worked into the installation or something. That whole fakeRAID guide just seemed rather complex. Does my RAID fall under that fakeRAID category? Well, jonnyMl, thank you.

---

### Post by Banacek on 2007-10-30
I have been thinking about just going into the mainboard BIOS and turning off the RAID to have the IDE Promise 20276 run as ATA133. Then I could do a fresh install of Ubuntu using software RAID to the entirety of both HDDs. A dual boot isn't the only way to run winBLOWS applications when you have Linux.

For the past week or so I have been seeing to finishing up torrent downloads and making sure everything I want to keep is saved onto DVDs. So, I'm about ready to do something; I just have to choose what to do and how to go about it.


The option of dedicating all available space of both HDDs to Ubuntu installed as software RAID, but using VMware or other virtual machine to install winBLOWS onto a disk image for running winBLOWS applications or perhaps just use an emulator such as Cedega for running winBLOWS games, is looking more and more acttractive.


Another option to consider is to install Slackware instead of Ubuntu. What are the pros and cons of each one? Is one better than the other? If so, why?


What threads are there having to do with installing and using VMware and avoiding problems or fixing them? Links, please. :) Also, the same for Cedega would be nice.

---

### Post by Banacek on 2007-10-31
Perhaps I should rephrase that as I'm sure there are plenty of VMware threads. Which threads are the best with the most useful information and/or the best resolutions? Your best recommendations, please.

---

### Post by macogw on 2007-10-31
Have you tried using a version of Ubuntu that isn't over a year old?  Newer versions have better hardware support.

---

### Post by Banacek on 2007-10-31
Yeah, I went ahead and downloaded the Ubuntu 7.10 i386 ISO already. It doesn't see Promise 20276 RAID either.


Anyways, now, In my considerations, I'm leaning towards disabling my RAID or running it as ATA133 and using software RAID in a Ubuntu install instead as well as using VMware for installing winBLOWS into a disk image.

---

### Post by JairunCaloth on 2007-10-31
I have on-board nvidia fake raid on my system, and was able to install into it.

Here are the steps I took.

1. Boot into live cd.

2. install dmraid 
> sudo apt-get install dmraid

3. Then I followed the fakeraid guide all the way **through** mounting the temporary file structure section.

4. Where it says install base system, I simply used the ubuntu installer on the live CD. When you get to the partitioner, you need to use manual partitioning and make sure you tell it what partitions you want to use for swap, root, boot, ect.....

Very important here that you make sure it's using the raid partitions and not the individual HDD partitions.

5. Configure Grub ala the fakeraid guide.

6. Boot into my Nvidia Fakeriad system :)

---

### Post by Banacek on 2007-11-16
Okay, I've finally decided to go with Ubuntu after all. At least for now. I still want to give Slackware a go but not for now; so, it's Ubuntu till that day finally arrives. I've been putting off installing Ubuntu for a few weeks now as I was a bit shy about dealing with that fakeRAID BS. Before I started, of course, I realized with Ubuntu LiveCD that eth(0) would be functional and I could have internet access available before the install was even finished. That's a real plus as I can let you all know where I am at as I go along.

That fakeRAID guide is mostly for Feisty Fawn but at the very end of it the guy says he's also made a guide for an Ubuntu 7.10 installation with RAID(0). It seems that Gusty does a good deal more of the work for you on the RAID than the Festy does. However, the Grub isn't fully done regarding RAID so it still has to be done manually.

So, I've been using the guide for [installing Ubuntu 7.10 on RAID(0)]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation"). I used fdisk to set up my partitions and the following layout results.
```
Command (m for help): p

Disk /dev/mapper/pdc_iighbfdg: 122.9 GB, 122985512960 bytes
255 heads, 63 sectors/track, 14952 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1fdd1fdd

                   Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_iighbfdg1               1          13      104391   83  Linux
/dev/mapper/pdc_iighbfdg2              14         209     1574370   83  Linux
/dev/mapper/pdc_iighbfdg3             210         471     2104515   82  Linux swap / Solaris
/dev/mapper/pdc_iighbfdg4             472       14952   116318632+   5  Extended
/dev/mapper/pdc_iighbfdg5             472        1907    11534638+  83  Linux
/dev/mapper/pdc_iighbfdg6            1908        2691     6297448+  83  Linux
/dev/mapper/pdc_iighbfdg7            2692       14756    96912081   83  Linux
/dev/mapper/pdc_iighbfdg8           14757       14952     1574338+  83  Linux

Command (m for help): w

```



I began the install and prepared to begin gparted. Nevermind the SCSI3 as it's just a USB memory stick (256 MB) for saving
extraneous files generated as I go along that I might want to keep (screenshots and copying the terminal session).

[IMG]http://i4.tinypic.com/82kynvm.png[/IMG]



The default is for guided using the entire disk. I chose manual instead. 

[IMG]http://i17.tinypic.com/8aa35e8.png[/IMG]


My partitions are shown repetitiously in gparted. The first series should be set for disuse.

[IMG]http://i6.tinypic.com/6yppwsy.jpg[/IMG]


Choose "Use as: dontuse" for the first two available choices.

[IMG]http://i5.tinypic.com/85krvwi.png[/IMG]


Make sure to set "dontuse" on the false swap as well. The entries in the
"Type" and "Mount point" columns are blanked for selections put to disuse.

[IMG]http://i4.tinypic.com/6xg47lc.png[/IMG]


Continue the same with the remaining four until the first _**available**_ numbered partition is reached.
Here I select the boot and root partitions to be mounted and "formatted" by gparted.

[IMG]http://i14.tinypic.com/6lv2h4w.png[/IMG]



The mount points for the remaining partitions are selected for gparted to do. Finito gparted.

[IMG]http://i16.tinypic.com/6p02pgg.png[/IMG]



Finally, installation is ready to begin. As foretold, the installation completes up to 95% and then halts as Grub has failed. I begin to manually install Grub as per instructions.

```
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/mapper/pdc_iighbfdg2 /target
mount: /dev/mapper/pdc_iighbfdg2 already mounted or /target busy
mount: according to mtab, /dev/mapper/pdc_iighbfdg2 is already mounted on /target
ubuntu@ubuntu:~$ sudo mount --bind /dev /target/dev
ubuntu@ubuntu:~$ sudo mount -t proc proc /target/proc
mount: proc already mounted or /target/proc busy
mount: according to mtab, /proc is already mounted on /target/proc
ubuntu@ubuntu:~$ sudo mount -t sysfs sysfs /target/sys
ubuntu@ubuntu:~$ sudo cp /etc/apt/sources.list /target/etc/apt
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /target/etc
ubuntu@ubuntu:~$ sudo chroot /target
root@ubuntu:/# sudo apt-get update
```


```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com gutsy Release.gpg [191B]  
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com gutsy-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Get:3 http://us.archive.ubuntu.com gutsy-security Release [51.2kB]
Hit http://us.archive.ubuntu.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Get:4 http://us.archive.ubuntu.com gutsy-security/main Packages [19.9kB]
Get:5 http://us.archive.ubuntu.com gutsy-security/restricted Packages [14B]
Get:6 http://us.archive.ubuntu.com gutsy-security/universe Packages [9744B]
Get:7 http://us.archive.ubuntu.com gutsy-security/multiverse Packages [599B]
Get:8 http://us.archive.ubuntu.com gutsy-security/main Sources [4377B]
Get:9 http://us.archive.ubuntu.com gutsy-security/restricted Sources [14B]
Get:10 http://us.archive.ubuntu.com gutsy-security/universe Sources [1863B]
Get:11 http://us.archive.ubuntu.com gutsy-security/multiverse Sources [14B]
Fetched 88.0kB in 3s (28.6kB/s)
Reading package lists... Done
```


```
root@ubuntu:/# sudo apt-get install dmraid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dmraid
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 185kB of archives.
After unpacking 627kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/universe dmraid 1.0.0.rc13-2ubuntu5 [185kB]
Fetched 185kB in 2s (67.4kB/s) 
Selecting previously deselected package dmraid.
(Reading database ... 92002 files and directories currently installed.)
Unpacking dmraid (from .../dmraid_1.0.0.rc13-2ubuntu5_i386.deb) ...
Setting up dmraid (1.0.0.rc13-2ubuntu5) ...
 * Setting up DMRAID devices...                                               [ OK ] 
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
root@ubuntu:/# sudo apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
root@ubuntu:/# cp /usr/lib/grub/i386-pc/* /boot/grub
root@ubuntu:/# grub
Probing devices to guess BIOS drives. This may take a long time.
```


```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> device (hd0) /dev/mapper/pdc_iighbfdg

grub> find /boot/grub/stage1

Error 15: File not found

grub> find /grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/grub/stage2 /grub/menu.lst"
... succeeded
Done.

grub> quit
```


```
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.22-14-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done
```




Okay, it's at this point that I suspect something is amiss. The guide seems to be written assuming the boot directory will be within the root partition rather than being a separate partition. My partitioning is done to have a separate boot partition and I have forgotten to adjust for that in reading the guide. Hence, why "stage1" is in "/grub/" but not in "/boot/grub/."

What should I do? Should I just restart the entire grub installation (manually) or do I need to undo or/and uninstall a few things first?

---

### Post by Banacek on 2007-11-16
It seems as though everything is just fine after all. I look in /boot/grub/ and, yes, /boot/grub/stage1 does exist in that exact location. The grub was just being a tad goofy in refusing to see absolute paths but only seeing relative paths.

So, after the /boot/grub/menu.lst file has been generated I look into it and see that the defaults just happen to be what I already need. Nothing is missing and I don't need to add a chain loader or anything to boot winBLOWS because I'm NOT DOING A DUAL BOOT. (Rather, I plan on using VMware for installing that crap into an image and running winBLOWS crud from it.) That's all there is to it. I'm done; so, I change nothing there, exit and reboot. The reboot is fine and I now have a fully boot-able installation of Gusty Ubuntu (yes, Gusty) up and running. Consider this baby solved. :)

---

