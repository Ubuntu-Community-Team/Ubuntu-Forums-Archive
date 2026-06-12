---
title: "lost file system?"
date: 2005-07-18
forum: Absolute Beginner Talk
---

### Post by Zaare on 2005-07-18
I wanted to increase the size of the Linux partition, so I used Partition Magic to free 5GB from a Windows partition. All went well. Then I tried to add the 5GB to the Linux partition I got an error message (with an OK-button). I klicked the OK-button and then Partition Magic freezed. I shut it down by "force".

When I tried to restart the computer I got:
> Grub loading, please wait...
error 17
I searched and saw that in most cases it was suggested to start the computer with Windows CD, choose repair and run "fixmbr". I did that and when I restarted the computer I got the message:
> No operating system found
(Or something like that. I don't remember the exact words)

Now, I've used Ubuntu Live Cd to start my computer and I can mount my two Windows partitions and access them with no problems.
But I can't mount the Linux partition:
> $ sudo mount -t ext3 /dev/hda3 /media/linux/
mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I'm not really surprised about that. And "fdisk" says:
> 
$ sudo fdisk -l 
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         637     5116671    7  HPFS/NTFS
/dev/hda2             638        2979    18812115    f  W95 Ext'd (LBA)
/dev/hda3   *        2980        4198     9791617+  83  Linux
/dev/hda5             638        2922    18354231    7  HPFS/NTFS
/dev/hda6            2923        2979      457821   82  Linux swap / Solaris
So the linux partition (hda3) can't be all lost, right?
At last a friend told me about "gpart". I installed and ran it:
> $ sudo gpart /dev/hda3

Begin scan...
Possible partition(Linux swap), size(447mb), offset(4777mb)
Possible partition(Linux ext2), size(9562mb), offset(5224mb)

*** Fatal error: dev(/dev/hda3): seek failure.


Any ideas on what I should do? If it's not possible to save the system, I can sattle with just an access to my files on the Linux partition so I can copy some files I really wouldn't want to lose.

---

### Post by JPatrick on 2005-07-18
Reinstall Ubuntu.

---

### Post by Zaare on 2005-07-18
I see... Thank you... Since that would mean I lose every file I'm trying to save, I'll use it as a last option.
Does anyone have another suggestion?

---

### Post by Wolki on 2005-07-18
[QUOTE=Zaare]I see... Thank you... Since that would mean I lose every file I'm trying to save, I'll use it as a last option.
Does anyone have another suggestion?[/QUOTE]

You can try sudo fsck /dev/hda3 to try to fix the errors.

These are often symptoms of a hard disk error coming up. I suggest using the vedor check utility.

---

### Post by Zaare on 2005-07-18
Thanks for the reply Wolki. This is what I get in response:
> 
$ sudo fsck /dev/hda3
fsck 1.35 (28-Feb-2004)
e2fsck 1.35 (28-Feb-2004)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

It seems fsck thinks the file system should be ext2, but I'm certain it is/was ext3.
I did try the command at the end of the quote:
> 
$ sudo e2fsck -b 8193 /dev/hda3
e2fsck 1.35 (28-Feb-2004)
e2fsck: Bad magic number in super-block while trying to open /dev/hda3

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


[QUOTE=Wolki]
These are often symptoms of a hard disk error coming up. I suggest using the vedor check utility.
[/QUOTE]
What is vedor check utility?

---

### Post by damonw5 on 2005-07-18
[QUOTE=Zaare]Thanks for the reply Wolki. This is what I get in response:

It seems fsck thinks the file system should be ext2, but I'm certain it is/was ext3.
I did try the command at the end of the quote:



What is vedor check utility?[/QUOTE]
 I think Wolki meant "vendor" check utility. You could download the Ultimate Boot CD at [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) and use the appropriate tool to check your hard drive. However, you must know which manufacturer it is (not the computer, but the hard drive itself.)

---

### Post by juhis on 2005-09-08
I have the same problem after messing up with Partition "Magic" (Partition Tragic I say: how can it be so hard, just writing and deleting some information to different parts of disk? I'm getting cynical). GRUB 17 errors while booting and stuff. For me it seems that fdisk and PM can read the linux root partition but fsck gives the same magic number 8193 -error.

Sure there's  no other way than that vendor -cd? Can I use it from Windows?

Could I somehow reinstall Ubuntu over the old one, my old swap and /home- partitions are alive and well (at least they are able to be mounted). 

Of course best would be to somehow recover the whole old ubuntu with all thousands of packages (that took ages to get to work).

I found this rather interesting, might-be-useful link (according to e2fsck):
[http://www.die.net/doc/linux/man/man8/e2fsck.8.html](http://www.die.net/doc/linux/man/man8/e2fsck.8.html)

juhis 
(indian-name: he who hates all operation systems and computers in general)

p.s. I think I've seen somewhere in this forum messages saying that 2 gb is enough for windows (XP) - nope! With lots of programs, which all need at least some space from C:\ -drive, and XP needingh some swap space, it would be wise to reserve enough space for it (4-11 gb). That's why I changed my partitions in the first place, with quite unpleasant results. Well, at least it seems most of my important files are safe. Just don't have the energy to fix things anymore. 
Ok, enough of my yaking, I'm happy with what I have!

p.s.s. Great forum!

---

### Post by Wolki on 2005-09-08
[QUOTE=juhis]Sure there's  no other way than that vendor -cd? Can I use it from Windows?

Could I somehow reinstall Ubuntu over the old one, my old swap and /home- partitions are alive and well (at least they are able to be mounted). [/quote]

The vendor cd is only to check for hardware fault, it'll likely not really help you with fixing errors. Last time I had such an error it meant goodbye to my hdd, in your case it's probably just Partintion Magic screwing up.

Reinstalling Ubuntu should work in this case, be careful to select format for the root drive, but not for /home while at the partition step.

---

### Post by tonysathre on 2005-09-08
try reinstalling just grub before you reinstall the whole system, to do this put in the install cd press enter at the boot prompt, let it configure, when it gets to the partition part go back to the main menu and go down to where it says reinstall grub and select it

---

### Post by Kyral on 2005-09-08
I know exactly why this is borked up right now. You see, you are allowed to resize a Linux partition, *as long as you don't change its starting point on the drive.* I'm willing to bet that Windows was the first partition on the drive, and when you took space offa it, you moved the Linux partition "backward" to take it.

---

### Post by juhis on 2005-09-12
[QUOTE=Kyral]I know exactly why this is borked up right now. You see, you are allowed to resize a Linux partition, *as long as you don't change its starting point on the drive.* I'm willing to bet that Windows was the first partition on the drive, and when you took space offa it, you moved the Linux partition "backward" to take it.[/QUOTE]

Yes, exactly! I thought the grub could somehow find out where the root-directory is and update partition table (or that some program could do that). Well, it's the same information but in the different part of the harddisk, isn't it...?

Partition magic didn't warn much about moving linux root-partitions...
Seems like I have to install Ubuntu again, installCD couldn't fix grub.

juhis

---

