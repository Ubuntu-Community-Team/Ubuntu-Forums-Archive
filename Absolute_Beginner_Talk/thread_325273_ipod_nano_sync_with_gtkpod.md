---
title: "ipod nano sync with gtkpod"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by Paul Barnett on 2006-12-25
I am trying to sync an Ipod nano with gtkpod. When I try to sync i get this message "Error opening '/media/ipod/iPod_Control/Music/F00/gtkpod808617.mp3' for writing (Read-only file system)". What do I need to do? Thanks, Paul

---

### Post by K.Mandla on 2006-12-25
(Moved to Absolute Beginner Talk. ;) )

---

### Post by blakesmith on 2006-12-25
Just add a song to the iPod playlist and sync it, it'll format your iPod and you'll be set.

---

### Post by atonaldenim on 2006-12-25
I had this same error trying to copy files to an iPod Nano in Rhythmbox. It automounted and could read the iPod's music fine, but couldn't upload any music to the iPod. Turns out that Edgy was mounting the iPod read-only, even though it was mounted with the "rw" mount option, because it was a Mac formatted drive (HFS+) with Journaling enabled.

Recent Linux kernels have decent support for writing to an HFS+ filesystem, but still can't handle writing to a *journaled* HFS+ filesystems. So Journaled iPods are mounted read-only under Linux - the output from **dmesg** should indicate as much.

So - the quick fix is to turn off journaling on your iPod. It's nondestructive and takes about 5 seconds, you'll just need a Mac OS X machine.

Plug the iPod into the Mac, and at the OS X Terminal enter the command ```
 diskutil disableJournal /Volumes/(name of ipod) 
``` After that, the iPod should mount read/write under Linux, and the write errors should go away! Mine works great now.

If you don't have access to a Mac, you could also reformat the iPod under Linux with a non-journaled HFS+ filesystem. For this, you'll need to compile Apple's HFS tools on your Linux machine, particularly **mkfs.hfsplus**. For instructions on this option, see the [Gentoo Linux hfsplus howto]("http://gentoo-wiki.com/HOWTO_hfsplus"). Also [this forum thread.]("http://ubuntuforums.org/showthread.php?t=2221&highlight=mkfs.hfsplus")

The final option, if you have access to a Windows box, would be to convert the iPod to Windows FAT32 format instead, using iTunes on Windows. Linux has better FAT32 support and will handle a Windows formatted iPod better than a Mac one.

(of course: **reformatting your iPod with either of these last 2 options will erase all music** and data on the drive. Disabling journaling, however, doesn't harm your music in any way.)

(also - if you're a Rhythmbox user, the latest versions of Rhythmbox have pretty good iPod read/write support built-in. Edgy's version 0.9.6 should work fine, but [Version 0.9.7 was also just released]("http://www.mail-archive.com/ftp-release-list@gnome.org/msg03275.html") for you cutting-edge types, and compiled fine on my Edgy machine. Finally, a fairly complete iTunes replacement in Gnome!)

---

### Post by Paul Barnett on 2006-12-26
Thanks, I reformated the ipod but I cannot mount it correctly. Gtkpod sees it but when I try to sync it to gtkpod I get an error message saying the the ipod directory structure is not present. Paul

---

### Post by Skraeling on 2006-12-27
Same thing happens to me.
Does your ipod mount correctly?

---

### Post by atonaldenim on 2006-12-27
after reformatting, then blakesmith's advice applies: you'll have to use iTunes to add some music to the iPod, which will create the proper filesystem structure. After that, you should be set.

I'm not sure if gtk/yami pod have this ability or not. You can try **File -> Create iPod's Directories** in gtkpod, that might do the trick also.

After all that, if gtkpod still doesn't work, give it a shot in [Banshee]("http://www.banshee-project.org"), as it uses a different library ([libipoddevice]("http://www.banshee-project.org/Subprojects/Libipoddevice")) than gtkpod/Rhythmbox ([libgpod]("http://www.gtkpod.org/libgpod.html")), and seems to be more actively developed. I'm not sure if gtkpod has support for the newest iPods, there was [some change Apple made]("http://www.snorp.net/log/2006/09/18/maybe-theyre-not-as-bad-as-i-thought/") to the internals of the newest iPods that broke existing programs -- support was added to libipoddevice but I can't tell if libgpod was similarly updated. 

Let us know what happens!

---

### Post by Paul Barnett on 2006-12-27
Ince I cnnot mount my ipod correctly I cannot use itunes. THe files in the ipod are there and correct but gtkpod cannot see them. It is formated for fat (windows) files. I have modified /etc/fstab to mopunt the ipod.
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=313492e8-6892-4dc7-a701-34366af5d39c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=00ef50a0-8211-44c1-b940-a2486f660f8d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda2 /mnt/ipod vfat user,noauto,umask=000 0 0

When I try to sync it with gtkpod i get an error message "iPod directory structure must be present before synching to the iPod can be performed." indicating that the file system does not exist. Any more ideas? Thanks

---

### Post by atonaldenim on 2006-12-29
I'm a little confused when you say you can't mount the iPod. 

Do you mean that when you use the command "mount" it fails? Because if so, then I don't understand how it could have the proper directory structure.

Or do you mean that it IS able to be mounted (attached to the filesystem), and you can list its contents and add and remove files from it and so forth, but only that gtkpod has problems syncing to its music database? This is what I think you're saying.

Or... can you mount the iPod on other computers (or OSes) but just not in Linux?

And just to make sure, you have tried in iTunes to add a song to the iPod, and it was successful? Also - can the iPod play this music properly when disconnected from the computer?

If so, have you tried using Banshee instead of gtkPod? (sudo apt-get install banshee)

From your fstab, that you are mounting /dev/sda2 seems to indicate that you were careful and preserved the iPod's partitioning scheme, which is a good thing. 

One thing you haven't mentioned yet: how exactly did you reformat the iPod? The only proper way to convert a Mac iPod to Windows format is to use iTunes on Windows, because of the iPod's peculiar partitioning/firmware setup. It is ok to use mkfs.hfsplus on Linux to reformat a Mac iPod with a non-journaled HFS+ filesystem, because it's still HFS+ in the end. However, to switch from HFS+ to VFAT requires more drastic changes which only iTunes can handle. If you happened to have simply done a "mkfs.vfat /dev/sda2" in Linux, you'll have to find a Windows box and do it the iTunes way. 

See Apple's support document [Restoring iPod to factory settings]("http://docs.info.apple.com/article.html?artnum=60983") for the official line.

---

### Post by atonaldenim on 2006-12-29
Oh... I re-read your post, and now I understand that you can mount the iPod in Linux but not in Windows (or Mac OS X? can't tell.) 

From this, it sounds like you did an "mkfs.vfat" on a Mac iPod, which I think would break it under Windows, because the iPod would still have a Macintosh-style partition layout and that seems like it would confuse poor Windows. (The way Macintoshes partition hard drives is different than the way that Windows/Linux computers partition hard drives. Not just the filesystem format but the actual map of partitions is different.)

Also, I was wrong in my last post, on a Mac formatted iPod the right partition to mount would be /dev/sda3, not 2. sda2 is appropriate for a Windows iPod, but only if it has been completely restored with a DOS-style partition table using iTunes on Windows. Again, not sure how you did the reformat.

On the topic of fstab, [this Gentoo wiki page]("http://gentoo-wiki.com/HOWTO_Using_an_iPod_With_Gentoo_Linux") claims the appropriate fstab entry should look like:
```
/dev/sda2  /media/ipod  vfat  async,nodev,nosuid,user,rw,noauto 0 0
```
the most significant difference being that yours doesn't have "rw" - maybe try adding that?

I think your best bet, if Windows can't read the iPod now, is to either find a Mac and hope that it can read it, restore it back to a Mac iPod and turn off journaling as explained before; or to put it back to an HFS+ filesystem either on a Mac or by compiling mkfs.hfsplus on your linux machine, as explained on the [Gentoo wiki page]("http://gentoo-wiki.com/HOWTO_hfsplus#Compiling_Apple.27s_Filesystem_Tools") I mentioned earlier. 

Could you post the output from **dmesg** after you plug your iPod in? Mine looks like:
```

[17219743.592000] usb 2-1: new full speed USB device using uhci_hcd and address 9
[17219743.764000] usb 2-1: configuration #1 chosen from 2 choices
[17219743.768000] scsi6 : SCSI emulation for USB Mass Storage devices
[17219743.768000] usb-storage: device found at 9
[17219743.768000] usb-storage: waiting for device to settle before scanning
[17219748.768000] usb-storage: device scan complete
[17219748.772000]   Vendor: Apple     Model: iPod              Rev: 1.62
[17219748.772000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17219748.776000] SCSI device sda: 1999871 512-byte hdwr sectors (1024 MB)
[17219748.784000] sda: Write Protect is off
[17219748.784000] sda: Mode Sense: 68 00 00 08
[17219748.784000] sda: assuming drive cache: write through
[17219748.796000] SCSI device sda: 1999871 512-byte hdwr sectors (1024 MB)
[17219748.800000] sda: Write Protect is off
[17219748.800000] sda: Mode Sense: 68 00 00 08
[17219748.800000] sda: assuming drive cache: write through
[17219748.800000]  sda: [mac] sda1 sda2 sda3
[17219748.824000] sd 6:0:0:0: Attached scsi removable disk sda
[17219748.824000] sd 6:0:0:0: Attached scsi generic sg0 type 0

```

Also, could you post the output of "parted /dev/sda print"... here's mine:
```

Disk /dev/sda: 1024MB
Sector size (logical/physical): 512B/512B
Partition Table: mac

Number  Start   End     Size    File system  Name     Flags
 1      0.51kB  32.3kB  31.7kB               primary       
 2      32.3kB  82.3MB  82.2MB               primary       
 3      82.3MB  1020MB  938MB   hfs+         primary       

```

One final, drastic option would be to completely re-partition the iPod under Linux, with a DOS-style partition table and a VFAT filesystem, and recopy the firmware to the first partition (sda1) using **dd**. I have not tried this, do not recommend trying it as it may completely break the thing forever, and the instructions on doing so are old and I don't know how similar are new iPod Nanos. But the page is [here]("http://pag.csail.mit.edu/~adonovan/hacks/ipod.html"), if you're interested.

---

### Post by atonaldenim on 2006-12-29
or... have I been misunderstanding all along, and it was never mac formatted? it was always vfat?

oops! I didn't know this:
> ...iPod nano comes preformatted for Windows (FAT32 file system). The first time you connect to a Macintosh, iPod nano will "reformat" itself to work with a Mac (HFS+ file system). This only occurs the first time you connect iPod nano to your Mac, and if you've never connected it to another computer.

Note: There are a few situations when iPod nano won't be optimized for Mac OS:

    * If you connect iPod nano to a Windows PC the very first time you use it and then connect iPod nano to your Mac.
    * If you open iTunes for the first time before you connect iPod nano for the first time, but you do not agree to the iTunes Software License Agreement.

In both cases, you will not see the "Optimizing" dialog, and iPod nano will not be optimized for Mac OS. If this happens to you, you can optimize iPod nano for Mac OS by simply using iPod Updater to restore iPod nano on your Mac.

[http://docs.info.apple.com/article.html?artnum=61672](http://docs.info.apple.com/article.html?artnum=61672)

---

### Post by Paul Barnett on 2006-12-29
View Profile Email Personal Message (Online) 	
	Re: help with ipod nano
« Reply #4 on: Today at 01:31:45 PM » 	Reply with quote Modify message Remove message


This is where I am now.  I have reformated the ipod from a windows PC. The ipod will mount on my PC. 
paul@paul-desktop:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             75434976  13484640  58118436  19% /
varrun                  257700       104    257596   1% /var/run
varlock                 257700         0    257700   0% /var/lock
procbususb               10240       144     10096   2% /proc/bus/usb
udev                     10240       144     10096   2% /dev
devshm                  257700         0    257700   0% /dev/shm
lrm                     257700     17580    240120   7% /lib/modules/2.6.17-10-generic/volatile
/dev/sda2              3853648   1310480   2543168  35% /mnt/ipod
paul@paul-desktop:~$
I have been able to load files on from a Windows PC. When I connect the ipod to my computer the ipod appears mounted. However when I try to access ipod from gtkpod I get this message ''/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted."
Amarok can read and play files from ipod but cannot transfer any files to the ipod. Thanks for the help. Paul

---

### Post by rfruth on 2006-12-31
Thanks all and Happy New Year ~!  I got a nano for xmas and it works great on my G3 iMac, after  diskutil disableJournal /Volumes/(name of ipod) it also works on my x86 Ubuntu box (am using the Ipod nano for disk storage, among other things) 8)

---

### Post by atonaldenim on 2007-01-04
hey paul-

sorry about the potentially bad advice earlier (although glad it helped someone else!)

I'm not sure what might be causing the iTunes DB problem with gtkpod. That sucks. sorry that gtkpod is not working for you. has it ever worked in the past?

But, if Amarok can read the iPod fine, but can't write to it, then I wonder if your fstab entry is the reason. Did you keep the same fstab as before? Because your system might be mounting the iPod read-only if you don't add the "rw" option. And being mounted read-only is probably the source of the initial sync errors in gtkpod, and also why I mistakenly thought it was an HFS+ iPod.

Try adding rw as an option to your fstab entry for the iPod. And if that still doesn't work, try removing the iPod line altogether maybe? I don't know what version you're using, but on Edgy, I could just plug in the iPod with no fstab entry, and HAL/dbus took care of everything and it popped up on my (Gnome) desktop with a little iPod icon, and Banshee/Rhythmbox recognized it without any configuration. Amazing.

---

