---
title: "Absolute Linux newbie neeing help mounting Windows FAT32 partitions"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Jabbadahut on 2006-03-21
Hello, fellow Ubuntu users.  This is my first time using Linux.  I am having trouble mouting my FAT32 partitions on my primary hard disk which has windows on it.

Here's how I have my disks set up, to give you an idea:

Primary hardisk is 120 GB total split up into 6 partitions, each one for different stuff, like programs, mp3 files, games, etc. - each one is approx 20 GB, give or take.

Second hardisk is same size, but with Ubuntu AMD64 bit version - using the default hard disk setup that the OS uses upon installation.

When I look in the filesystem under /dev, I notice several of my  partions there.  I have hda1 (windows partition), hda2, hda5, hda6, hda7, hda8, & hda9.  Why they aren't numbered 1 - 6 respectively, I have no idea, but whatever, lol. :)

I read the instructions on Wiki about mounting Windows partitions, and I was able to mount my "c: drive" fine (hda1).  Then I tried mounting hda2, making sure that I substituted the appropriate syntax, but I get an error.

This is what I typed:

mkdir /media/d:\programs
sudo mount /dev/hda2 /media/d:\programs -t vfat -o iocharset=utf8,umask=000

Then this error:

"mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

Whaa??  Okay, whatever.  I am completely clueless to Linux commands, but out of curiosity, I tried "dmesg | tail", then I get this message:

"[   80.141274] Bluetooth: RFCOMM ver 1.5
[   80.141283] Bluetooth: RFCOMM socket layer initialized
[   80.141295] Bluetooth: RFCOMM TTY layer initialized
[   82.239552] eth1: no IPv6 routers present
[   96.018434] ISO 9660 Extensions: Microsoft Joliet Level 3
[   96.025168] ISOFS: changing to secondary root
[ 2395.914584] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 2615.909127] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!"

I think the last two messages only pertain to my problem though.  I didn't try the other partitions, thinking that I'd get the same problem.

What's going on?  Any help would be much appreciated.

---

### Post by meborc on 2006-03-21
hi, hope you enjoi ubuntu...

EDIT: i suggest you try this page [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) as you have seen the wiki already

EDIT2: try **sudo mount /dev/hda2 /media/d:\programs -t vfat -o umask=000** it might do the trick :)

---

### Post by AtinLango on 2006-03-21
> When I look in the filesystem under /dev, I notice several of my partions there. I have hda1 (windows partition), hda2, hda5, hda6, hda7, hda8, & hda9. Why they aren't numbered 1 - 6 respectively, I have no idea, but whatever, lol.


hda1-4 are reserved for primary partitions, thats why extended start at 5.

> This is what I typed:

mkdir /media/d:\programs
sudo mount /dev/hda2 /media/d:\programs -t vfat -o iocharset=utf8,umask=000


I see you are making it complex, why not replace "d:\programs" with just "programs" and use something like 

```

sudo mkdir /media/programs
sudo mount /dev/hda2 /media/programs vfat user,umask=000 0 0
```

---

### Post by jbinto on 2006-03-21
```

"mount: wrong fs type, bad option, bad superblock on /dev/hda2,
missing codepage or other error
([B]aren't you trying to mount an extended partition,
instead of some logical partition inside?)[/B]
```

This could be a dead giveaway.

Something I just learned recently, as I was forced to use fdisk:

A computer can only have four primary partitions. To go beyond that, one must use an extended partition, which can be subdividied into logical partitions.

Consider a 100GB drive with four primary partitions of 25GB. No further partitions would be allowed. The windows equivalents would be c:, d:, e:, f:. The linux equivalents would be hda1, hda2, hda3, and hda4.

Then consider a 100GB drive with one primary partition of 25GB (c: in windows, hda1 in linux), and one extended partition of 75GB (hda2 - but no windows equivalent). One could subdivide the 75GB extended partition into three 25GB logical partitions (d:, e:, f:, or hda5, hda6, hda7), seven 10GB logical partitions, seventy-five 1GB logical partitions, etc etc. Or, the most likely situation, one big 75GB partition.

The confusion arises when you have a /dev/hda2 which is 75GB, and a /dev/hda5 which is 75GB. Both are the same drive, but hda2 is the extended partition which is not directly accessible and hda5 is the logical partition which is.

The point I'm trying to make here, is one cannot access extended partitions directly. Windows just hides that hda2 away from you, and their setup program automagically deals with primary/extended/logical. That 75GB hypothetical I brought up can only actually be accessed through their logical drives - not via hda2 but via hda5,6,7 etc.

I could be entirely wrong in diagnosing your problem, but please give us the output of

```
fdisk -l
```

when run as root. I would wager your windows partition is actually hdx5, as a logical subpartition of hdx2. (where the x in hdx is your drive)

And as one previous poster mentioned, it would be a good idea to get rid of the "d:\". Not only is it unnecessary, since linux uses a different path paradigm (no drive letters, and / instead of \), it could cause problems when being typed into the shell as it may interpret \ to mean something you don't want it to mean. I doubt it is the root of your problems, though.

Hope you were able to get something useful out of this rather longwinded explanation.

---

### Post by Jabbadahut on 2006-03-21
Thanks for your input, guys.  I'm not there yet, but I am making progress (I think, lol). :)

Looked at that link that was mentioned, and also did "sudo fdisk -l", and here's what I got:

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/hda2            2551       14945    99562837+   f  W95 Ext'd (LBA)
/dev/hda5            2551        5100    20482843+   b  W95 FAT32
/dev/hda6            5101        7650    20482843+   b  W95 FAT32
/dev/hda7            7651       10200    20482843+   b  W95 FAT32
/dev/hda8           10201       12750    20482843+   b  W95 FAT32
/dev/hda9           12751       14945    17631306    b  W95 FAT32

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

So yeah, hda2 is an extended partition - exactly why I got that error.  I forgot about Windows doing that.  That link was very helpful, as I was able to mount each drive that I needed to, according to how it was identified by Ubuntu.  Now all I need to do is implement those so they mount automatically each time I start Ubuntu.  I first edited the /etc/fstab file according to the web page's instructions to get my c;\windows partition mounted first.

However, I noticed during bootup that I got a "failed" message when the system attempted to load my Windows partition.  So, I looked at the file, and noticed In hindsight I made a stupid typo mistake on mounting my windows partition.  I forgot to replace "partitionname" with the one I named it.  Okay, no problem, I'll just go back and edit the file again, right?  Wrong.  For some reason, I cannot edit the /etc/fstab file, even when typing the appropriate command.

"~$ sudo -i
~# sudo cp /etc/fstab /etc/fstab_backup
~# sudo gedit /etc/fstab

(gedit:8576): Gtk-WARNING **: cannot open display:"

This is getting tedius, lol. :)  Oh well, at least I had no trouble setting up the OS as far as hardware & setting up my  Comcast internet. :p

---

### Post by ducttapemasterJ on 2006-03-21
ok this is good timing, cause I too am very new to linux and am having similar, but slightly different problems.
I too am trying to mount a partition that I can share between linux and Win XP.  I entered the following into /etc fstab file:

/dev/hdd5         /osshare vfat iocharset=utf8,umask=000 0 0

now when I restart the computer, it acts as though it did, infact, mount.  If I enter 
'sudo mount /osshare'  it tells me that osshare is already mounted...great... the problem is, it doesn't appear on my desktop or in 'computer' under "places".
I ran 'fdisk -l' and it came up with this entry for that drive:

/dev/hdd5            2551        4865    18595206    b  W95 FAT32

Then, I tried to go into the /osshare directory through the terminal.  Now I have one file on that drive for test purposes, and the file is just a text document of like one page.  I typed 'ls /osshare' into the command line and it listed the file as: "System Volume Information" which I have no idea what that means but maybe that helps...

  Now this partition DOES show up in Win XP, but not in Ubuntu desktop and I have no idea why.  Now like I said Im completely a newbie, and maybe there's something else Im supposed to do.  If anyone knows what Im missing let me know. 
Thanks a ton!

---

### Post by meborc on 2006-03-21
[QUOTE=Jabbadahut]I cannot edit the /etc/fstab file, even when typing the appropriate command.

"~$ sudo -i
~# sudo cp /etc/fstab /etc/fstab_backup
~# sudo gedit /etc/fstab

(gedit:8576): Gtk-WARNING **: cannot open display:"
[/QUOTE]

yeah, i have had the same... gedit sometimes just doesn't get it... but there is a workaround... :mrgreen: 
**sudo nano /etc/fstab**
it is a text-editor in terminal... just conrtol+x to save in the end...

---

### Post by Princey on 2006-03-21
[QUOTE=ducttapemasterJ]ok this is good timing, cause I too am very new to linux and am having similar, but slightly different problems.
I too am trying to mount a partition that I can share between linux and Win XP.  I entered the following into /etc fstab file:

/dev/hdd5         /osshare vfat iocharset=utf8,umask=000 0 0

now when I restart the computer, it acts as though it did, infact, mount.  If I enter 
'sudo mount /osshare'  it tells me that osshare is already mounted...great... the problem is, it doesn't appear on my desktop or in 'computer' under "places".
I ran 'fdisk -l' and it came up with this entry for that drive:

/dev/hdd5            2551        4865    18595206    b  W95 FAT32

Then, I tried to go into the /osshare directory through the terminal.  Now I have one file on that drive for test purposes, and the file is just a text document of like one page.  I typed 'ls /osshare' into the command line and it listed the file as: "System Volume Information" which I have no idea what that means but maybe that helps...

  Now this partition DOES show up in Win XP, but not in Ubuntu desktop and I have no idea why.  Now like I said Im completely a newbie, and maybe there's something else Im supposed to do.  If anyone knows what Im missing let me know. 
Thanks a ton![/QUOTE]

Did you make the directory osshare? The first step in mounting your drive is first create a directory whether it's your home directory or in mount before you edit your fstab file. For example and using your drive letter as an example:

> sudo mkdir /osshare

That's when you edit your fstab file by first backing up typing the command
> sudo cp /etc/fstab /etc/fstab_backup

Once you've backed it up, you then open your fstab file by enter the information as typed. Copy and paste will work in that case seeing I'm using your exact settings:
> sudo gedit /etc/fstab now type the information here:
> /dev/hdd5 /osshare vfat umask=000 0 0

Save the document and either reboot, or type 

> sudo mount -a and press enter

P.S Seeing your drive is already mounted you will have to unmount the drive first before following the above steps or removing the entries you typed in at your first attempt then rebooting so as to prevent the drive from being mounted. Here's the command to unmount the drive before following the steps outlined above:

> sudo umount /dev/hdd5

Post back your results.

---

### Post by ducttapemasterJ on 2006-03-21
yea I started over and followed all those steps exactly and came out with the exact same results as before.  It still acts like its mounted, but I don't see it on the desktop.  I did just notice something else interesting, however, when I 'sudo fdisk -l'  I just noticed that the hard drive that this partition is on seems to me oddly partitioned.  When I originally partitioned it, it was supposed to have 2 x 20 Gig partitions.  However, upon fdisk I get the following readout for that drive: 

Disk /dev/hdd: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        2550    20482843+   7  HPFS/NTFS
/dev/hdd2            2551        4865    18595237+   f  W95 Ext'd (LBA)
/dev/hdd5            2551        4865    18595206    b  W95 FAT32

now before I was only focused on hdd5, cause I saw FAT32 (which is what I formatted the second partition in, so I figured that was what I was looking for), however, what's with hdd2? 
like I said Im a newb so I don't know what (if anything) that stuff means, but maybe yall know what's going on :)
Thanks!

---

### Post by Princey on 2006-03-21
First, let me help you out here with your question then point you to where your problem might be.
> now before I was only focused on hdd5, cause I saw FAT32 (which is what I formatted the second partition in, so I figured that was what I was looking for), however, what's with hdd2?

hdd2 is your extended partition. When a drive is partitioned (I think this was covered earlier on but I'll see if repeating helps). It's split into a primary partition and an extended partition. This extented partion is then used as a logical drive. You can have several logical drives in an extended partition. Windows by default hides the extended partition so all you see are the logical drives within the extended partion e.g drive D:, drive E:. However, Linux will show all your drives extented, primary or logical. The fact that "Ext'd (LBA)" appears for hd2 simply says that it's the extended partition, that's why the next logical drive is hd5 as linux starts numbering logical drives within an extended partition from hd5. That's why, it's nothing to worry about. Now, on to your most likely mistake.

> yea I started over and followed all those steps exactly and came out with the exact same results as before. It still acts like its mounted, but I don't see it on the desktop.

You're expecting the drive mounted to show as a drive on the desktop like how say knoppix does it from the live CD. That's not how ubuntu treats your mounted FAT32 or NTFS drives. Remember you typed mkdir ossshare? Well, that's a FOLDER not a drive. Technically it is. But Ubuntu would show it as a folder. The drive is mounted and can be seen in your home directory. If you go to your home directory, it should show a folder there as osshare. That's where it can be found. If you wanted it on your desktop then you'd have to create a shortcut to it.  I'm not sure if you're running gnome or kde but I think right clicking on the folder allows you to create a shortcut to the desktop in both desktop environments. Why don't you go to the terminal and type the following:
> cd osshare

now check and see if the test file doesn't show up there by typing either dir or ls to do a folder listing. Let us know what happens.

---

### Post by AtinLango on 2006-03-21
[QUOTE=Princey]Remember you typed mkdir ossshare? Well, that's a FOLDER not a drive. Technically it is. But Ubuntu would show it as a folder. The drive is mounted and can be seen in your home directory. If you go to your home directory, it should show a folder there as osshare. That's where it can be found.[/QUOTE]

If Jabbadahut followed the instructions, as (s)he says, then (s)he typed:

```
sudo mkdir /osshare
```

not

```
mkdir osshare
```

So, osshare could not be in his home folder.

---

### Post by Princey on 2006-03-21
[QUOTE=AtinLango]If Jabbadahut followed the instructions, as (s)he says, then (s)he typed:

```
sudo mkdir /osshare
```

not

```
mkdir osshare
```

So, osshare could not be in his home folder.[/QUOTE]
Sorry AtinLango but that wasn't directed to Jabbadahut. ducttapemasterJ requested help on a similar issue, hence my post. You said that my command towards the end would not yield the folder in home. You're wrong. I  just did it by creating a new folder called osshare. Here's the output to validate my findings:

> princey@MCES:~$ sudo mkdir osshare
Password:
princey@MCES:~$ ls
amsn_received  Desktop    kubuntu-packages-jriddell-key.gpg    osshare
cxoffice       Downloads  kubuntu-packages-jriddell-key.gpg.1  sources.list


As you can see, the folder was created in the home directory even if sudo was used. sudo just gives administrative priviledges, not force a root formation of the folder as no leading directory was specified in the command like sudo mkdir /media/osshare

---

### Post by ducttapemasterJ on 2006-03-21
aaahh
now things are beginning to make sense.  Yes, I was expecting osshare to show up as a drive on my desktop, but now I see the error in that assumption.  Thanks also for re-explaining the extended drives concept.  I had read your earlier post, but reading it again in different words helped it make more sense to me. 
Anyway osshare is in my home directory and usable.  Thanks a ton for your help!

---

### Post by Princey on 2006-03-21
[QUOTE=ducttapemasterJ]aaahh
now things are beginning to make sense.  Yes, I was expecting osshare to show up as a drive on my desktop, but now I see the error in that assumption.  Thanks also for re-explaining the extended drives concept.  I had read your earlier post, but reading it again in different words helped it make more sense to me. 
Anyway osshare is in my home directory and usable.  Thanks a ton for your help![/QUOTE]

Glad to hear that things worked out for you. That's what we do here, help each other out. Glad to be of service. Have fun using linux!!!:mrgreen:

---

### Post by ducttapemasterJ on 2006-03-21
ok I lied :p Im not quite done squeezing you experts for information on this topic. :)
Alright so osshare shows up as a folder just fine, and I can see the same partition as a drive in windows just fine, however the files from each operating system only show up on its own OS.  For example, I booted in linux and saved a word document to osshare as "test1.doc" (saved as windows XP document).  Then I rebooted into windows, went to the same drive, and the file wasn't there.  Then I opened office and saved "test2.doc" on the same drive, then I rebooted back into ubuntu and the only file there was still just "test1.doc" - no "test2.doc".
Any ideas why the operating systems aren't able to see each other's files on the same drive?  (the drive is FAT32)
 thanks!

---

### Post by Princey on 2006-03-21
First of all, I'm no expert when it comes to Linux. Yes, I could say that for windows as I run my own pc repair shop and work as a system admin for a company. I'm still learning linux like you through the posts of others and me posting when I get stuck. Sometimes, through tinkering around I find the answer myself, other times I have to rely on someone else's advice or experience to bail me out. The good thing about it is that I keep learning everyday.

Putting that aside, I really don't have that problem on my linux box sharing with the windows partition on this computer. My music or documents show fine both ways wherever I save. However, I have tried using another fat32 partition to replicate your situation and somehow, I don't get the problem you're getting. However, I want to suggest this: if you go to the terminal and type > cd osshare press enter then type > ls what do you get as the output? Does it list one file or not? Also, try to see if the files aren't hidden (though I doubt it) but it's worth a try. Maybe someone more experienced than I am can help you out there.

---

### Post by AndrewCaul on 2006-03-21
It sounds like it didn't mount properly, so just appeared as an empty folder.
Try typing (I think) ```
mount -a
``` in the terminal and post the output here. You may have made a typo in fstab.

---

### Post by ducttapemasterJ on 2006-03-21
alright everything is working now.  
in the course of mounting and unmounting things as I tried various solutions yesterday I ended up having things mounted oddly.  Its all straightened out now though.  
Thanks again for all yall's help!

---

### Post by Jabbadahut on 2006-03-22
Yeah, I got my problem solved too.  Thanks everyone for your help.

---

### Post by Princey on 2006-03-22
Glad to hear that you two have finally succeeded.

---

