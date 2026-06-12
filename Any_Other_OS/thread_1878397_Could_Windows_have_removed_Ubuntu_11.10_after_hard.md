---
title: "Could Windows have removed Ubuntu 11.10 after hard drive error?"
date: 2011-11-09
forum: Any Other OS
---

### Post by MLGlololol on 2011-11-09
I'm not sure if this should belong here (the Forum, or website as a whole), so sorry if any thing is wrong. 

Anyway, I have Windows 7 Home Premium (installed first), and Ubuntu 11.10 both installed on my computer, and could boot between either with no troubles until I got errors after booting a game in Windows. It couldn't find the hard drive, so I clicked on the "Fix" button, and after a few minutes (which I don't think could have removed over 200 GB of stuff in) I rebooted Windows and was not given a prompt to boot to Ubuntu. 
Anyway, the point, is it possible for Windows to delete another OS? If yes, would installing it again get it back (albeit with my stuff gone)? If no, did Windows just hide it (an old GParted would cause the "loading from" screen to hang there, so I have no idea if it is empty space there... I sure know Windows didn't get it back...)?

So, thanks for reading, and any help you can give... Sorry again for anything wrong.
I'm also trying to ask Windows support, but I still need to find the key, and I figured you guys would be super smart.

---

### Post by coffeecat on 2011-11-09
> **MLGlololol said:**
> It couldn't find the hard drive, so I clicked on the "Fix" button, and after a few minutes (which I don't think could have removed over 200 GB of stuff in) I rebooted Windows and was not given a prompt to boot to Ubuntu. 

I've never come across a "fix" button, so I guess it might be some sort of manufacturer's utility. Hopefully, all it has done is to rewrite the Windows bootloader to the mbr. But let's get an overview of your system.

You need an Ubuntu live CD or any Linux distro live CD. I don't think the Gparted CD will do, but you're having problems with that anyway.

Boot up the Ubuntu CD and choose "try Ubuntu" to get to the live desktop. Make sure you can connect to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script - the instructions are on that page - and post the contents of the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. You can use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar for this.

I'll be logging off soon, but there are plenty of people who can help you if you post the boot script output, and I'll check this thread in the (my) morning.

---

### Post by mips on 2011-11-10
I suspect you might have to reinstall grub.

---

### Post by ubupirate on 2011-11-10
Just to double check, see how many partitions you have setup via Disk Management in W7 (Start ->Control Panel->System and Security->Administration->Create and format hard disk partitions).

If you still see the partition you made for Ubuntu (Ubuntu+Swap), then you need only to reinstall Grub (as stated) as most likely a Windows recovery feature rewrote the MBR.

---

### Post by MLGlololol on 2011-11-10
Thanks.
I looked at my existing partitions, and found on the right size, and it has all of it as free space. I think Ubuntu got deleted, but don't really know because it's blue ("Primary partition") and not "Free space" (it does say 100% free space...),  so I'll just assume it's gone, right? 
Another issue: Computer won't boot a disk (Ubuntu install). Any thoughts? Has nothing to do w/ Ubuntu, but why not try?
Thanks for the help, everyone!

---

### Post by oldfred on 2011-11-10
do you have BIOS set to boot CD or use one time key (f12 on my system) to choose CD drive?

Some BIOS have a setting to prevent anything else from booting, you may have to turn that off. 

CDs get scratched and may not work.

Have you cleaned CD lens or does CD work on other disks?

---

### Post by mips on 2011-11-11
> **MLGlololol said:**
> I think Ubuntu got deleted, but don't really know because it's blue ("Primary partition") and not "Free space" (it does say 100% free space...),  so I'll just assume it's gone, right? 

Check with gparted from a livecd as windows does not recognise linux file systems.

---

### Post by MLGlololol on 2011-11-12
Sorry for the late reply, but Skyrim, you know.
Anyway, I'm downloading GParted now, and if Ubuntu is still on I reinstall GRUB?
If it's not, just reinstall?
Another problem: whenever I try to boot from CD (F12, Boot from CDROM) Windows tries to boot, and just gets an error. The BIOS page says boot from CD first. Would this be a "GRUB" error, or a computer error?
Again, thanks.

PS: this is getting less and less Ubuntu related, so I'll make sure to put it as Solved tomorrow. Thanks oldfred.

---

### Post by oldfred on 2011-11-12
If you try to boot from CD and Windows is still booting, then it is a CD or CD drive error. If first device is not bootable it moves to the next one in order you specified in BIOS.

So either CD is not a bootable CD, not written at slowest speed or is scratched etc or CD Drive is not working.

---

### Post by MLGlololol on 2011-11-13
I got it working. Pro tip: Make sure to write the files to the disk, NOT just the one thing. I feel more stupid than you think I am, so don't worry.
I updated, but unfortunately my files are gone. At least I have it make with no apparent errors.
Thanks a lot, everyone.

---

### Post by oldfred on 2011-11-13
Been there & done it.:) Glad you got it working.

---

