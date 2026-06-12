---
title: "Partitioning, GRUB, video driver problems"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by derockus on 2008-02-06
Well, I think I did my computer in...

I had to do a no-cd install with Unetbootin since my drive is busted and it worked fine.  Partitioning the drives went fine and Ubuntu 7.10 installed and booted up.  It prompted my to install the "proprietary drivers" for my video card (GeForce 440) and ethernet card so I went ahead and did.  It asked for a reboot which I allowed only to restart Ubuntu to the dreaded black screen.  I rebooted Windows XP and it alerted me that new hardware was found and that it was installed and I needed another reboot.  I obliged and it still didn't work.  

tl; dr - couldn't get video card drivers to work for ubunutu

I figured that if i reinstalled ubunutu I could at least use it without installing the proprietary drivers.  I ran Unetbootin again and it went through everything OK until i got to the partitioning section again.  Since the drives were already partitioned I figured i could just use the same partitions and overwrite the previous installation.  It was upset about this and informed me that there was "no root directory" found.  I thought erasing the data from the ext3 partition would fix this but to no avail.  Now is where I get hosed.  I couldn't get it to reinstall so I figured "well, Windows is still working, I'll just end the installation now, leave the partitions set up and work on it tomorrow."  WRONG.  When I rebooted it gave me a GRUB error message and I can't even get to the "choose which OS to boot screen"  it tells me I have "ERROR 17."  What have I done and is there any solution.  I mean any solution.  Since my CD-ROM doesn't work I can't even load my Windows XP recovery disc!  And I can't (or don't know how to) get to a command prompt to just format C:.  Any ideas??

---

### Post by wickstopher on 2008-02-06
It sounds like a tricky situation and I can't begin to answer all of your questions, but I do know one thing that you are doing wrong:

when you attempt to reinstall Ubuntu, you're going to have to manually partition, and make sure that  the partition that you're installing Ubuntu to is mounted to "/".  That specifies the partition as the root partition that the installer was looking for and not finding.  By default, since you already have Ubuntu installed on that partition, the liveCD or unetbootin (not familiar with that, but i'm sure it's more or less the same) will mount that partition to something other than "/" so you have to manually set it in gparted by selecting the manual partitioning option when installing.

Hope this helps!

---

### Post by mikeyphi on 2008-02-06
As mentioned in post #2 - you need to erase the old Ubuntu partition first - then tell the installer that you want to make a new partition (in that space) mounted to "/"....after that all will go smoothly!!!

---

### Post by dstew on 2008-02-06
I don't know if you can boot the equivalent of a Live CD over the network, but if you can, you can use it to examine your system and see what you are left with. I know you can just go "all Ubuntu" by re-installing over the network, but I don't think you can install Windows over the network. So if you go all Ubuntu you might wipe out Windows, if it is still there. You might look around to see if there is a way to just boot to an Ubuntu system over the network without installing. Can you boot a USB port, or do you have a floppy drive? You could boot a system from these also. A floppy system would be small, but you could use the command line to check your hard drive partitions.

---

### Post by derockus on 2008-02-06
These are all great suggestions but I am unfortunately far more screwed up for these to work.  When I power on the Dell BIOS loads and then it immediately follows with error messages to the effect of "GRUB cannot load" and then maybe two other lines of error messages.  The final line is "ERROR 17."  After that it locks up and the only option is to power down.  You can't enter code or anything.

---

### Post by dstew on 2008-02-06
> It was upset about this and informed me that there was "no root directory" foundWhenever you install a new system you need to designate a root partition by giving one of the partitions the mount point '/' (without the single quotes). Probably at present it is best to try to re-install Ubuntu using Unetbootin. Use the previous partitons, and assign the ext3 partition to the / mount point. The installer may ask you to format the ext3 partition again, that is OK. But I don't know if you can save your Windows system. If it has not been damaged, you might be able to get it going again from a working Ubuntu system. If you have a floppy, you can try also to boot a tiny linux system from there to check out your system. You would need to get into your BIOS setup to get it to boot from the floppy. Usually, you do this by holding a function key, like F2, when you first power it on.

---

### Post by derockus on 2008-02-06
Where could I get a tiny linux system from?  Also, at this point I'm prepared to abandon my windows system without much regret.  All my important things are on an external harddrive and I was only trying to setup the dual boot system so I could use windows if I *really *had to. 

If I start with "tiny linux" could i use it to format my hdd and then somehow get ubunutu going?  Bear in mind my cd-rom is kaput.

---

### Post by mikeyphi on 2008-02-06
You might find further advice here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

but why not try your original method again - just delete the Ubuntu partition during the install process - remembering to tell the installer to use that free space and mount at "/"

---

### Post by derockus on 2008-02-06
I would try the original method but the computer will load the Dell BIOS and then it errors IMMEDIATELY.  No windows, no dos prompt, no GRUB, no install screen, no nothing, just an error message and no way to enter in any commands.

Is there any way to just do a clean format of the drive and start *completely * from scratch?

---

### Post by onthefence on 2008-02-06
I am having a similar problem which is basically a corruption of the Master Boot Record which is what loads the OS's (kinda). 
According to some answers I got on my post, you can fix the Windows entry in the MBR by entering recovery mode through the Windows Install CD and typing some commands, then you can reinstall GRUB by booting to the LiveCD and typing a command there. 

The disclaimer is that I haven't had a chance to test this but I believe it is the solution.

Here I wiill quote the previous posts:

Windows MBR:
"ok then.....it means you have to boot using winblows installation....choose recoverymode.....after you get something like C:\windows
type fixmbr
then fixboot
restart.....
next....fix grub"

GRUB:
"After you reinstall Windows insert the live cd and reinstall grub, ill hunt the command now. Try "sudo grub-install" without quotes.

edit: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) - Should be what you need if that fails."

---

### Post by derockus on 2008-02-06
Appreciate the help but for now it's not going to work as I am cd-rom-less.

---

### Post by derockus on 2008-02-06
x

---

