---
title: "Ubuntu 10.04 Won't Boot - Missing Operating System"
date: 2010-09-29
forum: Apple Hardware Users
---

### Post by macfreak on 2010-09-29
Hello World,

I'm trying to run Ubuntu 10.04 on an external USB hard drive so that I can boot into the same Ubuntu installation from both Windows machines and also Intel Macs. I tried following the instruction at [http://mac.linux.be/content/how-create-ubuntu-live-usb-both-mac-and-pc](http://mac.linux.be/content/how-create-ubuntu-live-usb-both-mac-and-pc) , but my setup varies slightly from the intentions of that article. I was able to get a USB thumb drive to boot using those instructions, but unfortunately my new external USB drive keeps showing a Missing Operating System error and It never seems to load GRUB.

Unfortunately the CD-ROM drive is broken on the Mac Mini I am using for development, so I cannot just boot into Ubuntu from the CD and follow standard installation procedures. The CD does load correctly but read errors happen during installation as a result of the damage to my CD-ROM drive. It is unfortunately not the CD. I promise - sounds bogus but true. I think the kid I was living with stuck something in the drive' cause sometimes it makes a wretched noise... but that's beside the point.

I've managed to use Oracle's VirtualBox to install Ubuntu onto a physical HD, as detailed under private-methods in their user manual. Everything seems to work when I try to boot the drive using rEFIt until you choose the linux icon... the it just says Missing Operating System - and stays there. What is strange, is that VirtualBox loads Ubuntu perfectly fine from the external HD. I imagine that if I had a windows machine to test it with, a windows machine would likely boot perfectly as well. Unfortunately I am using an intel mac - and cannot for the life of me get the HD to boot.

I've also tried the instructions for reinstalling grub-legacy from the recovery console listed here: [http://ubuntuforums.org/showthread.php?t=1549174&highlight=missing+operating+system](http://ubuntuforums.org/showthread.php?t=1549174&highlight=missing+operating+system)

I've tried grub-efi... I've scoured the internet and seem to be the only person with this issue. I am running a first generation intel mac mini. Nothing results differently from "Missing operating system" or a forever blinking cursor.

Partition layout:
Internal HD
- 60 GB Macintosh HD

External USB HD
- 4.2 MB free space
- 64 MB rEFIt boot partition (HFS+)
- 64 GB Ubuntu root partition (ext4)
- 400GB Data (ext3 - encrypted)

The only difference between the way I tried to install Ubuntu and the first article I presented, is that I omitted the boot partition because I want rEFIt to only show one Linux option, as opposed to a Linux and a Legacy OS option. Additionally I have an encrypted data drive, but it'S a separate mount point and not related to the home folder - so it shouldn't affect the system.

I'm at my wits end. Please help.
Thanks for your time!
Eliot Simcoe

---

### Post by P4man on 2010-09-29
Disclaimer: I know nothing about macs and EFI. 
That said:
> 

The only difference between the way I tried to install Ubuntu and the first article I presented, is that **I omitted the boot partition **because I want rEFIt to only show one Linux option, as opposed to a Linux and a Legacy OS option

You need that partition! I dont know if you can configure it like grub (I suspect you can) but you cant expect it to work by just leaving it out ?

---

### Post by macfreak on 2010-09-30
I only omitted the GRUB boot partition, because GRUB can be installed on the MBR and the /boot directory can live on the Ubuntu root partition. The Ubuntu OS partition loads correctly in VirtualBox (Including the GRUB menu), so why would this matter for booting on a mac? Are you saying that a separate GRUB boot partition is required? I have a separate rEFIt boot partition, but thought a separate GRUB boot partition was optional.

---

### Post by P4man on 2010-09-30
You can only have one MBR per drive. The way I read that tutorial is that it tricks by installing rEFIt on a "shrunk" stick, then installs grub's MBR before that (why you need that 4.2 MB I guess). I dont really understand the details, but Im sure he made that how to like that for a reason. 

Of course regularly, grub doesnt require its own partition, but then it doesnt require rEFIt either ;). Why dont you try to follow the howto to the letter, once that works, see if you can simplify it, but again I doubt he made that complicated for the sake of it.

---

### Post by pindar on 2010-10-01
You won't like this... I also have a mac mini and an external usb disk. I wanted to have the same thing you seem to be going for: boot ubuntu (or any other linux) from an external HD while leaving my interior HD untouched. I searched the forums, followed a half dozen tutorials I found on the web, all to no avail: it doesn't work. Repeat: it doesn't work. I have never been able to boot my mac mini from an external HD. What you **could **try (but this is completely untested):

[LIST=1]
[*]Install ubuntu to your external HD and make sure it's bootable from a windows box.
[*] Install reFIT to your mini
[*]Install bootcamp on your mini. Shrink your main partition and add a new one at the end, something like 300-500 MB will be enough. Format this partition as ext2 and add the bootable flag.
[*] Copy all files from you ubuntu /boot partition to this partition. 
[*] Install grub to this partition. 
[/LIST]
You could then have two grub installations: one on your mini's new partition, and one on your external HD. Both will boot the same system (one from your mac, one from a windows machine), but will have a different boot partition. But it's complex, and you may run into trouble at one point.

---

### Post by macfreak on 2010-10-05
The thing is - I was able to follow the tutorial using a 4 GB USB thumb drive with total success. With my new external 500 GB USB hard drive all I ever get is Missing Operating System. It doesn't even seem to load GRUB. There must be an explanation for this! Someone please help!!

---

### Post by macfreak on 2010-10-06
I've tried the article listed in the head post with success on a 4 GB USB flash drive, but my bus powered external USB HD always ends up with a Missing Operating System error and never loads GRUB. Could this have something to do with my HD being connected with a double ended usb cable for power? What's the fix guys? I'm not giving up!

---

### Post by linuxopjemac on 2010-10-06
Your Mac might not have support for USB booting tjis particular drive in its firmware.

---

### Post by macfreak on 2010-10-06
> **linuxopjemac said:**
> Your Mac might not have support for USB booting tjis particular drive in its firmware.

What does tjis mean?

I was able to boot my Mac Mini without problems into Ubuntu 10.04 on a 4 GB USB Flash Drive as outlined in the first message. Using the exact same method of installation works on my new Iomega bus powered 500 GB USB HD - using a weird USB cable with two large USB plugs on the computer end - but after the install GRUB fails to load on boot and all we get is a "Missing Operating System" message. There are no firmware updates available for my computer.

Might it be possible to install GRUB on the Ubuntu Boot partition (/dev/sda2) instead of the MBR? My boot partition has a mount point of /boot on my Ubuntu system. I'm not sure how this affects things.

This has to be possible. I refuse to accept defeat. Help welcome.

Thanks
Eliot Simcoe

---

### Post by P4man on 2010-10-06
Not sure how this fits in, but it just struck me that windows can only see one partition on a USB stick, but has no such problems on a USB harddisk.

What does windows have to do with this? Well, nothing, but maybe a similar problem exists with refit, or your firmware, and it shows that booting USB stick isnt necessarily the same as booting USB harddrive.

---

### Post by P4man on 2010-10-06
oh and one more thing. Make sure your USB stick is not one infected with U3. Some USB sticks present themselves as a CDrom to windows and load some software to access the rest of the disk. 

u3 enabled sticks are common (sandisk among others usually ship with them) and can NOT boot ubuntu unless you remove that firmware first.

More info here:
[http://en.wikipedia.org/wiki/U3](http://en.wikipedia.org/wiki/U3)

---

### Post by macfreak on 2010-10-07
I'm not sure what I was doing wrong for 6 days, but here is what worked:

Partition the external USB HD using the Ubuntu 10.04 Live CD's installation procedure as follows:
Partition      Format     Size      Mount Point-Function
/dev/sda1    FAT32    64 MB         rEFIt Boot
/dev/sda2    EXT4      64 GB       / - Ubuntu Root
/dev/sda3    SWAP      8 GB       Swap Space
/dev/sda4    EXT3       REST       /home -  Home Partition

After I installed the OS I booted into Mac OS X and reformatted the rEFIt Boot Partition as HFS+ with journaling. I then copied the efi folder on my System (created by the rEFIt installer) onto the rEFIt Boot Partition.

Restarted the system and everything works. IDK why. Good Luck All
Thanks for all your help!!
Eliot Simcoe

---

