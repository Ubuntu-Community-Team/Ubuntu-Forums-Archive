---
title: "XP crash NTFS refugees"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by WSmart on 2008-04-15
I'm trying to mount two XP NTFS drives, after XP crashed.  But I have a couple roadblocks.

The boot drive mounts.  I can read the files.  I can open a file and save it outside of the drive.  But I can't copy a file directly out.  I get no message.  It just doesn't work.  I'm trying to copy some program config files, Azureus, into a new install of the progam on my Gusty machine.

The second XP drive won't mount.  I get a message saying that the NTFS drive is marked in use and I can force mount it, &#8220;for your own responsibility&#8221;.  

I'm looking for anything anyone can offer here.  I don't want to load a windows install just so I can properly unintall this drive, but what problems will a force mount cause?.  I have a BartPE disc that I can load a windows environment through..  Wonder if I could do it that way.  But then I can't even copy files from the drive that did mount.  I wish all my data was in one location, ala VMWare.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x043c8ba8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2fc4689d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01baec48

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       18700   150207718+  83  Linux
/dev/hda2           18701       19457     6080602+   5  Extended
/dev/hda5           18701       19457     6080571   82  Linux swap / Solaris


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f76818d8-b563-4c0c-9917-61c55728 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=722e597e-7346-4add-b79f-c0ecd7a none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by skymera on 2008-04-15
A force mount will cause near no problems.
i force mount mine when the BSOD's get too much.

ok so your only trying to mount them? should be easy.

First make the directorys you want to mount them too.

```
 sudo mkdir /media/drive1
sudo mkdir /media/drive2 
```

change drive 1 and 2 to your desire.

Then mount the devices to the directories you just created :)

```
 sudo mount /dev/sdX /media/drive1
sudo mount /dev/sdXX /media/drive2 
```

you can find the drive details from ```
 sudo fdisk -l 
```
Lower case L

Thats it, they are mounted and are accessible through Terminal or Nautilus.

---

### Post by WSmart on 2008-04-16
Snoopy dance;  I got a reply!

Gusty did a great job of mounting these.  I already had named these drives in XP and they're showing up in the Gutsy Computer folder with those names.  I'm a bit shy when it comes to working in the terminal, mostly because this is my primary system.  If I had several virtual machines, I wouldn't be shy about experimenting. 
	
The drive that wasn't mounting works now, after booting the drive with my BartPE disc. It just needed an NTFS handshake before shutting down.  

The other drive isn't even recognized in the Bart environment.  I can't brouse it, nada, nothing mano, pfft!  I'm sure that would be true in Windows too, if I cared to do a 'causual' install of Windows..  I think I need a disk uttility program to check this drive out.  It's a Western Digital drive and looks like I have to find a working floppy drive and floppy disc to use their solutions(@#!!!), unless anyone else has a suggestion, a Linux disk utility.  Pretty cool that I'm even able to browse the disk with Linux where I don't seem to be able to do that with Windows.  The XP machine was running fine, then it spontaneosly crashed, the hard drive made the toaster noise a couple times, and after that I was able to boot past the boot menu I have, to the Windows screen, then it reboots.  I noticed this boot drive was not doing it's normal boot cycle chatter.  

Again, I have no complaints with how Gutsy Ubuntu handled the mounting, on the working drives, except the message I got didn't pop up all the time.  Not sure if it was poping up in the background or what.  I saw it start to flash but it didn't populate or actually read anything, just flashed for a second.  I noticed it didn't toggle with Alt-tab.  Once I saw it, I had to keep it on top or minimize any windows on top of it, to see it.  It actually recommented booting the drive with windows as a solution, so that was great. 

Thanks to * for looking at this and thanks for the response!

---

### Post by WSmart on 2008-04-22
As a follow up, Western Digital has a wonderful ISO diagnotic tool which fixed the problem I was having with the XP system, a read element failure, so I&#8221;ve got the XP machine back up.  

I was trying to get an Azureus BitTorrent install, the only thing left on my XP machine, reovered to my Ubuntu machine..  I couldn't get Azureus to pick up directories from mounted NTFS drives.  When I hit brouse, there was no way to get to the /media folder.  I'm going to try and move Azureus to it's own machine by transfering the data in rather than moving hard drives. 

Thanks all.  Bill

---

