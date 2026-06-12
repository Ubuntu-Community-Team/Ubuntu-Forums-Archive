---
title: "Can't boot 6.06 after install on G5"
date: 2006-06-04
forum: Apple PPC Users
---

### Post by swartzfeger on 2006-06-04
Hi all,

I've downloaded/burned and installed both Ubuntu/Kubuntu 6.06 ISO on my G5, the installs (seemingly) go well, and when it comes time to boot I've had no luck. Here are the details.

I have an extra 80GB HD in my G5, so with each install I selected to completely erase the second drive and do a clean install. The install goes well, finishes, and then says the computer will reboot into Linux. When it reboots, it actually loads OS X, so no big deal -- I restart and hold down the option key.

When I hold down the option key, I see the two separate boot/hard drives -- one with the OS X badge, the other with the Tux badge. I select the Linux drive, and it takes me to a black boot screen where I have three options: enter l to boot into Linux, C to boot from a CD, or X to boot into OS X.

Every time I select L, it simply takes me back to the boot drive select screen. This happened with both the Ubuntu install and Kubuntu install (it also happened to my first crack at Linux, SuSE, but I read SuSE's yaboot PPC implementation is messed up).

Anyway, any ideas? This is killing me not having a bootable Linux drive, because I had a blast playing with KDE during the install! (yeah, I guess even Mac bigots can have fun with other GUIs!)

I think I recall reading somewhere that the 6.06 PPC kernel had a boot bug... is this true? If so, can I download a previous kernel build, or maybe try a different PPC distro? I'm really chomping at the bit here to give Linux a whirl.

Thanks!

---

### Post by swartzfeger on 2006-06-04
I forgot to mention -- this is the original G5 dual-2.0GHz tower, 1.75GB of ram, Tiger 10.4.6, OS X on a primary drive, Linux installed on a secondary drive.

---

### Post by tidris on 2006-06-05
I also cannot boot after install and my hardware is a dual 2 GHz G5 with ATI video card. In my case  yaboot sends me into a "white screen of death" when I choose the LINUX or OSX options in the initial yaboot menu.

I tried installing from the desktop CD and the server CD with identical results.

During installation I let the installer erase the entire disk and automatically partition it. My G5 has two internal serial ATA disks and I installed ubuntu on the upper bay one (sda). 

I am able to use ubuntu 6.06 directly from the live desktop CD just fine, so I don't believe there is a problem with the LINUX kernel or the video driver. It seems to be just a fatally flawed installation process.

---

### Post by swartzfeger on 2006-06-05
[QUOTE=tidris]I also cannot boot after install and my hardware is a dual 2 GHz G5 with ATI video card. In my case  yaboot sends me into a "white screen of death" when I choose the LINUX or OSX options in the initial yaboot menu.

I tried installing from the client CD and the server CD with identical results.

During installation I let the installer erase the entire disk and automatically partition it. My G5 has two internal serial ATA disks and I installed ubuntu on the upper bay one (sda). 

I am able to use ubuntu 6.06 directly from the live client CD just fine, so I don't believe there is a problem with the LINUX kernel or the video driver. It seems to be just a fatally flawed installation process.[/QUOTE]

Here's an interesting thing I just noticed -- I booted (again) from the CD that I burned, which was created from the server ISO. At the boot screen, it identified itself as as the 'LIVE' CD (I'm 100% positive I downloaded the server image). Anyway, it appears that despite choosing 'erase disk', I'm guessing it just created a 'Live' install, which isn't bootable.

I downloaded the alternate image this morning and burned it, and when i booted from it, the system correctly recognized it as an alternate CD, and 'INSTALL' was the default option (as opposed to the server disc, where 'LIVE' was the default). I'm hoping the alternate CD does the trick this evening... crossing my fingers!

---

### Post by Plinky on 2006-06-05
I've had the same problem... I've installed at least 8 different versions of Ubuntu (Kubuntu, Edubuntu included, from Breezy on through different betas of Dapper). Setup: Dual 2 GHz G5, 1.5 GB RAM, 160 GB sda drive, 300 GB sdb drive, 300 GB is empty, and that's the drive I bought to put Linux on.  

I get a "selection loop" at startup: if I hit ctrl, I get a graphical selection screen, which has me wait for about 4-5 minutes before I can select the Linux drive as my preferred startup drive.  Once I hit "Enter", it brings me to a text-based selection screen, and asks me:
"L" to boot into Linux
"X" to boot into OSX
"C" to boot from CD-ROM

If I hit "L", it takes me back to the aforementioned graphical selection screen, only the colours of the icons are slightly messed up.  I wait another 3-4 minutes, and am finally able to select the Penguin drive.  Upon hitting "Enter" (or "Next") I get the text-based interface again.

When I select the OS X in the graphical device after I've gone through this loop several times, it gives me the white screen of death, and I have to hard-restart it every time.  This has happened to every version of Ubuntu, including the non-graphical installer versions in Breezy Badger.  

I thought this'd be a problem that would be fixed in Dapper Drake, but no such luck.  Any workarounds?

---

### Post by deadgobby on 2006-06-05
I saw this on Distrowatch
[COLOR="Red"]I reported this bug and received a polite response from the developers. While waiting for a fix, I've found a reasonable workaround. I edited file /etc/X11/xorg.conf and replaced the "ati" driver with "vesa". The vesa driver works with just about any hardware, but it's a noticeably slow driver. I no longer experience crashes, but I can forget about playing PlanetPenguin-Racer (ppracer, formerly known as TuxRacer)[/COLOR].

---

### Post by swartzfeger on 2006-06-06
[QUOTE=Plinky]I've had the same problem... I've installed at least 8 different versions of Ubuntu (Kubuntu, Edubuntu included, from Breezy on through different betas of Dapper). Setup: Dual 2 GHz G5, 1.5 GB RAM, 160 GB sda drive, 300 GB sdb drive, 300 GB is empty, and that's the drive I bought to put Linux on.  

I get a "selection loop" at startup: if I hit ctrl, I get a graphical selection screen, which has me wait for about 4-5 minutes before I can select the Linux drive as my preferred startup drive.  Once I hit "Enter", it brings me to a text-based selection screen, and asks me:
"L" to boot into Linux
"X" to boot into OSX
"C" to boot from CD-ROM

If I hit "L", it takes me back to the aforementioned graphical selection screen, only the colours of the icons are slightly messed up.  I wait another 3-4 minutes, and am finally able to select the Penguin drive.  Upon hitting "Enter" (or "Next") I get the text-based interface again.

When I select the OS X in the graphical device after I've gone through this loop several times, it gives me the white screen of death, and I have to hard-restart it every time.  This has happened to every version of Ubuntu, including the non-graphical installer versions in Breezy Badger.  

I thought this'd be a problem that would be fixed in Dapper Drake, but no such luck.  Any workarounds?[/QUOTE]

I tried re-installing via the alternate disc, but it continually hangs during the partition section.

After blowing almost 3 days on this, I've gotta say this has pretty much soured me to the whole 'Linux thing'. Every PPC install I've tried simply CAN NOT get the whole bootloader/yaboot thing right.

Ubuntu/Kubuntu was the best of the bunch, but that's not saying much -- at least I got to play with some reasonably cool (albeit very slow) stuff via Live.

To release a few official versions that simply won't install/boot properly just doesn't make sense to me. At least as far as PPC is concerned, Linux doesn't seem ready for primetime.

I'll give it a another shot once Apple releases their Conroe-based Powermac this fall.

---

### Post by warp99 on 2006-06-06
Yes there is a bug on booting with the PPC kernel:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

A fix has been committed and should be resolved very soon. The new kernel will make it's way onto the CD images. You should give ubuntu another try at that time, you won't be disappointed. 8-)

---

### Post by kellogs on 2006-06-06
I've got working dapper on a powermac G5 2.3 ghz already. First time I installed from breezy, upgraded to dapper, no probs here.

I installed with install-powerpc64-smp(or something like this, for dual processor G5) option, then I used the ubuntu installer to make the partitions for /(root) and swap, both ext3. Ubuntu installer could not create yaboot config and at the end of the day, I had to create a newworld mac boot partition(hfs+ from tiger cd and mark as newworldmac) then yaboot installer recognized every partition perfectly.

The only problem i am having is the lack of  3d acceleration(Ati does not support ppc on their drivers), so now im using open source ati drivers waiting for a fix.

hope this helps.

---

### Post by swartzfeger on 2006-06-06
[QUOTE=warp99]Yes there is a bug on booting with the PPC kernel:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

A fix has been committed and should be resolved very soon. The new kernel will make it's way onto the CD images. You should give ubuntu another try at that time, you won't be disappointed. 8-)[/QUOTE]

Thanks Warp! I think this is why I've been so frustrated with this process -- it isn't the time wasted (I don't look at it as wasted time, because I was learning something, besides I'm a wannabe geek). 

It's frustrating because the time I spent with Kubuntu it was REALLY cool! I was surprised, as a Mac user for 15 years, that I liked the GUI/user experience. It isn't as smooth (literally or figuratively) as the Mac GUI, but it isn't gag-inducing like Windows, and there's quite a few thing about the KDE I already like better than OS X. I hope the new CD comes soon. :)

---

### Post by swartzfeger on 2006-06-06
[QUOTE=kellogs]I've got working dapper on a powermac G5 2.3 ghz already. First time I installed from breezy, upgraded to dapper, no probs here.

I installed with install-powerpc64-smp(or something like this, for dual processor G5) option, then I used the ubuntu installer to make the partitions for /(root) and swap, both ext3. Ubuntu installer could not create yaboot config and at the end of the day, I had to create a newworld mac boot partition(hfs+ from tiger cd and mark as newworldmac) then yaboot installer recognized every partition perfectly.

The only problem i am having is the lack of  3d acceleration(Ati does not support ppc on their drivers), so now im using open source ati drivers waiting for a fix.

hope this helps.[/QUOTE]

Ok, this *may* do the trick... thanks for the help.

When I installed last night, I *did* notice that it was installing yaboot toward the end. I think what the issue may be in terms of booting is the ATI driver issue someone mentioned above. Maybe I can wipe the drive clean and reinstall, boot in Ubuntu in 'Live' mode, change the driver to 'VESA' in the .conf and then try rebooting.

So I understand -- there are to be 3 partitions, correct? /root, /swap, and a /newworldmac for yaboot, correct?

And when I go to install, I'm guessing it will automatically see the newworldmac partition and automatically use it for yaboot? How big does the yaboot partition need to be?

Also, does anyone know if this same showstopper bug exist in other distros, ie, should I give Gentoo a whirl?

Or, better yet, is there a way for me to download a CD ISO of a pre-Dapper build that doesn't have this bug?

---

### Post by kellogs on 2006-06-06
you will need a partition of type HFS ( in my case HFS+ didnt make any difference). I made that one with osx cd, just reboot with the osx cd on the drive, press C. and go to the disc utility, create an hfs partition. in my tigercd, it did not let me make it less than 4 mb, I dont know why. with that partition created then put the ubuntu cd on the drive and:

- in the space left, create one partition of type ext3 . (it automagically mounts to /). this is where linux file system and home is installed, you dont need a /boot, it does create into this system too automatically. and a /home partition is optional. again, I created all in /. no problem here (200gb is enough for all).

-a swap partition of about double of your memory was recommended several years ago. but now with gigs of ram available in computers... it is not recommended to create more than 1 gb of swap. in my system ive got 2.5 gb of ram, 512 mb of swap, and when I look at resource usage, in a month, my computer hasn't yet touched the swap... its always at 0.0 mb usage. maybe thats because Ive got enough ram, lol.

-when you've got this ready, you will see for your self, yaboot makes all the work.

about the drivers... well, the important part is to have the system installed and booting... later you will mess with xorg.conf for X.

hope it helps!

EDIT: forgot to Add: when youve got all that, just do a normal install of ubuntu. it will detect partitions or ask you to mark a bootable one for yaboot. just mark the one you created newworldmac, mark it as bootable and presto.

EDIT2: lol, I must say, you can do all the new partitions from within the ubuntu installer.  the only type of partitions it does not create is hfs, for that is the osx cd.

---

### Post by swartzfeger on 2006-06-06
[QUOTE=kellogs]you will need a partition of type HFS ( in my case HFS+ didnt make any difference). I made that one with osx cd, just reboot with the osx cd on the drive, press C. and go to the disc utility, create an hfs partition. in my tigercd, it did not let me make it less than 4 mb, I dont know why. with that partition created then put the ubuntu cd on the drive and:

- in the space left, create one partition of type ext3 . (it automagically mounts to /). this is where linux file system and home is installed, you dont need a /boot, it does create into this system too automatically. and a /home partition is optional. again, I created all in /. no problem here (200gb is enough for all).

-a swap partition of about double of your memory was recommended several years ago. but now with gigs of ram available in computers... it is not recommended to create more than 1 gb of swap. in my system ive got 2.5 gb of ram, 512 mb of swap, and when I look at resource usage, in a month, my computer hasn't yet touched the swap... its always at 0.0 mb usage. maybe thats because Ive got enough ram, lol.

-when you've got this ready, you will see for your self, yaboot makes all the work.

about the drivers... well, the important part is to have the system installed and booting... later you will mess with xorg.conf for X.

hope it helps!

EDIT: forgot to Add: when youve got all that, just do a normal install of ubuntu. it will detect partitions or ask you to mark a bootable one for yaboot. just mark the one you created newworldmac, mark it as bootable and presto.[/QUOTE]

Thanks so much kellogs, you're a saint! I wanna ask 1 (or a few more) dumb questions so I'm sure I'm doing this corrrectly.

1. I have an extra ATA drive in my G5 tower -- Tiger is on my primary drive, and I plan on installing Ubuntu on my second internal drive. Since I'm installing on a secondary drive, I'm guessing I don't need to boot from the Tiger CD, correct? I can just fire up Disk Utility and partition.

2. When I make the /newworldmac partition, the 4MB size is adequate for yaboot to install?

3. My disc is a Maxtor 82GB... so if my /newworldmac is 4MB, and I create a 1GB /swap, the remaining 75+GB should be adequate for the main /, correct?

4. Another dumb question -- 

/newworldmac is formatted as HFS+ under OS X
/ is formatted as /ext3

What is the /swap partition formatted as?

Or do I even need to worry about creating a separate /swap partition and just let Ubuntu handle it?

Thanks so much!

---

### Post by swartzfeger on 2006-06-06
[QUOTE=kellogs]EDIT2: lol, I must say, you can do all the new partitions from within the ubuntu installer.  the only type of partitions it does not create is hfs, for that is the osx cd.[/QUOTE]

Got ya, thanks -- I made my last post asking about the swap before you posted your 2nd edit. :)

---

### Post by kellogs on 2006-06-06
> 
1. I have an extra ATA drive in my G5 tower -- Tiger is on my primary drive, and I plan on installing Ubuntu on my second internal drive. Since I'm installing on a secondary drive, I'm guessing I don't need to boot from the Tiger CD, correct? I can just fire up Disk Utility and partition.


You will need,  because as far as I know, ubuntu installer doesn't know how to create HFS partitions. for ext3 and swap partitions those can be created in the ubuntu installer.

> 2. When I make the /newworldmac partition, the 4MB size is adequate for yaboot to install?

I think the minimum is about 875 kilobytes or so for yaboot to work correctly, in my case i could not create 1 mb only 4 as minimum, so i could not save that space :grin: . dont confuse yourself with that /newworldpartition ... is only a name for HFS mac partitions(default osx partitions).

> 3. My disc is a Maxtor 82GB... so if my /newworldmac is 4MB, and I create a 1GB /swap, the remaining 75+GB should be adequate for the main /, correct? 

yes. the first time I did it, I created two big HFS partitions with the osx installer. then I left the newworld boot(4mb) one, and deleted the remaining space for / and swap.

> 4. Another dumb question --

/newworldmac is formatted as HFS+ under OS X
/ is formatted as /ext3

What is the /swap partition formatted as?

Or do I even need to worry about creating a separate /swap partition and just let Ubuntu handle it?

swap is formatted as "swap type" xD. you will need strictly a SWAP and a "/ mounting point or root" ext3 type partitions. /boot and /home are created into "/" , that is, the base system, people usually creates boot or home partitions as backups.

well, hope  to help, sorry about my english.

---

### Post by swartzfeger on 2006-06-06
[QUOTE=kellogs]well, hope  to help, sorry about my english.[/QUOTE]

it was very helpful, kellogs, and you're English is perfect. :)

---

### Post by kellogs on 2006-06-06
you are welcome. and don't forget to remember the name of the Hd.

If you are using SCSI sata they will be named something like SDA and SDB.

I whiped out completely Macosx tiger, but that was deliberately done, no more propietary oses at home, thanks. =D> =D> =D>

---

### Post by tidris on 2006-06-06
[QUOTE=warp99]Yes there is a bug on booting with the PPC kernel:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/34508")

A fix has been committed and should be resolved very soon. The new kernel will make it's way onto the CD images. You should give ubuntu another try at that time, you won't be disappointed. 8-)[/QUOTE]

I am not so sure that bug is related to what has been reported in this thread. I see a lot G4 hardware mentioned, but no G5s. Also the symptoms listed there are very different from what has been posted here. 

Besides, If the kernel is broken for G5 hardware how come I am able to boot the 6.06 live CD just fine on my Dual G5? AFAIK the live CD uses the same kernel that gets installed in the hard disk.

I think the problem is with the yaboot program or the yaboot configuration and not with the LINUX kernel. On my Dual G5 I can't even get OSX started from the yaboot menu. Why would a problem in the LINUX kernel keep OSX from booting?

Also wanted to mention that the xorg.config used by the live CD does use the ATI driver as far as I can tell, so I don't believe the video driver has anything to do with this problem either.

---

### Post by kellogs on 2006-06-06
the first time I installed ubuntu on my Dual G5 powerpc, it was using breezy install....
the  biggest problem I found was starting the installation... using install-powerpc64-smp as installing option solved the problem, no kernel problem here, and not even in dapper.

Im using right now dapper 6.06 LTS, and it works quite well. maybe this problem of the kernel has todo with G4 specific hardware.

---

### Post by tidris on 2006-06-06
[QUOTE=kellogs]the first time I installed ubuntu on my Dual G5 powerpc, it was using breezy install....
the  biggest problem I found was starting the installation... using install-powerpc64-smp as installing option solved the problem, no kernel problem here, and not even in dapper.

Im using right now dapper 6.06 LTS, and it works quite well. maybe this problem of the kernel has todo with G4 specific hardware.[/QUOTE]

Did you install ubuntu in an internal serial ATA drive? If so, which bay, upper or lower? Do you still have OSX installed somewhere in one of the internal drives? Can you post the contents of your /etc/yaboot.conf file?

---

### Post by swartzfeger on 2006-06-06
[QUOTE=tidris]Did you install ubuntu in an internal serial ATA drive? If so, which bay, upper or lower? Do you still have OSX installed somewhere in one of the internal drives? Can you post the contents of your /etc/yaboot.conf file?[/QUOTE]

Well, as far as my install --

I'm reformatting the drive in OS X (in Disk Utility), the secondary ATA drive intend to install Kubuntu on is listed as

Device 0, "B (lower)"

---

### Post by tidris on 2006-06-07
Well, I am finally running 6.06 LTS on my dual G5.

Apparently a yaboot utility called ofpath doesn't work right when dealing with serial ATA disks, and that results in a broken yaboot installation. Fortunately there is a magic incantation one can put in the yaboot.conf file that works around that problem.

So in a nutshell, the fix consisted of modifying the yaboot.conf file and then running ybin to have yaboot reinstalled in the hard disk using the modified yaboot.conf file. If anybody is interested I can post a more detailed description of what I did.

---

### Post by swartzfeger on 2006-06-07
[QUOTE=tidris]Well, I am finally running 6.06 LTS on my dual G5.

Apparently a yaboot utility called ofpath doesn't work right when dealing with serial ATA disks, and that results in a broken yaboot installation. Fortunately there is a magic incantation one can put in the yaboot.conf file that works around that problem.

So in a nutshell, the fix consisted of modifying the yaboot.conf file and then running ybin to have yaboot reinstalled in the hard disk using the modified yaboot.conf file. If anybody is interested I can post a more detailed description of what I did.[/QUOTE]

PLEASE -- this would be GREATLY appreciated!

Also, exactly **HOW** do you boot in Ubuntu once it's succesfully installed?

Do you hold down the option key during startup and select the Linux drive, or is there another method?

---

### Post by swartzfeger on 2006-06-07
[QUOTE=tidris]Well, I am finally running 6.06 LTS on my dual G5.

Apparently a yaboot utility called ofpath doesn't work right when dealing with serial ATA disks, and that results in a broken yaboot installation. Fortunately there is a magic incantation one can put in the yaboot.conf file that works around that problem.

So in a nutshell, the fix consisted of modifying the yaboot.conf file and then running ybin to have yaboot reinstalled in the hard disk using the modified yaboot.conf file. If anybody is interested I can post a more detailed description of what I did.[/QUOTE]

Also, I'm wondering at this point if I made a big mistake using my second ATA drive... has anyone succesfully installed 6.06 on an ext. Firewire drive?

---

### Post by swartzfeger on 2006-06-07
[QUOTE=tidris]Well, I am finally running 6.06 LTS on my dual G5.

Apparently a yaboot utility called ofpath doesn't work right when dealing with serial ATA disks, and that results in a broken yaboot installation. Fortunately there is a magic incantation one can put in the yaboot.conf file that works around that problem.

So in a nutshell, the fix consisted of modifying the yaboot.conf file and then running ybin to have yaboot reinstalled in the hard disk using the modified yaboot.conf file. If anybody is interested I can post a more detailed description of what I did.[/QUOTE]

C'mon Tidris, you're keeping us in suspense. :)

I'm assuming you did something similar [mentioned here at penguinppc.org]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml")?

---

### Post by colinhayes on 2006-06-07
ppc kernel boots fine with the G5 chip.. now power management may be an issue as I posted..., go to your other post I replied to, I think your yaboot.conf is messed up.  you may need to boot the livecd, mount the root fs, chroot to it, edit yaboot.conf and run ybin.

---

### Post by tidris on 2006-06-07
[QUOTE=swartzfeger]C'mon Tidris, you're keeping us in suspense. :)

I'm assuming you did something similar [mentioned here at penguinppc.org]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml")?[/QUOTE]

My dual G5 has two internal serial ATA disks. I installed LINUX in the upper bay disk (sda) and OSX is in the lower bay disk (sdb). OSX is in partition 3 of sdb.

I booted from the live desktop CD and had it do an install on sda. I allowed the installer to erase and automatically partition sda. This created partition 2 as boot, partition 3 as root, partition 4 as swap.

After the installation completed I continued to use the live CD instead of rebooting. I opened a terminal window and used the following commands.

To mount the root partition of sda:
    sudo mount /dev/sda3  /mnt

To edit yaboot.conf in the root partition of sda:
    sudo pico /mnt/etc/yaboot.conf

After yaboot.conf was edited and saved I copied it to where ybin wants it to be:
    sudo cp /mnt/etc/yaboot.conf  /etc/yaboot.conf

To reinstall yaboot using the edited yaboot.conf:
    sudo ybin -v

After that I rebooted and I was able to boot LINUX from the hard disk.

Here is the original yaboot.conf file:

boot=/dev/sda2
device=/disk@0:
partition=3
root=/dev/sda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sdb3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"


Here is the edited file:

boot=/dev/sda2
ofboot=sd0:2
device=sd0:
partition=3
root=/dev/sda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=sd1:3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

In the edited file "sd0" is the OpenFirmware path for sda and "sd1" is the OpenFirmware path for sdb.
As for where the "sd0" and "sd1" came from, I booted the G5 into OpenFirmware and used the devalias command to see what device aliases were available.

I hope that helps!

---

### Post by swartzfeger on 2006-06-07
[QUOTE=tidris]
Here is the edited file:

boot=/dev/sda2
ofboot=sd0:2
device=sd0:
partition=3
root=/dev/sda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=sd1:3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

In the edited file "sd0" is the OpenFirmware path for sda and "sd1" is the OpenFirmware path for sdb.
As for where the "sd0" and "sd1" came from, I booted the G5 into OpenFirmware and used the devalias command to see what device aliases were available.

I hope that helps![/QUOTE]

And here's [kellogs' .conf]("http://www.ubuntuforums.org/showthread.php?t=191079") as a comparison:

boot=/dev/sda2
device=/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@0/disk@0:
partition=4
root=/dev/sda4
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
append="quiet splash"

I'm trying to figure out the differences, and which way I need to configure mine so it will properly boot.

Tidris' second line uses 'ofboot', whereas kellogs' uses the actual open firmware address... does anyone know you would use ofboot vs. the of address and vice versa?

Could it be because kellogs' wiped OS X completely from his drive? Open firmware shouldn't care whether OS X is installed, correct?

---

### Post by tidris on 2006-06-07
[QUOTE=swartzfeger]
I'm trying to figure out the differences, and which way I need to configure mine so it will properly boot.

Tidris' second line uses 'ofboot', whereas kellogs' uses the actual open firmware address... does anyone know you would use ofboot vs. the of address and vice versa?
[/QUOTE]

Ok, I see you posted a yaboot.conf file in another thread, so based on that here is what I think your edited yaboot.conf file should look like:

boot=/dev/sdc3
# sd2:3 is an OpenFirmware path alias for sdc3
# [EDIT] changed ofpath to ofboot
ofboot=sd2:3
#device=/disk@0:
# sd2: is an OpenFirmware path alias for sdc
device=sd2:
partition=5
root=/dev/sdc5
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
#macosx=/dev/sdb9
# sd1:9 is an OpenFirware path alias for sdb9
macosx=sd1:9

image=/boot/vmlinux
label=Linux
read-only
initrd=/boot/initrd.img
append="quiet splash"

image=/boot/vmlinux.old
label=old
read-only
initrd=/boot/initrd.img.old
append="quiet splash"

I am assuming your hardware has the same OpenFirmware aliases defined as my dual G5.
Remember that you need to run ybin after editing yaboot.conf in order for the changes to take effect.

---

### Post by swartzfeger on 2006-06-07
[QUOTE=tidris]Ok, I see you posted a yaboot.conf file in another thread, so based on that here is what I think your edited yaboot.conf file should look like:

boot=/dev/sdc3
# sd2:3 is an OpenFirmware path alias for sdc3
ofpath=sd2:3
#device=/disk@0:
# sd2: is an OpenFirmware path alias for sdc
device=sd2:
partition=5
root=/dev/sdc5
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
#macosx=/dev/sdb9
# sd1:9 is an OpenFirware path alias for sdb9
macosx=sd1:9

image=/boot/vmlinux
label=Linux
read-only
initrd=/boot/initrd.img
append="quiet splash"

image=/boot/vmlinux.old
label=old
read-only
initrd=/boot/initrd.img.old
append="quiet splash"

I am assuming your hardware has the same OpenFirmware aliases defined as my dual G5.
Remember that you need to run ybin after editing yaboot.conf in order for the changes to take effect.[/QUOTE]

Awesome, thanks!

Actually, my entire ubuntu install is on the lower/b drive so I changed sdc3 to sdb3, ofpath=sd2:3 to sd1:3, etc.

So I ybin -v after I followed your previous directions and got the following:

ubuntu@ubuntu:~$ sudo ybin -v
ybin: Finding OpenFirmware device path to `/dev/sdb3'...
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sdb3...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sdb3...
ybin: Installing /etc/yaboot.conf onto /dev/sdb3...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sdb3 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...

--

Looks like this may work!

---

### Post by tidris on 2006-06-08
[QUOTE=swartzfeger]Awesome, thanks!

ybin: Finding OpenFirmware device path to `/dev/sdb3'...

Looks like this may work![/QUOTE]

I don't like that line in your ybin output. It says ybin is still trying to convert a LINUX device path into an OpenFirmware path, and that is no good. When I run ybin I don't get that message. 

[EDIT] Ok, I just noticed I made a mistake in my previous message. The line that says ofpath=xxxxx should be ofboot=xxxxx instead. That would explain the ybin message above. Sorry about that!

---

### Post by swartzfeger on 2006-06-08
[QUOTE=tidris]I don't like that line in your ybin output. It says ybin is still trying to convert a LINUX device path into an OpenFirmware path, and that is no good. When I run ybin I don't get that message. 

[EDIT] Ok, I just noticed I made a mistake in my previous message. The line that says ofpath=xxxxx should be ofboot=xxxxx instead. That would explain the ybin message above. Sorry about that![/QUOTE]

got this after changing to ofboot:

ybin: /dev/sdb3: Permission denied
ybin: /dev/nvram: Permission denied
ybin: Warning: nvram will not be updated

I'm pretty much throwing in the towel at this point...

---

### Post by swartzfeger on 2006-06-08
[QUOTE=swartzfeger]got this after changing to ofboot:

ybin: /dev/sdb3: Permission denied
ybin: /dev/nvram: Permission denied
ybin: Warning: nvram will not be updated

I'm pretty much throwing in the towel at this point...[/QUOTE]

Don't know if I should've done this (doesn't matter since 6.06 is screwed anyway), but after receiving the permission denied message, I chmod sdb3 and nvram and ran ybin -v again and received this message:

ubuntu@ubuntu:~$ ybin -v
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sdb3...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sdb3...
ybin: Installing /etc/yaboot.conf onto /dev/sdb3...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sdb3 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...

---

### Post by tidris on 2006-06-08
[QUOTE=swartzfeger]Don't know if I should've done this (doesn't matter since 6.06 is screwed anyway), but after receiving the permission denied message, I chmod sdb3 and nvram and ran ybin -v again and received this message:

ubuntu@ubuntu:~$ ybin -v
ybin: Installing first stage bootstrap /usr/lib/yaboot/ofboot onto /dev/sdb3...
ybin: Installing primary bootstrap /usr/lib/yaboot/yaboot onto /dev/sdb3...
ybin: Installing /etc/yaboot.conf onto /dev/sdb3...
ybin: Setting attributes on ofboot...
ybin: Setting attributes on yaboot...
ybin: Setting attributes on yaboot.conf...
ybin: Blessing /dev/sdb3 with Holy Penguin Pee...
ybin: Updating OpenFirmware boot-device variable in nvram...[/QUOTE]
I have been using "sudo ybin -v" instead of just "ybin -v". Otherwise your ybin messages now look like the ones I get.

---

### Post by RoadTripDK on 2006-06-19
I am having a problem with Xubuntu locking up during the install log creation, so I can't get to the point where I can follow your strategy. Any ideas?

I am using the Xububtu live CD on my G5 single (PowerMac 9.1).

---

### Post by swartzfeger on 2006-06-20
[QUOTE=RoadTripDK]I am having a problem with Xubuntu locking up during the install log creation, so I can't get to the point where I can follow your strategy. Any ideas?

I am using the Xububtu live CD on my G5 single (PowerMac 9.1).[/QUOTE]

The only thing I can recommend (off the top of my head) is to try the Xubuntu alternate ISO.

---

### Post by sbeehre on 2006-06-22
Well after having all the same problems as you guys have mentioned i got ubuntu working fine on my G5 (Dual 2GHZ) 

here is the yaboot.conf i used

```
boot=/dev/sdb2
ofboot=sd1:2
device=sd1:
partition=3
root=/dev/sdb3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=sd0:3


image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

```

The only problem now that ive come accross is airport doesnt work (but its not a biggie since im using built in ethernet) and macromedia flash doesnt work! any idea if there is anything i can do about those 2 issues?

---

### Post by RoadTripDK on 2006-06-22
OK, thanks for your yaboot.conf. As I read it, you have two internal SATA drives with Ubuntu installed on drive #2, with the default Ubuntu partitioning scheme (i.e. root and swap)?

My problem is unfortunately more complicated than just the yaboot.conf file. 

When I install from the install CD (Xubuntu Dapper Drake PPC alternative CD), the install works fine with no errors. At system boot, Xubuntu runs some scripts, which seem to go without a hitch, then it complains about a 'module unknown not found', then it tries to mount /dev/sdb3 on /root (which fails with a 'no such device'), then comes a "no such file or directory' and then the system defaults into BusyBox and I get the error "/bin/sh: can't access tty: job conrol turned off".

This same scenario occurs with the Xubuntu PPC Dapper Drake  desktop (live) install version, when I boot into the system. However, with this install version, the system boots up and reaches the GTK login screen and then freezes. This may be related to similar behavior that I have seen with sound card issues on the G5 in earlier versions of Ubuntu and Fedora Core 4, but it could also be related to the above mentioned problem with install version of Xubuntu, despite the fact that I don't see the same messages (there are some error messages, but they don't seem to be fatal).

Any ideas?

---

### Post by amishman on 2006-11-13
I am finally up on Ubuntu.  Yeah!  I am glad I found this thread.  Anyway, I need to figure out how to tell what partition my OS X is on so I can adjust the yaboot file so I can also run OS X.  My main slot A on my G5 is a new 400GB that I allowed Ubuntu installer to erase and setup as needed.  My B slot has my original 160MB drive.  I have tried setting "macosx=sd1:3" but that does not work so I am guessing sd1 is not right for slot B or my partition is wrong for OS X or ??  Anyway, if I boot into OS X by doing the Option key at startup so O can select OS X, is there an OS X application that can tell me what sd1 or whatever the OS X is on?

Thanks

tj

---

### Post by bahbo on 2006-12-10
> **tidris said:**
> Well, I am finally running 6.06 LTS on my dual G5.

Apparently a yaboot utility called ofpath doesn't work right when dealing with serial ATA disks, and that results in a broken yaboot installation. Fortunately there is a magic incantation one can put in the yaboot.conf file that works around that problem.

So in a nutshell, the fix consisted of modifying the yaboot.conf file and then running ybin to have yaboot reinstalled in the hard disk using the modified yaboot.conf file. If anybody is interested I can post a more detailed description of what I did.

I sure would be interested!  I've tried everything I can think of, and still can't get yaboot recognized on my dual g5.  Thanks

---

### Post by slink44 on 2008-01-13
> **tidris said:**
> My dual G5 has two internal serial ATA disks. I installed LINUX in the upper bay disk (sda) and OSX is in the lower bay disk (sdb). OSX is in partition 3 of sdb.

I booted from the live desktop CD and had it do an install on sda. I allowed the installer to erase and automatically partition sda. This created partition 2 as boot, partition 3 as root, partition 4 as swap.

After the installation completed I continued to use the live CD instead of rebooting. I opened a terminal window and used the following commands.

To mount the root partition of sda:
    sudo mount /dev/sda3  /mnt

To edit yaboot.conf in the root partition of sda:
    sudo pico /mnt/etc/yaboot.conf

After yaboot.conf was edited and saved I copied it to where ybin wants it to be:
    sudo cp /mnt/etc/yaboot.conf  /etc/yaboot.conf

To reinstall yaboot using the edited yaboot.conf:
    sudo ybin -v

After that I rebooted and I was able to boot LINUX from the hard disk.

Here is the original yaboot.conf file:

boot=/dev/sda2
device=/disk@0:
partition=3
root=/dev/sda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/sdb3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"


Here is the edited file:

boot=/dev/sda2
ofboot=sd0:2
device=sd0:
partition=3
root=/dev/sda3
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=sd1:3

image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet splash"

In the edited file "sd0" is the OpenFirmware path for sda and "sd1" is the OpenFirmware path for sdb.
As for where the "sd0" and "sd1" came from, I booted the G5 into OpenFirmware and used the devalias command to see what device aliases were available.

I hope that helps!

thanks, i dont know if you are still in this forum, but thanks a million.  i was trying to install 7.10 on my G5(original single processor 1.6ghz) on and off all week and definitely all weekend.  when i got to your post i was able to get 90 percent done.

when i did what you said to do, i would get to the boot menu, but when i tried to boot Linux it would not work.  something about wrong device.

 i had to put in the following at the prompt that said boot:
sd0:3,/boot/vmlinux

then it would begin to boot.  but, then it would get the following error
VFS: Cannot open root device "Null" or unknown

and i would say something about root fs on unknown block(0,0)

i just had to put my "root=" down a bit lower in my yaboot.conf file.

image=/boot/vmlinux
	label=Linux
	root=/dev/sda3
	read-only
	initrd=/boot/initrd.img
	append="quiet splash"


i also put it in the "image=/boot/vmlinux.old" part, too.
after that i booted up fine.

I wish ubuntu, did a better job with this one, but i guess you cant get all the problems (bugs).

anyway, thanks again.

---

