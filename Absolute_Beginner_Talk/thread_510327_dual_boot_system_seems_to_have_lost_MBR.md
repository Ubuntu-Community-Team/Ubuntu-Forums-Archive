---
title: "dual boot system seems to have lost MBR"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by MikeSz on 2007-07-26
During a recent storm, I seem to have lost the MBR on a hard disk on a friends computer.  It has XP and Ubuntu 6.06.  I know the hard disk is fine as I can boot using the live CD and explore the drive - everything is there as it should be.  I have read a couple of threads about how to restore GRUB and I have a couple of questions - 

1) none of them refer to a dual boot and whether you can simply just reinstall GRUB and have everything back the way it was.

2) The walkthrough asks me to go through terminal and enter 'mount -t ext2 /dev/hda7 /mount/hd'  

  2) (a) - firstly, I thought ubuntu uses ext3 so shouldnt it be that rather than ext2?
  2) (b) - I have no idea how the drive is mapped - is it hda1, hda7 or what!  How do you find        out?

If anyone could help that would be great - im hoping its just a simple fix for this :)

---

### Post by Cypher on 2007-07-26
Yes, as long as all the data is intact, restoring GRUB should be enough.

I'd suggest checking out [SuperGrub]("http://supergrub.forjamari.linex.org/") to do some of the heavy lifting for you..

---

### Post by cek on 2007-07-26
1.  Mount should be able to determine the type for ext2/ext3, so the -t option is probably unnecessary.

2.  With access to the HD, have a look at /etc/fstab -- this file contains the mapping for partitions/mount points, look for the /boot mount point and note its /dev/hd* designation to find the necessary partition.

---

### Post by starfry on 2007-07-26
If everything on the hard drive is fine (including the grub files being present in /boot/grub) and you have an alternative means of booting using grub (such as with a live cd) then you can do this...

This assumes the hard drive in question is "hda", that the "/boot" area is found on /dev/hda0 and that the machine normally boots from hda.

boot into Grub with the live CD. When it shows the menu, press C for a grub command line. Do not boot the OS: press C for a grub command line.

type

root (hd0,0)
setup (hd0)
quit

then reset your machine. It should boot...

---

### Post by MikeSz on 2007-07-26
> **starfry said:**
> If everything on the hard drive is fine (including the grub files being present in /boot/grub) and you have an alternative means of booting using grub (such as with a live cd) then you can do this...

This assumes the hard drive in question is "hda", that the "/boot" area is found on /dev/hda0 and that the machine normally boots from hda.

boot into Grub with the live CD. When it shows the menu, press C for a grub command line. Do not boot the OS: press C for a grub command line.

type

root (hd0,0)
setup (hd0)
quit

then reset your machine. It should boot...

Unfortunately, I tried to re-boot from the live cd and I only have the usual menu options - pressing C doesnt seem to do anything no matter when i press it - the only option erally is the top one - start or install ubuntu - il stay on the web with a laptop so I can keep re-booting the broken machine.  Am I missing something here?

---

### Post by MikeSz on 2007-07-26
concerning supergrup - this machine unfortunately doesnt have a writer - only a DVD reader drive :(

I do have a USB stick - can I use supergrup and boot from the usb drive or is that too messy?

---

### Post by MQMike on 2007-07-26
Get into Ubuntu with the Live CD,
get a Terminal,
type sudo grub,
Presss Enter,
then type what starfry said:

root (hd0,0)
setup (hd0)
quit

and test it

---

### Post by MikeSz on 2007-07-26
got a message saying "Error 17: Cannot mount selected partition"  after typing 'setup (hd0)'

---

### Post by MQMike on 2007-07-26
Sorry,

the line:

root (hd0,0)

should actually be

root (hdx, y),

where hdx is the hard drive Ubuntu is on,and y is the partition containing Ubuntu.
Ex.: If Ubuntu is on the second hard drive, the 3rd partition, that would be
(hd1, 2)
(Note:  IN GRUB, counting drives and partitions starts from zero.)

Where is your Windows XP (drive and partition)?
Where is your Ubuntu (drive and partition)?

---

### Post by MikeSz on 2007-07-26
Hi MQMike - alas, this is what I dont know and what's been confusing me...

I installed XP first on the computer's only hard disk drive (which is by the way, a serial ATA - does that make a difference?).  Once XP was on, I then set ubuntu up on another partition.  As such, an 80Gb hard disk is split into two partitions with XP on one, and Ubuntu on the other, although I have no idea what hda numbers they are!

---

### Post by MQMike on 2007-07-26
Sounds like XP is on (hd0, 0)
(first hard drive, first partition)

Let's foind out where Ubuntu is.
Get a Terminal
 type
sudo fdisk -lu
(-lu is "l" as in "list," and "u" as in "units.")

then can you print that here or type it or just see what partition Ubuntu is on,
like hdax,
what is x where that "Linux" is?

---

### Post by MQMike on 2007-07-26
(BTW, no it doesn't matter that it is a SATA HD -- that's the best!)

---

### Post by MikeSz on 2007-07-26
ive got /dev/sda1 which is linked as HPFS/NTFS and then I seem to have /dev/sda2 which is tagged as Linux.  Then Ive got sda3 which is extended and sda5 which is linux swap/solaris

---

### Post by MQMike on 2007-07-26
OK, then the root statement should be:

root (hd0, 1)
setup (hd0)
quit
$exit

close out,
remove CD,
and
re-boot to test it

(That is, Ubuntu is on sda2 = (hd0, 1) = first hard drive, second partition.)

---

### Post by MikeSz on 2007-07-26
nope - system wont boot.  It just hangs on Nvidia Boot agent just after post and verifying DMI pool data....

It did seem to work though what you suggested - got a series of "success" messages

---

### Post by MQMike on 2007-07-26
Yes, it sounds like GRUB got re-installed ok, but I don't know now what this other stuff is.
So, you couldn't boot into either XP or Ubuntu, I take it.
I'm puzzled now by that message you got.  Sorry.

---

### Post by MikeSz on 2007-07-26
me too - sounds like an MBR failure by the looks of it - ive checked the BIOS boot sequence and all seems in order - there are no problems with the hard disk and I can access its contents from the live cd.  Therefore I cant think what else it might be!!  Might just bite the bullet and reinstall both os's from scratch but id like to keep that as a last resort...

---

### Post by MQMike on 2007-07-26
In terms of the GRUB stuff, you have a most simple system, one HD, two partitions, Windows on first, then Ubuntu – the simplest setup.  GRUB should work in a heartbeat.  It seems something got broken in the lightening!  Either software got very rearranged or even a hardware damage somewhere.
Let us know what you do or find out, and maybe someone will chime in here re: that message you got back.

For your future reference, or just for fun, here’s a How-To I wrote:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(there are several posts there with various topics in them, but the first and second posts are the basic tutorials)

The classic, of course, is Herman’s bigpond,
bigpond, home:   [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
(especially the GRUB page)

But, as we’ve said, the GRUB part doesn’t seem to be the problem . . .?

---

### Post by starfry on 2007-07-26
Have you googled?

I just found this:
Grub error 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the
filesystem type cannot be recognized by GRUB.

And this:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)


And this:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

I hope these help you.

---

### Post by MikeSz on 2007-07-26
Would seem the boot sector is fried.  Having tried to install ubuntu from scratch, although it installed seemingly ok, on restart, I got the same freeze on "NVidia boot manager" just after "Verifying DMI..."  It will still boot from the live disc and I can still see the hard disk but for some reason it just refused to boot from it.

---

### Post by MQMike on 2007-07-26
Yes, it doesn't sound like any booting problem I've run into with GRUB.  The GRUB stuff *should* just work.
Keep us posted.  Maybe someone will chine in here with specifics re the message you are getting.

---

### Post by MQMike on 2007-07-26
Thought – Given what you said happened in the storm, and the sounds of your error message (Nvidia boot . . .), it just occurred to me that perhaps re-setting the BIOS of the motherboard might help.  Maybe some settings there (esp for boot disk) might have gotten zapped.  I really have no clue, just a long shot.
You would need to locate & follow the instructions for re-setting BIOS for your motherboard.  I only know how to do it with recent Intel boards (with the configuration jumper).  That process would reset all settings back to their Default values, usually safe values, but THEN you may have to go into BIOS and re-set any that require special, non-default settings that you use/require (like, Enable Boot from USB, as an example).  If you know the motherboard model number/make, the maker’s website would have instructions.

---

### Post by MikeSz on 2007-07-27
Thanks for that and for the help thus far - ive tried going into bios and restoring defaults which didnt make any difference at all.  There is also a backup bios which you can boot from and ive tried using that one though it seems exactly the same as the first.  I might just take the battery out later (usually does the trick in re-setting a bios) and see what happens from there but at which point im stuck.

As an afterthought, i might take the hard disk out and try it  in another computer (I have a spare pc that I could plug the hard disk into) and see if I can install ubuntu on it.  Would at least pin down whether its the hard disk or something on the motherboard.

---

### Post by MQMike on 2007-07-27
Both very good ideas -- 
remove battery,
test hard drive, on different motherboard.

Keep us posted,

Mike

---

### Post by Sbarton on 2007-07-27
Just out of curiosity have you considered reinstalling the XP mbr (fix/mbr) via the XP CD to see if that works? If it does work you can try 'Grub' again, though it does'nt seem grub is the problem! Could be hardware problem!
Anyway good luck.
regards

---

### Post by MikeSz on 2007-07-27
I hadnt thought of that Sbarton - its a good idea though so I will give it a go!  

Many thanks and il let you know what happens...

---

