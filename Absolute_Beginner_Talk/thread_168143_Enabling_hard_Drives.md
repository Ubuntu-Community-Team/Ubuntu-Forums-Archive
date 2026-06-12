---
title: "Enabling hard Drives"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by georgetoon on 2006-04-29
I have a rack system. I succesfully installed Ubuntu to my 200 gig hard drive (using 14 gigs of space) and have a second rack housing another 200 gig hard drive. it has multiple partitons (FAT32)  ubuntu wil not enable these.  When I selct the drive in System Adminsitaration and select "enable"  the drive dos not enable.
I'm assuming I'm missing a step.

---

### Post by jazzmuzik on 2006-04-29
Mounting windows and nfs disks:
[indent][http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)[/indent]

---

### Post by georgetoon on 2006-04-29
[QUOTE=jazzmuzik]Mounting windows and nfs disks:
[indent][http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)[/indent][/QUOTE]

I thought Ubuntu was suppossed to be easy?

why the heck do I have to jump through all these hoops?  isn't there a redetect routine in grub? why can't I just enable the drives?  Sorry if I sound a bit short here, but this really dosnt make sense.  I've run a few other ditros as Live CDs and all just let me clikc and enable or mount these dirrves. now that I finally have Ubuntu on a HD, this situatin arises.

---

### Post by aysiu on 2006-04-29
[QUOTE=georgetoon]I thought Ubuntu was suppossed to be easy?

why the heck do I have to jump through all these hoops?  isn't there a redetect routine in grub? why can't I just enable the drives?  Sorry if I sound a bit short here, but this really dosnt make sense.  I've run a few other ditros as Live CDs and all just let me clikc and enable or mount these dirrves. now that I finally have Ubuntu on a HD, this situatin arises.[/QUOTE] I'm confused by this too. It's one of the nice features that Knoppix and Mepis have (though, the new Mepis doesn't appear to have this feature, and it's based off of Ubuntu...).

Honestly, though, it's a hoop you have to jump through only once. After you set up your Windows drives in the /etc/fstab file, they'll be automounted at every bootup.

---

### Post by georgetoon on 2006-04-29
[QUOTE=aysiu]I'm confused by this too. It's one of the nice features that Knoppix and Mepis have (though, the new Mepis doesn't appear to have this feature, and it's based off of Ubuntu...).

Honestly, though, it's a hoop you have to jump through only once. After you set up your Windows drives in the /etc/fstab file, they'll be automounted at every bootup.[/QUOTE]
Perhaps, but Ubuntu found my external USB HD.:) find the drive every time.  i don't ahve to do a thing.  It's FAT32, as well.

I won't knock ubuntu as I think it's a very neat and clean OS.:)  but I'm not going to pursue it much more either. I have lots of free space on this HD to use other distros.  I'll experiment.  When ubuntu fixes this problem, then I'll be back.:)

---

### Post by aysiu on 2006-04-29
[QUOTE=georgetoon]Perhaps, but Ubuntu found my external USB HD.:) find the drive every time.  i don't ahve to do a thing.  It's FAT32, as well.[/quote] Yeah, that adds to the weirdness. Automounting external hard drives--automatic. Automounting internal ones--manual.

> 
I won't knock ubuntu as I think it's a very neat and clean OS.:)  but I'm not going to pursue it much more either. I have lots of free space on this HD to use other distros.  I'll experiment.  When ubuntu fixes this problem, then I'll be back.:) I think it's easier to add a couple of lines to your /etc/fstab than to install an entirely new distro, but whatever works for you.

---

### Post by georgetoon on 2006-04-30
[QUOTE=aysiu]Yeah, that adds to the weirdness. Automounting external hard drives--automatic. Automounting internal ones--manual.

 I think it's easier to add a couple of lines to your /etc/fstab than to install an entirely new distro, but whatever works for you.[/QUOTE]

Actually, it's easiest to just click "Mount" or "Enable" and have the drive mounted and working.;) :D 

No really, I'm one of those guys who just wants to stay away from command lines and editing  /etc/fstab, etc.:)  ](*,) 

This HD is srictly experimental...trying out different Linux distros. Ubuntu will stay installed and I'll plug it in every now and again to see what's new.  Maybe sometime down the road an update will come along and bingo, my HD partitions will be awakened and enabled with the click of a mouse.:)  

All in all, though, I've found Ubuntu to be quite engaging and a really nice OS.  Very  clean, very fast. Installing software is quite easy, as well, and a really top notch feature! I'm impressed.:)

I hope to learn more.

the folks up on this forum are really very nice.:D :cool:   Thanks so much for your patience with me.

---

### Post by georgetoon on 2006-04-30
Just for the record, I did visit the link a member provided me and gae that method a try.  I was realy curious. I have no idea what the heck I'm doing. Dang!  My problem is still unresolved.  Dang!

---

### Post by mrgotea on 2006-04-30
I followed the steps in the guide listed above and it only took a few minutes. 

> No really, I'm one of those guys who just wants to stay away from command lines and editing /etc/fstab, etc.  

Don't shy away from the command line.

---

### Post by georgetoon on 2006-04-30
[QUOTE=mrgotea]I followed the steps in the guide listed above and it only took a few minutes. 



Don't shy away from the command line.[/QUOTE]

Okay,  I tyrioed it again and I'm not understanding tyhe process.  Am I doing this editing in the terminal?  or am I doing editing in a text editor?

Lost.

---

### Post by georgetoon on 2006-04-30
Okay, hang on...i found the fstab file.:)  Okay, so i need to edit this file in some way to get these fat32 partitons mounted/  Rightnow, this is what fstab says:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

My internal FAT32 partitions are on a 200 gig HD in the lower rack set to slave.

They are at:

/dev/hdd1
/dev/hdd5
/dev/hdd6
/dev/hdd7
/dev/hdd8
/dev/hdd9

So, what would I need to add to /etc/fstab to get the drives to be enabled?

---

### Post by aysiu on 2006-05-01
You have to make the mount points first: ```
sudo mkdir /fat1
sudo mkdir /fat2
sudo mkdir /fat3
sudo mkdir /fat4
sudo mkdir /fat5
sudo mkdir /fat6
``` Then, add these entries to your /etc/fstab
```
/dev/hdd1 /fat1 vfat iocharset=utf8,umask=000 0
/dev/hdd5 /fat2 vfat iocharset=utf8,umask=000 0
/dev/hdd6 /fat3 vfat iocharset=utf8,umask=000 0
/dev/hdd7 /fat4 vfat iocharset=utf8,umask=000 0
/dev/hdd8 /fat5 vfat iocharset=utf8,umask=000 0
/dev/hdd9 /fat6 vfat iocharset=utf8,umask=000 0
```

---

### Post by georgetoon on 2006-05-01
Thank you.:)  One problem..I'm not root.  How do I open this as root so I have permission to edit?

Wait. i figured it out by doing a search and got root privleges to edit. i was ale to enable the partiitons.. but they stil do not show up. I'm going to restart the system.  Maybe this wil do it.:)

Rebooted and I see where my mistake is...i was looking in the "mnt" foler to find a Drive icon. Al the partitons are present as Fat1, Fat2,  etc. folders at the / level.:)

many, many thaks to all!:)  I can see these files now.:)  I'm assuming I can make shortcuts to the desktop.:)

---

### Post by aysiu on 2006-05-01
[QUOTE=georgetoon]I'm assuming I can make shortcuts to the desktop.:)[/QUOTE] Yes. If you're in Gnome, middle-click-drag the icon to the desktop and select "link here." If you're in KDE, just drag it with the left-click and do the same.

---

### Post by georgetoon on 2006-05-01
[QUOTE=aysiu]Yes. If you're in Gnome, middle-click-drag the icon to the desktop and select "link here." If you're in KDE, just drag it with the left-click and do the same.[/QUOTE]

Middle click?  I don't have a three button mouse.

---

### Post by confused57 on 2006-05-01
It's me again, if you have a scroll wheel, it acts as a middle button; I just found that out a couple of weeks ago.  Clicking the left and right mouse buttons simultaneously is supposed to accomplish the same thing as a middle click.

---

### Post by georgetoon on 2006-05-01
[QUOTE=confused57]It's me again, if you have a scroll wheel, it acts as a middle button; I just found that out a couple of weeks ago.  Clicking the left and right mouse buttons simultaneously is supposed to accomplish the same thing as a middle click.[/QUOTE]

Thank you for that piece of info!:)  Gonna try that tonight then.:)

---

### Post by Giga on 2006-05-01
[quote=aysiu]You have to make the mount points first: ```
sudo mkdir /fat1
sudo mkdir /fat2
sudo mkdir /fat3
sudo mkdir /fat4
sudo mkdir /fat5
sudo mkdir /fat6
``` Then, add these entries to your /etc/fstab
```
/dev/hdd1 /fat1 vfat iocharset=utf8,umask=000 0
/dev/hdd5 /fat2 vfat iocharset=utf8,umask=000 0
/dev/hdd6 /fat3 vfat iocharset=utf8,umask=000 0
/dev/hdd7 /fat4 vfat iocharset=utf8,umask=000 0
/dev/hdd8 /fat5 vfat iocharset=utf8,umask=000 0
/dev/hdd9 /fat6 vfat iocharset=utf8,umask=000 0
```[/quote]

Hy Aysiu,
my fstab is like this:
[quote=aysiu]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb        /media/usb0     auto    rw,user,noauto  0       0
/dev/sda1       /mnt/ata        auto    rw,user,uid=1000 0 0 [/quote]

i have some questions about  fstab
1) the rw means read and write , right?
So why this is happening?
[quote=aysiu]

giga@ubuntu:/media/USB DISK$ sudo cp bookmarks.html /mnt/ata/
cp: cannot create regular file `/mnt/ata/bookmarks.html': Read-only file system
giga@ubuntu:/media/USB DISK$[/quote]

2) uid=1000 i got from command id which represents the user id who can use the ata drive? is it correct?

3) what means "auto"  and those zeros after uid?

4) How can i enable write to this ata HD? And doing this, is it secure? (or i am taking a risk of Linux write over ntfs partition table of this ata Hd and when i run Windows i might get that awful surprise that this ata HD will not be visible?

I read a HOWTO thread that the persons was telling its not 100% safe..i got a bit confuse.


Thanks

---

### Post by aysiu on 2006-05-01
NTFS is read-only in Linux.

For more on understanding the /etc/fstab, look here:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by jazzmuzik on 2006-05-01
When I use "iocharset=utf8" in fstab I get complaints from Linux...

I can't remember the error but I decided to remove that instruction.

---

