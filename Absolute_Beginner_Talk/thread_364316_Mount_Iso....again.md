---
title: "Mount Iso....again"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by SlimJimSouthpaw on 2007-02-18
I'm trying to mount an .iso file and am having no luck.

Here's what I've done so far that hasn't worked.

1) I've created a /media/iso to mount to
2) I navigate to the directory where the file lives
3) I use: sudo mount -t iso9660 -o loop BeggarsBanquet.iso /media/iso
               to try and mount said file, which is the Rolling Stones album Beggars Banquet

can't find the mounted CD image anywhere.  I obviously checked under /media/iso and I see no files, no nothing.

Is this a concept I'm misunderstanding, or am I putting this into practice the wrong way?

BTW, I get no errors at the Terminal, everything looks fine from there.

Thanks in advance for any help,

J

---

### Post by xopher on 2007-02-18
cd into /media/iso and do a ls: ```
ls
```

if that doesn't show anything, try ls as root: ```
sudo ls
```

If that helps, it's a permissions problem

---

### Post by SlimJimSouthpaw on 2007-02-18
Here's what I get....

cd /media/iso
> ls
> sudo ls
> 

So, obviously, nothing.

What should I do to fix the permissions problem?

J

---

### Post by xopher on 2007-02-18
Well it's not a permissions problem. If it was, then 'sudo ls' should have listed the files.

Are you sure the iso file is intact?

---

### Post by SlimJimSouthpaw on 2007-02-18
um... pretty sure.  I burned it to disc at one point.  However, can't remember checking it.  I'll go grab it really quick and see if it is corrupt.

J

---

### Post by SlimJimSouthpaw on 2007-02-18
Well, that must be the answer.  I can't get my drive to read the CD.  I'll try a few other .iso's I've got on here to see if those work.

J

---

### Post by SlimJimSouthpaw on 2007-02-18
Finally got something different.  Here is an error message from a different file...

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What is this telling me?

J

---

### Post by xopher on 2007-02-18
Yeah, 'cause as far as I know, the command you're running is 100% correct :)

If you mount a lot of iso's/other image formats then I suggest you try fuseiso, it probably won't help you get that iso-file working or anything, but it'll ease the mounting/umounting A LOT ;)

Think 'right click iso -> Mount, Right click folder on Desktop -> Umount' ;)

Here's more information about that if you're interested : 

[http://www.grumz.net/?q=node/282&PHPSESSID=3041df5167e6b5953d71d06e97bd9c3d](http://www.grumz.net/?q=node/282&PHPSESSID=3041df5167e6b5953d71d06e97bd9c3d)

---

### Post by xopher on 2007-02-18
> **SlimJimSouthpaw said:**
> Finally got something different.  Here is an error message from a different file...

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What is this telling me?


I have no idea about what that error would want you to do, sorry .. Only that it's implying that the filesystem line of your command might be a bit off. Which it, as far as I know, isn't. Really weird.

---

### Post by SlimJimSouthpaw on 2007-02-18
I've ripped all of these files via Ubuntu though.  Would this make a difference, using fuseiso or not?

I had problems with .iso's that I brought over from XP when I made the switch a few months ago as well.  I just deleted them since I went around and around trying to get Ubuntu to recognize them.

What I've used to rip them is, right click and select Copy Disc and then under the Copy Disc pull down, choose File Image.

All of those (only 4 of them) are corrupt.

J

---

### Post by SlimJimSouthpaw on 2007-02-18
I'm installing fuseiso right now.  I'll let you know how that works out.

J

---

### Post by xopher on 2007-02-18
Well, then is might be that your CD-ROM/DVD-ROM is the problem too. That it is what corrupts the files in the first place. Id download an iso file that's confirmed to work, and try mounting that. Eg. the ubuntu iso. If that works, then it's probably something with the CD-rom, might only be a hdparm settings or something like that.

And well, fuseiso shouldn't make a difference in if they work or not, so Id install it only after you've gotten things working. You get better output when doing everything manually.

---

### Post by SlimJimSouthpaw on 2007-02-18
I'll grab the ubuntu.iso quick and let you know what happens with that.

Thanks very much for all the help so far.  If you will be around for a while, I'll report back with my findings.

J

---

### Post by SlimJimSouthpaw on 2007-02-18
Ok, so I mounted the Ubuntu.iso just fine.  It showed up on my desktop and all the files were there, etc.

So, I think my drive is fine.  I can do everything else with it.  I have an internal that I've had problems with, but my external Lacie DVD/CD drive has never given me problems.

What do you think about the hdparm settings that you mentioned?  Anything I should try there?

J

---

### Post by xopher on 2007-02-18
Well, Im not sure at the moment (can't check things out myself, Im not home -- and even worse, Im at a windows computer so..).

It might be the nautilus-cd-burner app that's giving you problems too, have you tried eg. K3b, ripping an iso with that?

if you can get hdparm to list the properties of your DVD/CD then post that here too.

probably something like: (sudo) hdparm -l /dev/sda

---

### Post by SlimJimSouthpaw on 2007-02-18
Here's what I get from sudo hdparm -l /dev/sda

```
sudo hdparm -l /dev/sda

hdparm - get/set hard disk parameters - version v6.6

Usage:  hdparm  [options] [device] ..

Options:
 -a   get/set fs readahead
 -A   set drive read-lookahead flag (0/1)
 -b   get/set bus state (0 == off, 1 == on, 2 == tristate)
 -B   set Advanced Power Management setting (1-255)
 -c   get/set IDE 32-bit IO setting
 -C   check IDE power mode status
 -d   get/set using_dma flag
 --direct  use O_DIRECT to bypass page cache for timings
 -D   enable/disable drive defect management
 -E   set cd-rom drive speed
 -f   flush buffer cache for device on exit
 -g   display drive geometry
 -h   display terse usage information
 -i   display drive identification
 -I   detailed/current information directly from drive
 --Istdin  read identify data from stdin as ASCII hex
 --Istdout write identify data to stdout as ASCII hex
 -k   get/set keep_settings_over_reset flag (0/1)
 -K   set drive keep_features_over_reset flag (0/1)
 -L   set drive doorlock (0/1) (removable harddisks only)
 -M   get/set acoustic management (0-254, 128: quiet, 254: fast) (EXPERIMENTAL)
 -m   get/set multiple sector count
 -n   get/set ignore-write-errors flag (0/1)
 -p   set PIO mode on IDE interface chipset (0,1,2,3,4,...)
 -P   set drive prefetch count
 -q   change next setting quietly
 -Q   get/set DMA tagged-queuing depth (if supported)
 -r   get/set device  readonly flag (DANGEROUS to set)
 -R   register an IDE interface (DANGEROUS)
 -S   set standby (spindown) timeout
 -t   perform device read timings
 -T   perform cache read timings
 -u   get/set unmaskirq flag (0/1)
 -U   un-register an IDE interface (DANGEROUS)
 -v   defaults; same as -mcudkrag for IDE drives
 -V   display program version and exit immediately
 -w   perform device reset (DANGEROUS)
 -W   set drive write-caching flag (0/1) (DANGEROUS)
 -x   tristate device for hotswap (0/1) (DANGEROUS)
 -X   set IDE xfer mode (DANGEROUS)
 -y   put IDE drive in standby mode
 -Y   put IDE drive to sleep
 -Z   disable Seagate auto-powersaving mode
 -z   re-read partition table
 --security-help  display help for ATA security commands

```

J

---

### Post by SlimJimSouthpaw on 2007-02-18
looks more like options to me, than info about my cd drive

J

---

### Post by xopher on 2007-02-18
Yeah, well as I said, I couldn't remember the command completely. . .

Edit: Just SSH'd into my box, and it was as easy as: 'sudo hdparm /dev/sda'

---

### Post by SlimJimSouthpaw on 2007-02-18
are we looking for my external drive here?  If so, I checked my fstab and the only thing that looked remotely close was hdc

screw it.  here is my fstab in case that will help

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b597fda1-778a-49db-9689-7721bad23716 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6f3f62ca-92d4-4053-8f74-0f26987fb697 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hdb1 /storage ext3 defaults 0 0


```

J

---

### Post by xopher on 2007-02-18
We are looking for the DVD/CD-drive that's been causing you problems :) /dev/hdc is probably the internal one though.

---

### Post by SlimJimSouthpaw on 2007-02-18
i think /media/cdrom0 might be the one....i'll run hdparm on that real quick

J

---

### Post by SlimJimSouthpaw on 2007-02-18
maybe not...here's what I got for that

/media/cdrom0:
 BLKROGET failed: Inappropriate ioctl for device
 BLKRAGET failed: Inappropriate ioctl for device
 BLKGETSIZE failed: Inappropriate ioctl for device

J

---

### Post by xopher on 2007-02-18
Well /dev/hdc IS /media/cdrom according to fstab.

The external DVD/CD, how do you connect it?

---

### Post by SlimJimSouthpaw on 2007-02-18
gotcha...

firewire 400 for the external

J

---

### Post by xopher on 2007-02-18
Right. Paste the output of ```
sudo fdisk -l
```

If that would shed some light on where it's located ;)

---

### Post by SlimJimSouthpaw on 2007-02-18
```
Disk /dev/hda: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2385    19157481   83  Linux
/dev/hda2            2386        2491      851445    5  Extended
/dev/hda5            2386        2491      851413+  82  Linux swap / Solaris

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19929   160079661   83  Linux

```

J

---

### Post by xopher on 2007-02-18
It IS connected right? Because according to that it's not.. Haven't used firewire things myself so can't be totally sure but generally every storage device is listed there. Even usb memory sticks are shown. And usually they're called /dev/**s**dx.

---

### Post by SlimJimSouthpaw on 2007-02-18
it is most definitley connected.  I can put in a cd and it comes right up on the desktop

J

---

### Post by xopher on 2007-02-18
Allright. Well Im lost.. hehe. How does your mtab look like then?

---

### Post by SlimJimSouthpaw on 2007-02-18
```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-generic/volatile tmpfs rw 0 0
/dev/hdb1 /storage ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

```

never used mtab before.  What is this about?

J

---

### Post by xopher on 2007-02-18
mtab is a list of the currently mounted things. Can't find the cdrom there either..

But, as it works -- it definitely has to be SOMEWHERE. Im running out of ideas though.

---

### Post by SlimJimSouthpaw on 2007-02-18
just put a cd in and it shows up on the desktop and it plays fine with Sound Juicer, which is the default CD player.

any info I can get now that a CD is in?

J

---

### Post by pxwpxw on 2007-02-18
> **SlimJimSouthpaw said:**
> I'm trying to mount an .iso file and am having no luck.

3) I use: sudo mount -t iso9660 -o loop BeggarsBanquet.iso /media/iso
               to try and mount said file, which is the Rolling Stones album Beggars Banquet

can't find the mounted CD image anywhere.  I obviously checked under /media/iso and I see no files, no nothing.

J

Is there a problem there with mount -t iso9660 which is probably not the correct type for the Rolling Stones album - unless produced using mkisofs.

I dont know what is the correct type, but can someone shoot that idea down?

---

### Post by SlimJimSouthpaw on 2007-02-18
px,

thanks for jumping in...  all i'm trying to do is rip cd's dvd's etc. to .iso's.  I would hope to mount them, and also burn them back to blank media, etc.  

I'm trying, eventually, to catalog my entire cd collection.

if i have to go about it a different way than I am, I am fine with that.  let me know if you have any suggestions.

J

---

### Post by pxwpxw on 2007-02-18
Not my expertise, but question is how is the iso being produced?

---

### Post by SlimJimSouthpaw on 2007-02-18
From post #10

> What I've used to rip them is, right click and select Copy Disc and then under the Copy Disc pull down, choose File Image.

J

---

### Post by pxwpxw on 2007-02-18
What desktop and release are u using copy disc from? - I dont know what it produces, someone else may do. 

Also if you like to have a read of man mkisofs in a terminal, it may give you a hint, and would tell you how to create an iso9660 image the hard way.

---

### Post by xopher on 2007-02-18
When mounting, you could try to use 'auto' as the filesystem, if it's not iso9660, then it might recognize the correct one.

```
lshw
```

That might give you the logical name of it.

---

### Post by SlimJimSouthpaw on 2007-02-18
> **pxwpxw said:**
> What desktop and release are u using copy disc from? - I dont know what it produces, someone else may do. 

Also if you like to have a read of man mkisofs in a terminal, it may give you a hint, and would tell you how to create an iso9660 image the hard way.

Gnome, not sure of the release version.  Where can I check?  It seems to produce a raw cd image.  I'll have a look at the mkisofs manual.

J

---

### Post by SlimJimSouthpaw on 2007-02-18
tried 'auto' instead and got, "you must specify file system type"

J

---

### Post by SlimJimSouthpaw on 2007-02-18
had a quick look at the mkisofs manual and it seems a bit over my head at this point.  I could sit down and really figure it out, eventually.  But, for my situation is seems a bit overkill.

J

---

### Post by pxwpxw on 2007-02-18
dont know, will have a look here.

try **xophers** suggestion, mount -t autofs .....
or just leave out the -t iso9660, see what it does.
```
  sudo mount -o loop BeggarsBanquet.iso /media/iso 
```

---

### Post by SlimJimSouthpaw on 2007-02-18
tried both, autofs and leaving it blank.   autofs option gives me this:

```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

and blank gave me "must specify file system type"

I think I'm giving up for this evening.  I've got to go to bed, it's 5.40 am here.

Thank you all for your help so far.  I'll check the thread in the morning and possibly bump for the morning users.

J

---

### Post by pxwpxw on 2007-02-18
um,

I am out of ideas, I have xubuntu here cant find Copy Disc, will go look on another box with ubuntu desktop. But man mkisofs definitely worth a read. 

Will check back later.

---

### Post by pxwpxw on 2007-02-18
If someone comes up with the real answer (hopefully simple) thats good, 
but if not I tried a few things and so (open to comment):

1. A downloaded CD/DVD image file with .iso extension may not be 
an iso9660 image, although you might expect it to be. 
Images can be of other file systems e.g. msdos, ntfs 
(see man mount, The Loop Device.) 
Ubuntu is telling us your image is not an image of an iso9660 file system. 
An image is just an exact copy of everything on the source CD for example.	

2. I have ubuntu breezy here. It has Sound Juicer which extracts or plays 
 tracks from audio CD. It can access tracks on a music CD, but the CD
   does not show up anywhere in mount or df, or in the /dev/ tree, and I
 cant get it to mount in ubuntu. i.e. Sound Juicer seems to be controlling
 the CD drive directly, not mounting it in the Linux file system. 

But SJ cannot read an iso9660 CD holding mp3 music files (or probably any 
other format music files), however ubuntu can mount the same iso9660 CD and
 access the files that way.

This probably applies generally to similar Audio players, rippers, i.e. that
 thay dont have to mount a CD, and can handle file systems that cant be mounted
 normally in ubuntu. (open to correction here). 

I just checked this: 

 - with a music CD (a bought one) the songs show as *.ogg (vorbis ?) 
  when extracted by Sound Juicer. 

  - and on an iso9660 CD containing mp3 music files. (same songs converted
 to mp3 in an Apple Mac, itunes, and saved to CD (not as an image). Mounts normally. 

[B]3. In the same way, you may be able to access the image file (the .iso ) 
just by selecting the image  with your Audio disc player or ripper 
(i.e. you may not need to mount it ). Worth a try.
[/B]
4. If not, you need to question the source of the original ".iso" image, 
and what might be the file system involved in the process. Could be 
an image from Windows, MacOSX etc. Not sure if you compiled a selection by
 extracting, or whether you just downloaded the .iso. 

If you could mount the original CD/DVD, then you should be able to 
loop mount the image, using the same file system type.

5. I dont use Audio much in ubuntu, so there may be other packages 
that might help.

Getting late here too now 3:10 am.
=====

---

### Post by ToohTaah on 2007-03-10
Hope it is not too late to ask you a question...

What kind of iso file you are trying to mount (vcd or dvd)?

---

