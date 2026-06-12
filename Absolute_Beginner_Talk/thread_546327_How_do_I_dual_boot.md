---
title: "How do I dual boot?"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Fixman on 2007-09-08
Well, I have installed Ubuntu Feisty, and, after some time, found out that its a bad idea for single-booting (specially for gamers like me). So, how do I dual boot with Windows Vista?

---

### Post by oilchangeguy on 2007-09-08
> **Fixman said:**
> Well, I have installed Ubuntu Feisty, and, after some time, found out that its a bad idea for single-booting (specially for gamers like me). So, how do I dual boot with Windows Vista?

see this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by spacegypsy on 2007-09-08
useful links for dual booting;

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

have fun

---

### Post by djchandler on 2007-09-08
> **Fixman said:**
> Well, I have installed Ubuntu Feisty, and, after some time, found out that its a bad idea for single-booting (specially for gamers like me). So, how do I dual boot with Windows Vista?

Back up your data you want to save in Ubuntu, Install windows, then re-install Ubuntu.
I don't think there's anyway to install windows with another OS already installed unless you have two separate hard drives, and have a bios menu to choose which to boot.

Before you do that though, I would at least try to put the Windows install CD in your optical drive, boot from the hard drive, and see if grub lets you use part of the HD for Windows. I'm not sure it works. I'll do some research and see if it's possible.

DJ

PS That's the thing about this forum. Somebody always knows something you don't, and in this case, something I don't.

---

### Post by oilchangeguy on 2007-09-08
> **djchandler said:**
> Back up your data you want to save in Ubuntu, Install windows, then re-install Ubuntu.
I don't think there's anyway to install windows with another OS unless you have two separate hard drives, and have a bios menu to choose which to boot.

Before you do that though, I would at least try to put the Windows install CD in your optical drive, boot from the hard drive, and see if grub lets you use part of the HD for Windows. I'm not sure it works. I'll do some research and see if it's possible.

DJ

PS That's the thing about this forum. Somebody always know something you don't, in this case, I don't.

where have you been? of course it's possible to dual boot, using one hard drive. simply install windows first, then ubuntu.

---

### Post by Fixman on 2007-09-08
So, I just can't install Vista witout de installing Ubuntu before?

---

### Post by Rupertronco on 2007-09-08
It is very, very simple to dual boot a system with windows/linux with linux already being installed, on one hard drive. The only down side, your windows will not be installed on the C:\ drive. Your computer will give it some arbitrary letter. This only encounters problems when programs are much older and try to install themselves on C:\ instead of first looking for your windows directory. 

Check out [www.apcmag.com/dualboot](www.apcmag.com/dualboot) a friend of mine helped write that and I think it's a spectacular guide.

---

### Post by oilchangeguy on 2007-09-08
> **Fixman said:**
> So, I just can't install Vista witout de installing Ubuntu before?

if you're using a restore cd just load it. and let it do it's thing. if it's a vista cd, follow the prompts, and delete any partitions. then create a new one for vista. and when ready install ubuntu, following the prompts to create a partition for it.

---

### Post by bobpur on 2007-09-08
You can dualboot on one drive. If your not into partitioning drives I'd stick to dualbooting on two separate drives. I like it because if you screw up on one drive things should be good on the other drive. If you jump from distro to distro having windows on another drive keeps that info out of the way.
This computer I'm using at the moment has a 300gb Maxtor SATA Drive partitioned as 125 gb NTFS for Windows 2K Pro, 124 gb EXT 3 for linux and the remainder as FAT 32 for access from both OS's.

---

### Post by oilchangeguy on 2007-09-08
> **Rupertronco said:**
> Bios is your basic input output system. It will decide what device to boot from. It differs from GRUB, a bootloader that will tell your computer what operating system to load. It is very, very simple to dual boot a system with windows/linux with linux already being installed. The only down side, your windows will not be installed on the C:\ drive. Your computer will give it some arbitrary letter. This only encounters problems when programs are much older and try to install themselves on C:\ instead of first looking for your windows directory. 

Check out [www.apcmag.com/dualboot](www.apcmag.com/dualboot) a friend of mine helped write that and I think it's a spectacular guide.

the computer does NOT assign the drive letter. windows does. if ubuntu is installed first, and then windows. windows simply overwrites grub. this is fairly simple to fix.

---

### Post by djchandler on 2007-09-08
> **oilchangeguy said:**
> where have you been? of course it's possible to dual boot, using one hard drive. simply install windows first, then ubuntu.

Did you read my first sentence? I'm hoping there's a way to install Windows without wiping out Ubuntu first. As far as I know, the only way to do that is with two hard drives, and a bios-based boot menu. I guess I should have been clearer the first time through. I went back and edited to make sure somebody else didn't make the same assumption you did.

DJ

---

### Post by Rupertronco on 2007-09-08
> **oilchangeguy said:**
> the computer does NOT assign the drive letter. windows does. if ubuntu is installed first, and then windows. windows simply overwrites grub. this is fairly simple to fix.

If you clicked my link you'd see that it concentrated on restoring grub to the mbr after windows wipes it. The correction which actually assigns the drive letter is really quite irrelevant, good tidbit?

---

### Post by djchandler on 2007-09-08
> **Fixman said:**
> So, I just can't install Vista witout de installing Ubuntu before?

[Maybe this will work for you.]("http://www.goodells.net/multiboot/principles.htm") Give it a try; it may save you some time of having to re-install Ubuntu. Use Gparted to restrict the size of your Ubuntu partitions first. Don't delete the swap partition.

DJ

PS I have never seen anybody here suggest this, but you are also an unusual case, as most people already have Windows, then want to install Ubuntu. Microsoft makes it hard to do the reverse.

---

### Post by djchandler on 2007-09-08
> **Rupertronco said:**
> It is very, very simple to dual boot a system with windows/linux with linux already being installed, on one hard drive. The only down side, your windows will not be installed on the C:\ drive. Your computer will give it some arbitrary letter. This only encounters problems when programs are much older and try to install themselves on C:\ instead of first looking for your windows directory. 

Check out [www.apcmag.com/dualboot]("http://www.apcmag.com/dualboot") a friend of mine helped write that and I think it's a spectacular guide.

I just found another way to do that also.

[http://www.goodells.net/multiboot/principles.htm](http://www.goodells.net/multiboot/principles.htm)

Sometimes we're too fast for each other. While you're writing a post, especially a slow typer like me (bi-lateral carpal tunnel) gets beat, and there's 10 posts before I can answer the first. It's good to know you don't have to wipe out Ubuntu first, but most of us have never tried to do that, just the reverse, which is easy.
DJ
:guitar:
PS This is a case where I was asked why I hadn't clicked a link on somebody's post, because I was busy writing my own. We need to watch the back-biting here.
Good gravy, we're competitive, but we can be a little more polite to each other.

---

### Post by ts51 on 2007-09-08
> **oilchangeguy said:**
> where have you been? of course it's possible to dual boot, using one hard drive. simply install windows first, then ubuntu.



Exactly! It would be too dificult to dual boot with Ubunt installed first.

Wipe clean your HD.

Make 3 partitions... A big NTFS for Windows, A big ext3 for Ubuntu and a 1 gig swap partition.

Install Windows first on NTFS

Install Ubuntu second on Ext3



badda bing baddda boom

---

