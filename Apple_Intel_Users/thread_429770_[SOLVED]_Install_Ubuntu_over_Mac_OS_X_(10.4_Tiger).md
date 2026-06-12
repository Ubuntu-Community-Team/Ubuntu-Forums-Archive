---
title: "[SOLVED] Install Ubuntu over Mac OS X (10.4 Tiger) - Grub"
date: 2007-05-01
forum: Apple Intel Users
---

### Post by altonbr on 2007-05-01
**What I did:**
I used qtparted to resize the HFS+ partition to allow 10GB of space for Ubuntu. I installed Ubuntu on a 9.3GB partition and a swap on a 700MB partition. 

**Problem:**
I rebooted and now OS X won't boot except for Grub and Ubuntu. Why did Grub not detect OS X and how do I get it back in the MBR? Doesn't OS X have a proprietary boot partition? I thought for sure Grub wouldn't overwrite the MBR, or the Mac wouldn't allow. But I was incorrect.

Does anyone know what I'm talking about?




FINAL RESOLUTION: [http://ubuntuforums.org/showpost.php?p=2585601&postcount=19](http://ubuntuforums.org/showpost.php?p=2585601&postcount=19)

---

### Post by ronocdh on 2007-05-01
> **altonbr said:**
> **What I did:**
I used qtparted to resize the HFS+ partition to allow 10GB of space for Ubuntu. I installed Ubuntu on a 9.3GB partition and a swap on a 700MB partition. 

**Problem:**
I rebooted and now OS X won't boot except for Grub and Ubuntu. Why did Grub not detect OS X and how do I get it back in the MBR? Doesn't OS X have a proprietary boot partition? I thought for sure Grub wouldn't overwrite the MBR, or the Mac wouldn't allow. But I was incorrect.

Does anyone know what I'm talking about?
I would try installing [rEFIt]("http://refit.sf.net") as a bootloader and see whether that detects the OS X install. You could also try booting from your OS X installer disc and running the disk utility there to repair/recover the installation. You may lose your Ubuntu installation in so doing, but I think that's a secondary concern for you at the moment.

If you treat OS X as your "most important" partition (I support this philosophy), you should partition from inside OS X; that way you can create other partitions outside of it without harming it that way. Any other method has the potential to handle the HFS+ partition destructively.

---

### Post by benanzo on 2007-05-01
I think you might just need to run gptsync which is part of the refit package.  You can do it from within Ubuntu by enabling universe and installing refit.  Then as root run ```
gptsync /dev/sda #or whatever your disk is
```  This will syncronise your MBR (what Ubuntu needs) and GPT (what OS X needs) so there is no confusion at boot time about what is installed and where.  You can also install refit into OS X so you get a menu when you boot.  But that wont help if you can't boot into OS X in order to install it.

Try running it in Ubuntu.  It's pretty non-destructive.  If it detects any weird abnormalities it will refuse to do anything.  The best case scenario is if it says something like"Would you like me to syncronize the GPT and MBR?"  say yes.

---

### Post by altonbr on 2007-05-01
So, while I'm trying your fixes, what would have been the proper way of doing this? I thought the install was just like Windows where you just need to install the proprietary OS first...

---

### Post by altonbr on 2007-05-01
**@ronocdh & @benanzo**

I ran gptsync just like you said, and it asked me if I would like to syncronize the GPT and MBR. I said yes, and it appeared to work. I rebooted, but the only options Grub has is the usual Linux kernel options.

I ran gptsync again, and this is what I received:
```
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     96238656  Linux LVM
 3       96238657    115769907  Basic Data
 4      115769908    117209361  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640     96238656  8e  Linux LVM
 3       96238657    115769907  83  Linux
 4      115769908    117209361  82  Linux swap / Solaris

Status: Tables are synchronized, no need to sync.
```


This is my /boot/grub/menu.lst *(no surprise here)*:
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d081d625-e2e5-4685-965a-fc73c634f34e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d081d625-e2e5-4685-965a-fc73c634f34e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
```

---

### Post by ronocdh on 2007-05-01
GRUB doesn't really "get" EFI yet, which is why some people resort to using ELILO or an equivalent. Using rEFIt from Ubuntu is a good start, but if that doesn't work, I would try using the OS X installation DVD; at least it is designed to detect and repair HFS+ partitions. Keep it mind you may lose your Ubuntu party for now, but I think that's less important at the moment.

---

### Post by Gen2ly on 2007-05-01
```
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     96238656  Linux LVM
 3       96238657    115769907  Basic Data
 4      115769908    117209361  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640     96238656  8e  Linux LVM
 3       96238657    115769907  83  Linux
 4      115769908    117209361  82  Linux swap / Solaris

Status: Tables are synchronized, no need to sync.
```

lol, you don't have OS X installed.

---

### Post by Chrisj303 on 2007-05-02
> **altonbr said:**
> **What I did:**
I used qtparted to resize the HFS+ partition to allow 10GB of space for Ubuntu. I installed Ubuntu on a 9.3GB partition and a swap on a 700MB partition. 

**Problem:**
I rebooted and now OS X won't boot except for Grub and Ubuntu. Why did Grub not detect OS X and how do I get it back in the MBR? Doesn't OS X have a proprietary boot partition? I thought for sure Grub wouldn't overwrite the MBR, or the Mac wouldn't allow. But I was incorrect.

Does anyone know what I'm talking about?

I'm a little confused with your first statement - are you saying that you created a logical/extended partion within your mac OSX' HFS+ partition? If so then i'm sure that won't work - i'm sure that you can only boot from a primary partition.
And during the ubuntu install set-up, when you specify mount points, did you do anything other than just mount your ubuntu partition at " / " and your swap partition (which i belive to be uneeded with intel macs - a 500mb swap file is what i use).

And, as Dirk pointed out above me, youve managed to overwrite OSX. I seriously hope you backed up any data that was important, as it appears to have gone entirely.

I think the only real solution to this is a *complete* re-install (unless the message rEFIt is giving is incorrect). You haven't specified what type of Mac you are using, but this is a good one : [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

If you do reinstall, make sure you google as many guides as you can, making sure to read through them and cross-reference when needed.

good luck,
chrisj303

---

### Post by altonbr on 2007-05-02
**@Dirk.R.Gently & Chrisj303**, I never overwrote OS X:

When I run:
```
sudo mount /dev/sda2 /media/mac
```
then
```
ls /media/mac
```
it returns
```
Applications  Desktop DF  mach_kernel  System                       var
automount     dev         mach.sym     tmp                          Volumes
bin           etc         Network      User Guides And Information
cores         Library     private      Users
Desktop DB    mach        sbin         usr

```

As you can see, my Mac files are still there. The Mac partition is still readable via:
```
sudo parted
```
```
print
```
which returns
```
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags       
 1      20.5kB  210MB   210MB   fat32        EFI system partition  boot, hidden
 2      210MB   49.3GB  49.1GB  hfs+         Customer              hidden, lvm 
 3      49.3GB  59.3GB  10.0GB  ext3                                           
 4      59.3GB  60.0GB  737MB   linux-swap          
```

gtpsync was, supposedly, able to read the EFI boot partition for the Mac, but never wrote anything to /boot/grub/menu.lst. 

This didn't work, as stated here:
> **ronocdh said:**
> GRUB doesn't really "get" EFI yet, which is why some people resort to using ELILO or an equivalent...

I've already installed the gptsync package, but apparently I have to run some configuration to get it to overwrite the MBR. I'll read the documentation on how to run this program and get back to you guys soon.

---

### Post by altonbr on 2007-05-02
It says on [http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html), that I can only install it on a HFS+ partition. How can I install it via my Ubuntu partition? I don't see any documentation for it.

Here's the blurb
> **Installing on a separate volume or external disk**

If you&#8217;re uncomfortable with having rEFIt on your Mac OS X volume, you can install it on any other volume, as long as it is formatted in the HFS+ (&#8220;Mac OS Extended&#8221;) format. For example, you can install rEFIt on a USB flash drive.

The installation procedure is basically the same as explained above &#8212; copy the &#8220;efi&#8221; folder to the root of the volume, and run &#8220;enable.sh&#8221; inside the &#8220;efi/refit&#8221; directory. The path in Terminal will be different, for example &#8220;/Volumes/MyStick/efi/refit&#8221; if the volume is named &#8220;MyStick&#8221;.

If you want, you can use the provided &#8220;rEFIt.icns&#8221; icon as a volume icon. 

The is no "efi" folder anyway... Here's the installed files list:
> /.
/sbin
/sbin/gptsync
/usr
/usr/lib
/usr/lib/refit
/usr/lib/refit/refit
/usr/lib/refit/refit/refit.efi
/usr/lib/refit/tools
/usr/lib/refit/tools/gptsync.efi
/usr/share
/usr/share/doc
/usr/share/doc/refit
/usr/share/doc/refit/README.Debian
/usr/share/doc/refit/TODO.Debian
/usr/share/doc/refit/copyright
/usr/share/doc/refit/changelog.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/gptsync.8.gz

This is all the README says:
> EFI files are available in /usr/share/refit/, copy it to somewhere
accessible from MacOSX, boot into Mac OS X, 'bless' refit.efi in a EFI
or HFSplus partition in order to use it.
and /usr/share/refit/ doesn't even exist.

---

### Post by Chrisj303 on 2007-05-02
Honestly, if i was in your position i would forget about getting a working dualboot setup from this, and just concentrate on pulling out whatever you need from the HFS+ partition, then i would start from scratch.

I don't know for definite, but i really don't think it is possible to install rEFIt onto your OSX partition from ubuntu, not properly anyway.

 I have never used the Mac's install discs as a repair tool - as someone mentioned earlier this could very well save your life! 

You still haven't mentioned what type of Mac your using. If possible i would physically remove the drive and transplant it into another mac, that way you can dump anything important, then copy it back over later (when you have a functioning setup).

If thats not possible i would boot into ubuntu and use synaptic to download the HFS+ tools - to enable you to mount, read and write to your osx partition, becuase you could copy over data from the borked osx partition over to external drive or suchlike.


cheers,
303

---

### Post by altonbr on 2007-05-02
> **Chrisj303 said:**
> Honestly, if i was in your position i would forget about getting a working dualboot setup from this, and just concentrate on pulling out whatever you need from the HFS+ partition, then i would start from scratch.

I don't know for definite, but i really don't think it is possible to install rEFIt onto your OSX partition from ubuntu, not properly anyway.

 I have never used the Mac's install discs as a repair tool - as someone mentioned earlier this could very well save your life! 

You still haven't mentioned what type of Mac your using. If possible i would physically remove the drive and transplant it into another mac, that way you can dump anything important, then copy it back over later (when you have a functioning setup).

If thats not possible i would boot into ubuntu and use synaptic to download the HFS+ tools - to enable you to mount, read and write to your osx partition, becuase you could copy over data from the borked osx partition over to external drive or suchlike.


cheers,
303

I've already mounted the filesystem and backed up my data (as described here: [http://ubuntuforums.org/showpost.php?p=2579248&postcount=9)](http://ubuntuforums.org/showpost.php?p=2579248&postcount=9)).

I am using a MacMini, so there is no floppy, and it looks next to impossible to open up.

I don't have access to the recovery disk as this is my co-op boss' computer and he is out of town for the week. He gave me permission to install Ubuntu so long as I promised that Mac OS X would still boot up. By all logic, I thought it would.

---

### Post by Gen2ly on 2007-05-02
> **Chrisj303 said:**
> Honestly, if i was in your position i would forget about getting a working dualboot setup from this, and just concentrate on pulling out whatever you need from the HFS+ partition, then i would start from scratch.

Agreed.  You have OSX on your second partition but the partition table is flubbed.  Partition number 2 listed below should be "HFSplus Mac OS X" partition or something like that.  Believe me when you have to start all over again (including OSX)  I messed this up b4 too.  Use the [Gentoo]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook") or [Ubuntu Wiki]("https://help.ubuntu.com/community/MacBook") to partition correctly.

```
Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     96238656  Linux LVM
 3       96238657    115769907  Basic Data
 4      115769908    117209361  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2 *       409640     96238656  8e  Linux LVM
 3       96238657    115769907  83  Linux
 4      115769908    117209361  82  Linux swap / Solaris
```

Good luck.

---

### Post by altonbr on 2007-05-02
I quoted in post#9 that my HD still can read the HFS+ partition:

```
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags       
 1      20.5kB  210MB   210MB   fat32        EFI system partition  boot, hidden
 2      210MB   49.3GB  49.1GB  hfs+         Customer              hidden, lvm 
 3      49.3GB  59.3GB  10.0GB  ext3                                           
 4      59.3GB  60.0GB  737MB   linux-swap          
```

Does the problem have something to do with the flags?

---

### Post by Gen2ly on 2007-05-02
Its an early guess but I think you may not have used apples partitioning tools.  Check!?  Mac use a fairly complicated partitioning scheme.

```
 2         409640     96238656  Linux LVM
```

Is not valid.  I'm too bz to compare by reboot but I have zero doubt its wrong.  Sorry to break it to you.

The mac mini has a DVD burner doesn't it?

---

### Post by ronocdh on 2007-05-02
> **altonbr said:**
> I quoted in post#9 that my HD still can read the HFS+ partition:

```
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags       
 1      20.5kB  210MB   210MB   fat32        EFI system partition  boot, hidden
 2      210MB   49.3GB  49.1GB  hfs+         Customer              hidden, lvm 
 3      49.3GB  59.3GB  10.0GB  ext3                                           
 4      59.3GB  60.0GB  737MB   linux-swap          
```

Does the problem have something to do with the flags?
Sure, go ahead and try messing with the flags on Partition 2. It appears that when you resized the partition it was changed from a primary party to a logical one (see lvm flag). This means it's unbootable, as has already been said in this thread.

I'll add my opinion that you should get an OS X disc and completely reformat. As long as you are sure you have your boss's files backed up, you should be OK; the user folder (especially the "Library" directory) will be extremely valuable in replacing all his/her settings and documents.

But again, go ahead and experiment with the flags. It's not like you have anything to lose at this point, because you have backed up the data (a wise move!).

---

### Post by altonbr on 2007-05-03
Can someone post their partition table... someone who is dual booting Mac OS X and Ubuntu like I am.

My current table looks like this:
```
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI system partition  boot 
 2      210MB   49.3GB  49.1GB  hfs+         Customer                   
 3      49.3GB  59.3GB  10.0GB  ext3                                    
 4      59.3GB  60.0GB  737MB   linux-swap
```

I was able to boot to the EFI partition (the one that shows the Apple logo and the loading gif) but it was unable to talk to the HFS+ partition. I'm hoping there is just a flag I am missing, because that seems to have shown progress thus far. Once I can boot into Mac OS X, I'll use... BootCamp and rEFIt ?... to dual-boot into Ubuntu.

Thanks for all your help everyone. Much appreciated.

---

### Post by altonbr on 2007-05-03
While I'm waiting, a guy at [http://modular.math.washington.edu/macbook/](http://modular.math.washington.edu/macbook/), has this has his partition table. It's almost verbatim to mine.

```
Disk /dev/sda: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      20.5kB  210MB   210MB   fat32        primary  boot
 2      210MB   21.6GB  21.3GB  hfs+         primary
 3      21.6GB  27.0GB  5450MB  hfsx         primary
 4      27.0GB  29.0GB  2000MB  linux-swap   primary
 5      29.0GB  100GB   71.0GB  ext3         primary

```

This was his instructions that I *should* have followed:
>    7. Reboot your computer into OS X. Then set it up so it can dual boot both OS X and Linux as follows:
         1. Download rEFIt, and extract it to the root of your HFS+ OSX partition, then "bless" it (note that osx below may be different for you):

            $ cd /Volumes/osx
            $ sudo bless --folder . --file refit.efi --setBoot --labelfile refit.volicon

            Also, create a directory /Volumes/osx/Linux by copying the directory /efi/elilo from the Linux live boot CD. IMPORTANT! You must edit /Volumes/osx/Linux/elilo.conf or Linux won't be able to mount the root device when it boots up. In particular, you must have root=/dev/sda5 in your kernel append options (or /dev/sdax for approproriate x if you set things up differently than I did). Also, you can safely delete the initrd's, which are only needed for the live boot CD (as far as I can tell). But if you do that make sure not to list them in elilo.conf.
         2. Reboot. You should now have the choice of booting into either OS X or Linux. If you do not make a selection in 20 seconds, OS X will automatically boot up. As of 2006-04-03, the boot menu, options, and timeout seem to not be configurable (except probably by building your own custom rEFI boot program). Select Linux and boot up. You should boot up into your new hard-drive-installed Linux system. At this point typing startx should take you to a Gnome session.
         3. Configure your new Linux system, e.g., to get the machine to automatically start your favorite window manager with you logged in, etc. This is outside of the scope of this webpage, since it has nothing in particular to do with MacBooks. I do make a few MacBook-relevant remarks below though. 



---

### Post by altonbr on 2007-05-03
Apparently I was giving the Mac enough time to boot. I let it sit at the grey screen with the Apple logo and it eventually booted up.

Since I already burned rEFIt onto CD, I had the installer read to go. I double-clicked "rEFIt.mpkg" and it went through the installer as usual. If I knew the root password, I could tell you if it worked properly, but it looks like it will

```
**Automatic Installation with the Installer Package**

Both disk image distributions (.dmg and .cdr) also contain the new installer package. It will install rEFIt on your Mac OS X installation volume and make sure it is active. This is now the recommended way to install and use rEFIt.

The steps to install rEFIt this way are as follows:

   1. Download and mount the rEFIt-0.9.dmg disk image.
   2. Double-click on the “rEFIt.mpkg” package.
   3. Follow the instructions and select your Mac OS X installation volume as the destination volume for the install.

If everything went well, you’ll see the rEFIt boot menu on the next restart.
```

**THUS, the problem I has originally was that the boot partition was flagged "hidden" and the Mac HFS+ partition was flagged "hidden" and "lvm". Once that was changed, the Mac was able to boot, and rEFIt was able to install.**

Thanks again to everyone that helped, and an applause to the rEFIt developers as it's an excellent program (very clean aesthetically too).

---

### Post by Gen2ly on 2007-05-03
> THUS, the problem I has originally was that the boot partition was flagged "hidden" and the Mac HFS+ partition was flagged "hidden" and "lvm". Once that was changed, the Mac was able to boot, and rEFIt was able to install.


Ah, that explains the lvm we saw on the second partition listed by rEFIt, but because it was hidden rEFI wouldn't boot it (thats your real fix).  I still have no idea how you originally got to this point, but I'm glad you got it fixed....

But, its a hack of a fix.  Note upgrading grub and other things may ruin your partition table.  You must be circumventing the GPT-EFI partitioning with elilo, which is an odd (and very likely) and unsafe hack. watch

 U won't reinstall.

---

### Post by altonbr on 2007-05-04
> **Dirk.R.Gently said:**
> Ah, that explains the lvm we saw on the second partition listed by rEFIt, but because it was hidden rEFI wouldn't boot it (thats your real fix).  I still have no idea how you originally got to this point, but I'm glad you got it fixed....

But, its a hack of a fix.  Note upgrading grub and other things may ruin your partition table.  You must be circumventing the GPT-EFI partitioning with elilo, which is an odd (and very likely) and unsafe hack. watch

 U won't reinstall.

I'll keep you updated :P

---

