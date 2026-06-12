---
title: "Hard drive access on XServe G5 LAMP - help :-)"
date: 2008-06-08
forum: Apple Hardware Users
---

### Post by kokoroexchange on 2008-06-08
Hello,

I've had 7.04 running on a XServe G5 for about a year and a half now and just ran into a little hitch today.

Actually it's probably not a hitch, just my lack of knowledge.

I added a new hard drive via one of the two open slots on my G5 XServe and can't figure out now how to access the drive...?

I'm no pro by any means but can manage to navigate around with the CLI fairly well but I don't have a very good working knowledge of the Ubuntu structure outside of the web server where I spend most of my time.

I also have webmin installed and use it from time to time as well.

Anyway, can anyone help me with some advice on how to gain access to the drive I have installed?

Jason

P.S. I've been searching and experimenting (with the Ubuntu Linux toolbox book in one had and my command line interface in the other :-) ) and see that at /etc/fstab I can see my drive that I have attached but the mount point is "none".  I'm not sure if it needs to be ext3 (the same as the drive I'm running the webserver on) or what?  Guess I'll keep reading and hope for help here from the forums too :-)

P.P.S. I have to stop editing this post and just wait for help....  I guess my P.S. addition was wrong.  That is apparently the swap, not the drive that I've added.  hdparm only shows my old drive.... Is there some other way I should be searching for this drive....?  Ah, I'm lost.

---

### Post by frog_pilot on 2008-06-08
first you have to check if the drive is recognized by the system

# sudo fdisk -l

figure out which device file is associated to the drive

e.g. /dev/sdc

Did you already create a volume on the drive? which filesystem did you use. If you didnt already created one, use parted (frontend gparted) do do so. ext3 would the best for your config, as you use linux as the only filesystem on the machine.

Once you figured out which device file the new drive is related to and managed to create a volume on it, you have to create a mountpoint for it in media

# sudo mkdir /media/storage

add a new line for it to your /etc/fstab like

```
/dev/sdc /media/storage ext3 defaults 0 2
```

now the drive will mount on startup...

---

### Post by kokoroexchange on 2008-06-08
Thanks frog_pilot,

I guess I'm in trouble because the system doesn't seem to even be recognizing the disk at all.

sudo fdisk -l

Gives me /dev/sda1 through /dev/sda4 but the size of those 4 devices does not match the size of the drive I've added.  The drive I added is a 500Gig drive.  The 4 that show up are 31.5k, 977k, 224.2Gig (my main drive), and 9.5Gig (it says Linux swap)

Nothing that resembles my 500gig drive.  Hmmm...what to do now?

Jason

---

### Post by frog_pilot on 2008-06-08
could you please copy and past the whole output of```
sudo fdisk -l
```

---

### Post by kokoroexchange on 2008-06-08
frog_pilot,

Thanks, I can't really copy/paste but I'll transfer the contents to my laptop I'm using now.

/dev/sda
        #     type   name       length     base  (size)   system
/dev/sda1  Apple_partition_map  Apple   63 @ 1  (31.5k)  Partition map

/dev/sda2  Apple_Bootstrap untitled  1954 @ 64  (977.0k) NewWorld bootblock

/dev/sda3  Apple_UNIX_SVR2 untitled  470283204 @ 2018 (224.2G) Linux native

/dev/sda4  Apple_UNIX_SVR2 swap   19949530 @ 470285222 (9.5G) Linux swap

That's it.  Thanks again for your help.

Jason

---

### Post by kokoroexchange on 2008-06-09
Hello?

If anyone can point me in the right direction here I'd be most appreciative :-)

How do I get Ubuntu to recognize a drive that I've added to my server?  The drive is spinning and connected correctly etc. but I don't see it using fdisk....

Jason

---

### Post by stream303 on 2008-06-09
You may have to manually edit your /etc/fstab to make sure that the UUID is correct for the new drive.  Run

```
sudo blkid
```

to see them, and also
```
sudo mac-fdisk -l
```

I'm no expert, but this might be one thing you may have to manually edit...

---

### Post by frog_pilot on 2008-06-10
I think thats not the whole output of #fdisk -l.

If there is an empty drive connected to the system bus it will show something like

# /dev/sdc
# 2345678 blocks ........
# anything else (cant recall it right now)

without any partition list

A similiar output should appear beyond the partition list of your /dev/sda

anyway, forget about...

Start ubuntu on your xserve. Start gparted (System > Administration > Gnome Partition Editior).
In the upper right corner there is abutton which shows you the current drive. Click on it and try to choose another drive there.

It will show you your empty 500 Gig drive. Create a volume on it with the ext3 filesystem. And try to mount it as suggested above.

If there is no other drive shown in Gnome Partition Editor, it appears to be a hardware related issue.

Then check if you plugged in all connectors (data bus, power), check if the controller is working (put it at the same controller/ same cable as your sda).

Check the jumper settings at the drive (usually on macs use cs (cable select))

Then try this again.

If it wont work, take into consideration that you bought a broken drive...

Please report your progress. And stay relaxed, if I couldnt answer that fast, sometimes I cant manage to visit this site every day :KS but I willl answer at once...

---

### Post by kokoroexchange on 2008-06-10
frog_pilot,

Thanks again.  Actually I did transpose all of the output from fdisk.  There wasn't anything else.

Also, I am running Ubuntu 7.04 LAMP (no desktop environment) so I'm not sure how to get to gparted.  Actually I installed it from command line but oddly, I cannot run it after installing it.  I get the following error

'terminate called after throwing an instance of 'Glib:OptionError'
Aborted

??

I am quite thoroughly lost :-(

Jason

---

### Post by frog_pilot on 2008-06-10
Oh, I should have taken into consideration, that you are running ubuntu without gui on your server setup.

Gparted depends on a gui. Thats why you get this error. If you dont want to install gnome its no option for you. You could use parted instead from the command line. But I suggested the gui frontend, because it would provide a graphical representation of your drives and an easy possibility to create a ew volume on it. Alternatively you could run ubuntu with gnome from a live cd. There is gparted preinstalled.

But
#sudo fdisk -l
should have shown your new drive as e.g. /dev/sdb

This fact points to a more hardware related problem. Are you shure that you connected it properly? Can you test this drive on another machine?

---

### Post by stream303 on 2008-06-10
Which xserve do you have?
[http://www.everymac.com/systems/apple/xserve/index-xserve.html](http://www.everymac.com/systems/apple/xserve/index-xserve.html)

One of the things I noticed was that all these machines support multiple drives, which are even hot-pluggable, so that may be a contributing factor.  On some powermacs for example, they have multiple hd controllers on board, and this can get a bit finicky, so on xserves, this might be a bit more troublesome.

Maybe take a look at some of the powermac threads and see if there is anything in there that might help.  I think the thing to concentrate on is the UUID in your /etc/fstab and possibly moving the drive to different positions within the xserve itself etc.

Do the docs for the xserve cover additional hard drive installation notes?  Anything about having to reset a pmu/smu?

You are on some pioneering ground as there aren't too many xserve owners out here (there are a few, but they may not be running multiple hard drives).

---

### Post by kokoroexchange on 2008-06-10
frog_pilot & stream303

Thanks for your advice and help.  

I will take the drive into work with me today and test it there to make sure it is functioning properly.

As for my XServe, I have the dual 2.3ghz model (I think it was the last one before the transition to Intel processors).

Pioneering ground....yikes! :-)  Exciting but I've only been working with Linux for a little over a year so I'm still pretty green.  Not sure if I'm ready to be a pioneer :redface:

I'll try different bays later today and some other experimenting...and, of course, look on the threads more and see if I can find something helpful.

Updates to come.

Jason

---

### Post by stream303 on 2008-06-10
The drive is probably functioning properly - the trick is to convince the xserve of that fact. :)

---

### Post by kokoroexchange on 2008-06-11
Hmmm, well I haven't made much progress.  I took the drive in to work today thinking I'd hook it up to something only to find out that all our older hardware (not that old but..) on campus is IDE.  The tech guy in my department had a little device that allows you to connect an internal 3.5" drive to your computer via USB  but...yep it is only for IDE.  

So, I wasn't able to verify the integrity of the drive but it is brand new and there was no damage to the shipping package whatsoever so I'm thinking it would be pretty rare for it to be non-functional.  I can hear it spinning down when I pull it from the machine.... not that that means everything but :-)

There is, of course, no entry in fstab for my drive but I don't even know what the UUID is so I couldn't create one anyway.  Not exactly sure how to get the system to recognize it either...?

And here's something even more interesting...my current setup has my main drive (the one with Ubuntu, my webserver (Apache), MySQL etc. on it) is in the leftmost drive bay.  I tried my new drive in the center drive bay and the drive sled light comes on and the drive spins.  When I put the sled with the drive in it in the rightmost bay, I get nothing.  No light...nothing.  And the engagement is very tight.  So tight that the second time I tried the sled in it I almost couldn't get it out.

I have made a custom 'rack' that may be in a bit of a bind so I guess it's possible that the case is a little warped on that side but I don't understand why the light wouldn't even come on...?

Anyway, maybe that's not even related.

The sled with the 500G drive is in the center bay now, the light is on but I can't find it anywhere from the console.  Can I enter the 'setup' (bios like environment) at startup and possibly access the drive then?

I'd rather not have to shut down the server as it's hosting a site that approximate 1500 students are using (Oops) and I don't have a backup server at the moment but if that is what is necessary I'm sure they'll live without their Moodle for a little while :-)

Jason

P.S. I did try a restart with the drive in the machine but nothing changed.

P.P.S. I tried parted but there is apparently no tool/function from within parted to scan the currently connected devices so there isn't much I can do from within it....or at least that's how it appears.

---

### Post by stream303 on 2008-06-11
You know, it may just be easier to put that drive in an external firewire / usb case and deal with it that way.  I'd be surprised if the xserve didn't have it.

I think in the long run, that would get you up and running much faster.

---

### Post by frog_pilot on 2008-06-11
If sudo fdisk -l wont show your drive it is presumably a hardware issue. UUIDs are distinctive designations which identify your drives mor reliable as the old block device paths as (/dev/sda). But if there is no drive recognized you dont need to think about writing uuids to your fstab...

With Mactracker I found out that your Model is Xserve G5 January 2005 (Machine ID: RackMac3,1)

Hard Drive Bus: 3 - 1.5 Gbps Serial ATA (SATA)
ADM Compatibility: 74 (10,000 RPM), 80, 250, 400, and 500 GB

ADM means Apple Drive Module (Is this the carrier for the drive, which you can plug into your machine???) [I found at apple docs somthing about ADM Compatibility]("http://support.apple.com/kb/HT1219") but I cant understand what it means because Ive never seen an Xserve :)
If you bought a 500 GB Drive with 10,000 RPM maybe it wont work because it spins too fast?

Ive read on forums about harddrive issues with Xserve G5 (maybe not exactly your model), that you have to switch your jumper setting on the drive to "SATAI" (means: sata one) or to 1,5 GBps bus speed.

[And I found this anouncement about exactly your model]("http://www.computerbase.de/news/hardware/komplettsysteme/apple/2005/januar/apple_23_ghz_xserve_g5/"):
> Der Xserve G5 unterstützt bis zu acht Gigabyte 400 MHz schnellen Arbeitsspeicher mit ECC, drei 400 GB Serial ATA-Festplatten und damit insgesamt 1,2 TB Festplattenspeicher...
translation: The Xserve G5 supports up to eight Gigabyte 400 MHz fast RAM with EEC, three 400 GB Serial ATA-harddrives and therfore altogether 1,2 TB harddisk space...

But I think this doesnt mean 500 GB drives are not supported. First of all I woulld check if the bus speed is the problem. Try to switch to 1,5GBps or SATA 1 mode...

//edit:
[On wikipedia I found the following]("http://en.wikipedia.org/wiki/Xserve"):
> On January 3, 2005, Apple speed bumped the Xserve G5 with 2.3 GHz PowerPC 970 processors in the dual-processor configurations. 400 GB hard disks were made available for up to 1.2 TB of internal storage. The slot-loading optical drive was upgraded to a combination DVD-ROM/CD-RW standard, DVD-/+RW optional.
Recently, Apple updated the Xserve and Xserve RAID to allow the use of 500 GB Hard Drives.
I think the second main question is: Is your machine really supporting 500 GB drives?

---

### Post by kokoroexchange on 2008-06-11
frog_pilot,

Wow, thanks for all the information.  I was assured by the vendor of the drive (Other World Computing) that the drive was compatible but they may have been wrong.

I will look into that some more and see if it is simply an issue of drive size.

Also, I thought that the eSATA drives did not have/require jumper settings.  Looking into this a little found the following from the Hitachi web site (the drive I bought is a Hitachi drive):
> 
Hitachi Serial ATA (SATA) hard disk drives do not have jumpers. Since SATA allows just one drive per port, SATA models do not require jumper addressing and will operate without them.

I don't even see any place where jumper settings could be adjusted on the drive.  The only 'connection' that is unused is the legacy power supply but that isn't needed when using the SATA power connector.

Also, the firewire option isn't really the best workaround for me as I was hoping for the optimal speeds allowed by the sata interface.  Plus, I bought the drive sled for the XServe which wasn't cheap so I feel compelled to use it :-)

Jason

Edit - I've been reading here and there on the web and have found quite a few people ([example]("http://lists.apple.com/archives/Macos-x-server/2007/Oct/msg00078.html")) that are successfully running drives as large as 750Gig in the XServe G5 so I don't think the drive size is my issue.  The limit quoted by Apple is, I think, a software limitation with the OSX server software and some of the drive monitoring features.

---

### Post by kokoroexchange on 2008-06-13
Making a little progress here...very little but...

I ran dmesg to see if I could find any confirmation that the system is 'seeing' the drive and got several lines starting with ata1.00 for my main drive and then the same series of lines with ata2.00 with the model number for the drive I've added.  Seems like a good sign! :-)

I noticed however, that the last line for the ata1.00 series of lines says  "configured for UDMA/100"

and the last line for my new drive ata2.00 says configured for UDMA/133

Could this 'configuration' difference be a problem?

Jason

P.S. Later in the long list that I get when typing dmesg I see

ata2: soft resetting port
ata2: SATA link down (SStatus 4 SControl 300)
ata2: failed to recover some devices, retrying in 5 secs
ata2: hard resetting port
ata2: SATA link down (SStatus 4 SControl 300)
ata2.00: limiting speed to UDMA/133:P103
ata2.00: disabled

That doesn't look go to me....?

P.P.S. One last edit here.  While looking at one of the config files in my boot directory (config-2.6.20-15-powerpc64-smp) I saw several places that looked like 'hotplugability' might be deactivated for sata drives....

---

### Post by kokoroexchange on 2008-06-14
I'm kind of having a conversation with myself here but... :-)

I managed to get the system to apparently recognize and configure the drive that I have connected.  I had taken the drive in and out of the bay several times and started to suspect that although it is supposed to be hotswappable, my system was not setup to allow for such activity.

So, I put the drive in the bay and restarted the system (twice actually) and now in the output generated from dmesg I see that the drive was recognized and configured as ata2.00  

Also, when I go to /dev  I can see sdb

But when I run fdisk -l  (as sudo) I get only my sda device.  Strangely however, if I run fdisk -l (as my login user - not root) I get an error for both sda and sdb...?

And....when I run lsmod, I see that two sata_svw devices are identifed.  Under the "used by" column for those two devices I see (ata_generic and sata_svw) 

Feel like I'm making baby steps in the right direction but not quite there yet.  How do I mount the drive if I can see it?

Jason

P.S. One last edit to this post.   sudo hdparm /dev/sdb gives me the following

IO_Support = 0 (default 16-bit)
readonly   = 0 (off)
readahead  = 256 (on)
geometry   = 60801/255/63, sectors = 976773168, start = 0

and for sda

IO_Support = 0 (default 16-bit)
readonly   = 0 (off)
readahead  = 256 (on)
geometry   = 30515/255/63, sectors = 490234752, start = 0

---

### Post by kokoroexchange on 2008-06-15
Yeah! :-) I am almost there :biggrin:

I figured out that my problem was that the drive had never been initialized/formatted etc.

So, I initialized/formatted the disk with *fdisk*

Then used *parted* to make a Native Linux partition

Then used *mkfs.ext* to create the file system on the partition

Up to that point everything worked perfectly :-)

I can now get the UUID by using *vol_id*

I thought I'd try mounting the disk manually (glad I did) before editing fstab.  I mounted it manually and must have picked the wrong mount point....

I typed

*sudo mount /dev/sdb2 /var*

and it appeared to mount...but when I accessed the /var directory everything that used to be there was gone and all I could see was lost+found

And, of course, my site located at /var/www  was gone!!  Ooops...I hope there weren't any students working on the site.

I guess I told it to mount at /var and thus blocked the contents of /var  ??

I don't know but after doing so I couldn't execute any commands and kept getting an error something like "couldn't mkdir" with a path.  I didn't write down the error and quickly did a 'brute force' shutdown (hold on the power button) :-) & restarted.  Everything is fine now and I'm glad I didn't write any changes to fstab yet....whew!

Anyway, I'm almost there.

Jason

---

### Post by kokoroexchange on 2008-06-15
SUCCESS!!  

This will be the last post of me talking to myself :-) as I have finally manged to get my 500Gig drive working in my G5 XServe!!

From my previous post, I tried mounting the drive again but first made a directory in /var like this

sudo mkdir /var/mynewdirectory

and then mounted my new drive (sdb2) at/in that directory like

sudo mount /dev/sdb2 /var/mynewdirectory

Then, for anyone familiar with Moodle, copied my datadirectory to the new directory and changed my config.php file to point to the new directory.

So, now students and teachers have plenty of space to upload files etc. 

Whew!!  What a process.  Now I just have to make the changes in fstab so that the next time I restart (which is rare) I can avoid having to remount.  I don't restart much so by the time another restart comes around I will have forgotten that I didn't add the mount info to fstab and wonder why things aren't working.

Jason

P.S. So, I don't know if I am a pioneer :-), but I now have two SATA drives running successfully under Ubuntu 7.04 on an Apple G5 XServe (dual 2.3Mhz)!

---

### Post by stream303 on 2008-06-15
> **kokoroexchange said:**
> P.S. So, I don't know if I am a pioneer :-), but I now have two SATA drives running successfully under Ubuntu 7.04 on an Apple G5 XServe (dual 2.3Mhz)!

Yes you are, congratulations!  It would be great to get a summary like what slot you ended up putting the new drive in, and the output of your /etc/yaboot.conf, and /etc/fstab, and even the final output of fdisk -l

Way to go!

btw, I forgot if you are running the server-edition of Ubuntu, or if this is all under a desktop-edition, and if you are running any sort of gui, your /etc/X11/xorg.conf would be nice in this case..

---

### Post by kokoroexchange on 2008-06-17
Stream303,

Thanks :-)

Here are the details:

My current configuration ended up with my original drive in the leftmost bay (I think Apple's specs call this #0) and the new 500Gig drive in the center bay (Apple's #1).  I don't seem to have any response whatsoever from the rightmost bay.  Not sure if that is a hardware or software related issue yet.

As for the configuration files, I don't have a gui, desktop etc. on my server but I was able to copy the files over to my laptop via a network hard drive I have connected in my LAN.

Hmm...I don't know exactly what yaboot.conf is supposed to look like but I don't see the drive here....?  Odd?

[I]boot=/dev/sda2
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"[/I]

And this is the fstab

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cf28979a-a89a-49ac-a10a-a898ddf0c9a3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=d17df1ed-35f1-4d77-8f37-50c56d2bdf43 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0[/I]

But I am guilty of having not yet added the line for the new drive.  It will look like this:

UUID=45082dfa-c321-4b14-adbb-f05c6f90c248 /var/mdl500   ext3   defaults,errors=remount-ro 0

I may change the errors setting if I have problems later but will leave it the same as my system drive for now.  

And, fdisk now gives me the following:

/dev/sda
# type name length base (size) system
/dev/sda1 Apple_partition_map Apple 63 @ 1 (31.5k) Partition map

/dev/sda2 Apple_Bootstrap untitled 1954 @ 64 (977.0k) NewWorld bootblock

/dev/sda3 Apple_UNIX_SVR2 untitled 470283204 @ 2018 (224.2G) Linux native

/dev/sda4 Apple_UNIX_SVR2 swap 19949530 @ 470285222 (9.5G) Linux swap

Block size=512, Number of Blocks=490234752
DeviceType=0X0, DeviceId=0X0

/dev/sdb
# type name  length base (size) system
/dev/sdb1 Apple_partition_map Apple 63 @ 1 (31.5K) Partition map
/dev/sdb2 Apple_UNIX_SVR2 2 878906187 @ 64 (419.1G) Linux native
/dev/sdb3 Apple_Free Extra 97866917 (46.7G) Free space

Block size=512, Number of blocks=976773168
DeviceType=0X0, DeviceId=0X0

Everything seems to be functioning smoothly.  Actually I feel like my web app has sped up a little but I'm not sure.  Also, I know I left a little unused free space on the drive (46.7G).  I made a mistake when using parted but now have an idea for a different use for that so I may create another partition using that space and use it elsewhere.

Hope this may be of some help to someone.  And, please, if I have done something glaringly wrong here and just haven't noticed it yet, please let me know. :-)

Jason

---

### Post by stream303 on 2008-06-17
Again, GREAT feedback!  This will surely help out any other xserve owners.  Since everything seems to work, **it might be best to leave it as is,** although I can't resist the temptation to comment. :)

Your yaboot.conf file for the yaboot boot-loader looks fine.  I don't know what the splash-screen on a server-install looks like, but I'd be tempted to see the boot messages scroll on by instead by changing the append= line to:

```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	**append="nosplash"**

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	**append="nosplash"**
```

and then making the system aware of it with:

```
sudo ybin -v -C  /etc/yaboot.conf
```


> And this is the fstab

Looks fine.  Since you are running Pre-Hardy, another option you can use is to try the "noatime" parameter if you don't require time-stamps being written on every file that is accessed read-only!  It seems to help speed up older drives, and not sure if it would provide a very noticeable increase on your modern system.  And, from a server standpoint, you may have software that depends on these timestamps, so just something for the notebook. :)

[http://ubuntuforums.org/showthread.php?t=692318](http://ubuntuforums.org/showthread.php?t=692318)

> And, fdisk now gives me the following:
.
.
/dev/sda4 Apple_UNIX_SVR2 swap 19949530 @ 470285222 (9.5G) Linux swap

Yikes!  You must have something like 4gb or more of ram intalled in that machine, since the swap is so huge.  The standard calculations tend to be a bit too generous (1 -2.5 times ram) when you have a lot to begin with, so if you need to reclaim some space, you could knock this down to 1x ram to be safe, and increase your system partition.

> Everything seems to be functioning smoothly.

Which is probably a big reason not to go futzing with my suggestions. :)  You're happy, and your users are happy and that's what counts.  I'd hate to see you incur the wrath of the users when you take one of my suggestions and find the server down.

Thanks again for the great report.  It was almost like being there.

---

