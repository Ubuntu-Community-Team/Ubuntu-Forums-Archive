---
title: "Fixing XP from Fiesty Fawn"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by BLGramma on 2007-08-31
I am new to Linux and Ubuntu.

I am a grandmother and at this time I am homeschooling two grandchildren.  My grandson's computer is having a major problem.  He has a Toshiba laptop with XP Media Edition and built in 
wireless (no card).    It is stuck in a loop when trying to boot up and always stops in the boot process at the same file.  From research on the internet It looks like the only way to fix it is to do a fresh install of XP.  He is worried that he will lose all of his files so we are trying to find a way around that.

We downloaded the iso file of Fiesty Fawn, burned it to CD and put it on his laptop.  We can sees XP C: Drive.
We hooked up his external hardrive (I think it's called USB)..anyway, we can see that.  What we are hoping to do is go ahead and install Fiest Fawn and would like to be able to fix XP problem by getting backup files from the external drive and putting them in Windows folder while in Fiesty Fawn.  If we can't do that we would like to at least move his more important files to the external hard drive.  Or maybe we can move them to Fiesty Fawn desktop and burn them to CD.   Whatever, we want to get these irreplaceable files saved before a fresh install of XP.

Does the above make sense?  Is it possible to do this?

---

### Post by obscur156 on 2007-08-31
Yes you can retrieve windows stuff from feisty.
You have to install feisty but make sure you dont delete the windows partition.
After the installation,you will have to install NTFS-3G and NTFS-CONFIG.
That way you will be able to see whats in windows partition and back up the important data that you have.

Becarefull not to delete the windows partition...

Good luck,best regards.

---

### Post by BLGramma on 2007-08-31
Obscur156,

Thank you.  We will probably (gulp) start it tomorrow.  Hope you're around tomorrow nite as I'm sure I'll be back.   I understand "Do Not Delete Windows".  I won't!!  

Okay, my first step will be install, then partion it, then come look for you..lol

Sincere thanks!

---

### Post by jombeewoof on 2007-08-31
You wouldn't have to install feisty, 
easiest way is the also the safest. 

Boot from feisty cd with USB external hard drive connected
Copy all important data from Windows drive. It's important you don't forget anything.
and if the external drive is big enough I always recommend copying the whole windows drive over.

Reinstall with feisty as your main operating system :)   or you could reinstall windows I guess.

copy important files back to windows. *optional, you could keep em on the USB drive.

This is the safest because there is no way to delete the windows drive. Well, not impossible, but a lot harder than when installing a new OS to a usb drive if you really don't know what you're doing. 

When you reinstall windows, if your drive is big enough leave 10 or 15 gigs free to do an ubuntu install. 
Can never hurt to have a couple more kids learning to use linux :)

---

### Post by obscur156 on 2007-08-31
Yes good call jombeewoof,she can use the LIVE CD.
So that way it is safer than installing feisty.:)
But after that ,they can surely give a try to ubuntu its a wonderfull distro and welcome to ubuntu forum.

Best regards.

---

### Post by Kheldin on 2007-08-31
It sounds like your XP is caught in a loop where it just keeps rebooting. I'm afraid to say though without any decent tech skills, it's going to be rather hard or irritating trying to fix this. Your best bet is what others said, use the CD and/or install Ubuntu and backup your important files, then either keep Ubuntu, or reinstall Windows then restore the data you backed up.

---

### Post by mlentink on 2007-08-31
You can simply use the Ubuntu liveCD as a rescuedisk in this case.

1. Boot up the LiveCD with the USB-(external)-drive connected
2. Copy all important data (preferably evrything on the windows disk) to the USB-drive
3. Make a choice on what to do next:
     a. Reinstall Windows XP from the XP-Installation CD
     b. If you decide not to use Windows anymore, install Ubuntu from the Live CD. You might then just as well give it the whole disk to play with. You would then still have access to all important data from the USB-drive, but NOT the Windows programs. Those don;t usually run in Ubuntu

---

### Post by Sef on 2007-08-31
> From research on the internet It looks like the only way to fix it is to do a fresh install of XP. He is worried that he will lose all of his files so we are trying to find a way around that.

If the files are not on a separate partition, then they will be lost if XP is reinstalled.

---

### Post by BLGramma on 2007-08-31
Tried to use the Fiesty Fawn CD as a live CD.  We were able to copy from both the external USB drive and the Windows Folder on XP.  The problem then was we could not paste from External to Windows or from Windows to External.  We could however, paste to the Fiesty Fawn desktop.  We tried copying the XP Programs folder to the desktop but recieved error message that the size was to big to copy (approx. 17 gigs of program files).

The next step was to try and install Fiesty Fawn instead of just using it as a live CD.  Got hung up on partitions.

Prepare disk space
How do you want to partition the disk
OPTIONS:
Guided\use entire disk
Manual
We chose manual
we need to specify  Partition for the root file system
(mount point\) with the minium size of 2 gbs and the swap partition
of atleast 256 mb

We have no clue how to proceed or if we should have chosen manual or what comes first... We were afraid the Guided would erase what was on XP's C drive now and the whole point of this is to not lose those files.
His Computer has 111 gigs and 35 of it is used by XP.  We would like to give 15 gigs to a Fiesty Fawn
install.  Whatever is suggested by you people to a swap file and the rest to Windows I guess.  Is there anything else we should have?   How do we do this and 
if anyone can show us how it should look (how do I type it in the partition list) I would appreciate it. 
Sorry to be such a pain.

Thanks in advance for all help.

---

### Post by Officer Dibble on 2007-08-31
Just for the time being it may be more advantageous to utilise your greater knowledge of XP than to look to Linux to solve the problem here.

Have you tried getting into Safe Mode in XP yet? Considering the implied specifications of your laptop I feel it is safe to assume that you will be able to access a USB connected External drive via XP in Safe Mode.

If you don't know how to get into Safe Mode then follow these instructions:

Turn on your Laptop

BEFORE it starts booting into Windows hold down the F8 key.

You will now see a menu with the "Safe Mode" listed at the top - choose that option.

Follow the prompts and login to XP as usual. You will notice that things are running a little slower than normal - that's very typical while in Safe Mode.

Once in, should be able to transfer files off that computer.

Personally I am suspecting that you will not need to reinstall XP on this machine, that it is likely a very fixable problem. But the most important thing at this time is that your data is preserved and so if you can get into safe mode then that would be the safest way to do it.

Later on we can talk about the option of fixing XP, repartitioning, etc, for the purpose of dual booting with Ubuntu if that's what you want. (You won't regret it!!)

---

### Post by ThinkingAboutWater201 on 2007-09-04
Hi got a ubuntu accout its me whos computer broke.......
I ran chkdsk /r and it worked!!! :guitar:

---

