---
title: "2 days wasted on boot loader - need help badly"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by pilot550 on 2007-03-10
I'm about to lose it now.:mad: I have spent 2 days trying to make a triple boot xp/vista/kubuntu. ](*,) I have 3 hard drives. 2 SATA drives set up in a RAID0 config divided into 3 partitions. XP on one Vista on the other and files on the third. My third hard drive is an IDE with 3 partitions, Kununtu on ext3, swap on ext2 and a fat32 partition mounted as /media/share.

Linux doesn't like my RAID of course which is fine except that I can't use the GRUB boot manager to boot to my Windows partitions. So I am trying to use the windows boot manager; following the directions from here:
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)
I have also tried to do it this way:
[http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/](http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/)

Doing it the first way when I select to boot kubuntu the screen goes black except for the word GRUB and it just hangs there.

The second way just flat out tells me the file linux.bin is corrupted.

sudo dd if=/dev/hdc of=/media/share/linux.bin bs=512 count=1
is the way to copy my boot sector, right? So what am I doing wrong?:-k  
The only thing I can do is go in my BIOS every time and change the boot order of my drives. That's a pretty crappy way to do it.

I've tried to do the fakeraid thing just to get grub to work, but that's a nightmare. Please help!!:confused:

---

### Post by Herman on 2007-03-10
Hello pilot550,
Try this, [EasyBCD]("http://neosmart.net/dl.php?id=1")                   > EasyBCD is NeoSmart Technologies' multiple award-winning answer to tweaking the new Windows Vista bootloader. With EasyBCD, almost anything is possible. Setting up and configuring Windows boot entries is simple, and there is no easier way to quickly boot right into Linux, Mac OS X, or BSD straight from the Windows Vista bootloader - on the fly, no expert knowledge needed!Let me know if it works,
Regards, Herman :)

---

### Post by xyz on 2007-03-10
problem with the link...
Try [.this EasyBCD]("http://technorati.com/tag/EasyBCD")

BTW Herman - can it be useful with XP at all or is it strictly for Vista pbms?

---

### Post by pilot550 on 2007-03-10
I just got done trying EasyBCD. I booted from the Kubuntu live CD opened a terminal and:
sudo grub
find /boot/grub/stage1
received "(hd0,0)"
root (hd0,0)
setup (hd0,0)
quit

Then booted Vista and ran EasyBCD 1.52. I added Linux to the boot menu and set it up as hard drive 0 partition 1. Rebooted and selected Linux. Then all I get is a black screen with the word GRUB and then nothing. Thanks for trying.

---

### Post by Herman on 2007-03-10
Hello pilot550,
I'm sorry for any inconvenience, and disappointed it didn't work for you. :(

About all I can suggest is to please re-read any documentation that comes with EasyBCD and try again.

One tip I can give you is to try commenting out the 'savedefault' commands in your /boot/grub/menu.lst in Ubuntu, and see if that helps. (See example below),
```
title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.15-25-386
[COLOR=Red]**# **[/COLOR]savedefault
boot
```[EasyBCD]("http://neosmart.net/dl.php?id=1") is developed by a fellow Ubuntu Web Forums member called Computer Guru, who seems very dedicated to his software, and who even has his own web forum where he personally helps people, so try here, [NeoSmart Technologies Help and Support]("http://neosmart.net/forums/index.php?getforum=5")

xyz,
I don't think you can use EasyBCD in Windows XP but I haven't checked.
You can use [WinGrub,]("http://sourceforge.net/projects/grub4dos") in Windows XP, I tried it out a while ago, 11th Nov 2006 to be precise, and it it still in my computer and still works very well every time I re-try it.

Regards, Herman :)

---

### Post by pilot550 on 2007-03-14
I'm trying to use NeoGrub from EasyBCD 1.52. I have it configured like this:
```
# NeoSmart NeoGrub Bootloader Configuration File
#
# This NeoGrub menu.lst file should be located at \NST\menu.lst of the boot drive.
# Please see the EasyBCD Documentation for information on how to create/modify entries
title        Kubuntu [Feisty Fawn Herd 5]
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-9-generic root=/dev/hdc1 ro quiet splash
initrd        /boot/initrd.img-2.6.20-9-generic
# savedefault
boot
```

This is the what is in my /boot directory:
```
steve@tsunami:/boot$ ls
abi-2.6.20-9-generic         initrd.img-2.6.20-9-generic.bak
config-2.6.20-9-generic      memtest86+.bin
grub                         System.map-2.6.20-9-generic
initrd.img-2.6.20-9-generic  vmlinuz-2.6.20-9-generic
```

Is there something wrong with this? When I choose to boot Kubuntu I still get the same thing. A black screen with the word GRUB and then nothing happens.

---

### Post by dstew on 2007-03-14
You can boot a RAID using grub. I found this discussion. It all depends on installing dmraid while running from the Live CD. This allows you to mount your RAID and make it bootable. Here is the link:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Herman on 2007-03-14
> A black screen with the word GRUB and then nothing happens.That does not sound very good. Can you tell me more about this black screen with the word GRUB on it? 
Does it have some other text on it?
Does it have a right-arrow after the word Grub and a blinking underscore? Like[ this]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Returns_to_a_Grub__prompt")?

Or does it have a non-blinking (solid) underscore, like [this]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#GRUB_")?

Or is it really just the word 'grub' and nothing else?

Have you tried booting your Kubuntu from a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to see if it will boot from that?

When you installed Kubuntu, did you use the 'Alternate' CD (see my sig link), and set your Kubuntu up with RAID?
[IMG]http://users.bigpond.net.au/hermanzone/p3d/14ntfs.png[/IMG]

I have not tried that myself, so I'm not sure, but it seems to be as something that might be worth considering.
You should also try searching the Official Ubuntu Wiki on the subject if you haven't already tried that. [Official Ubuntu Wiki Front Page]("https://wiki.ubuntu.com/")
Here is a link from the wiki already, [RaidConfigurationHowto]("https://help.ubuntu.com/community/RaidConfigurationHowto")

I hope I'm being helpful, I haven't tried RAID myself so I have no first-hand experience with it. I'm trying to be helpful anyway.

Regards, Herman :)

---

### Post by pilot550 on 2007-03-14
I do appreciate all your help. It's none of the screen you linked to. The entire screen is black except for the top left hand corner it says "GRUB" and thats it. When I select the drive I installed Kubuntu onto as my first boot device in the BIOS it boots normally but it will not read my SATA RAID drives. If I do "sudo fdisk -l" I get "Unable to seek on /dev/sda".

This RAID issue might be the root of my problem. I will download the alternate install CD and see if I can get my RAID running in Linux. I'll let you know what happens. Thanks for your help Herman and dstew.

---

### Post by Herman on 2007-03-15
Okay pilot550, I'm sorry I can't be more helpful, I really should find out all I can about RAID and also LVM. They are both options that the 'Alternate' install CD can do, which I have neglected to look into. I could make my 'Alternate' CD install web pages better if I do some more work and find out more about those two options. About all I know about RAID now is just what everyone else knows already, which means I only know what I can find out by googling. Really, the only way to find out for sure what a RAID install will be like is to try one myself. Until recently, I haven't had hardware that would be suitable for that. Now I do, so a RAID install is on my 'to do' list. You have aroused my curiosity.
What kind of computer work (or pleasure), would most users find RAID0 useful for, if it's okay for me to ask? 

Regards, Herman

EDIT: I found these links if any of these are any help, 
[RAID 1 in Ubuntu 6.10 and mkinitrd - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=378362")
[FakeRaidHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FakeRaidHowto")
[SATA RAID Howto - Ubuntu India]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto")
[coding, by Derek Young: Linux RAID: lessons learned]("http://dmy999.com/article/17/linux-raid-lessons-learned")

---

### Post by pilot550 on 2007-03-17
I have been using a RAID0 for performance in gaming. I have followed all of the guides listed, and tried some of my own ideas, and still cannot get my RAID to work. The guides are not that great. When a guide says "do this and you will get a bunch of error messages" something needs work. I guess the Linux programmers have to decide there is a need for native RAID support in the install CD. At least the guide should specify which error messages you should receive so you can isolate where your problem is.

I have an A-Bit AV8 motherboard with a VIA chipset. Perhaps my RAID controller just isn't supported.

---

### Post by dstew on 2007-03-17
I think some of the other posters have misunderstood your problem. Maybe I have too, but from my point of view it looks like you want to keep your RAID partitions as they are, and install linux on your RAID, and end up with a dual-boot system.

If you want a dual-boot system, you must must must follow the FakeRaidHowTo and install dmraid from the live CD before you can properly install your linux system. Here is the key phrase in the whole discussion:

> Installing dmraid

The standard LiveCDs and Alternative install CDs do not yet contain support for fakeRAID. I used the LiveCD to boot up, and used the package manager to download the dmraid package from the universe repository (enable the "Universe" source in the settings of Synaptic or by editing /etc/apt/sources.lst). 

You do this *before* you install linux on your hard disk. You are installing and using the dmraid program in your temporary file system while running the LiveCD. If you install linux on your disks as though they were individual disks, and not a RAID, then linux will behave that way, and not see the RAID. If you want linux to install on the RAID, and boot from it, you need to install it on a working RAID, and that is why you need to have dmraid running during the installation process.

---

### Post by pilot550 on 2007-03-19
I set up 2 additional partitions on my RAID drives with partition magic. A 30Gig ext3 for linux and a 1.5 Gig ext2 for the swap. I tried installing with the alternate live CD and loading the drivers manually as directed in the fakeraid how to. I also tried using the normal live CD and just going to the repositories to install the specified programs from the fakeraid how to. I even tried using the feisty driver on the edgy install like it recommended.

The end result is always the same. My drives are listed as /sda and /sdb. With /sda giving me an error message about can't read, and /sdb says unknown. There is no third option being a /via(crazy number) representing both drives, and my partitions are nowhere to be found. I even tried to install onto /sdb just because it would at least read that one, and I got an error message. I guess I am getting off topic. I really am fine with linux being on /hdc. I just want a boot loader that will work with my RAID. Thanks for all the time and effort.

---

### Post by nyinge on 2007-03-20
When you're following the FakeRaidHowto guide, where do you get stuck?  Also, make sure the raid controller is supported.  Here's dmraid's [readme]("http://people.redhat.com/%7Eheinzm/sw/dmraid/readme").

Follow the original fakeraid guide.  Not the edgy fakeraid guide, since it doesn't work for some.  I recommend using Feisty, because dmraid package in Edgy is broken.  Also because you might run into dependency problems later if you only grab Feisty's dmraid package and related packages for installation in Edgy.

---

### Post by pilot550 on 2007-03-20
> **nyinge said:**
> When you're following the FakeRaidHowto guide, where do you get stuck?  Also, make sure the raid controller is supported.  Here's dmraid's [readme]("http://people.redhat.com/%7Eheinzm/sw/dmraid/readme").

Follow the original fakeraid guide.  Not the edgy fakeraid guide, since it doesn't work for some.  I recommend using Feisty, because dmraid package in Edgy is broken.  Also because you might run into dependency problems later if you only grab Feisty's dmraid package and related packages for installation in Edgy.

I guess my RAID is supported. I checked the readme and it's listed (Highpoint 370). The closest I was able to get was using the Kubuntu Feisty Fawn live CD. As per the fakeraid guide you suggested I booted from the live CD and downloaded dmraid from the repositories. It shows my RAID drives but none of my partitions on the RAID.

---

### Post by nyinge on 2007-03-21
Unfortunately, the graphical installation will not work.  The installation failed for me in the end while I was using the ubiquity(name of the Ubuntu graphical installer).  That's because, IMO, Ubiquity is not aware of dmraid and fails to incorporate into the initial ram disk (initramfs).

You'll have to follow the procedure in the guide exactly, i.e. bootstrap installation of Ubuntu.  It is painful but worth it, because once you get it, you'll understand a lot about how the distribution is built... well...  pretty much :D ..  I strongly recommend you read through the whole thing at least twice before actually doing it.  Also, be extremely careful about where you install stuff, because the slightest mistake could ruin your data.

---

