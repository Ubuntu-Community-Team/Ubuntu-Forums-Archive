---
title: "Changing WinXP from IDE to SATA."
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by DiMaG on 2006-05-21
Hello.

I have two HDs in my PC. One 60 GB with WinXP and one 80 GB with Ubuntu. I am running low on my space in 60 GB disk and got 250 GB disk as birthday present. Naturally I thought of changing disk. I'm checking here that my metods are right. Fell free to correct me (plain language, please).

[LIST=1]
[*]```
dd if=/dev/hda1 of=$HOME/WinXP_duplicate
``` First possibble error; does all my files work after I copy them to SATA disk?
[*]I take IDE disk out and insert SATA disk.
[*][LIST=A]
[*]I format my SATA disk with my WinXP copy. Not preferable.
[*]I use Gparted LiveCD. I hope it works.
[/LIST]
[*]Then I'll just rewrite all my data on SATA disk. Still no idea how, but looking  the answer.
[/LIST]

Please don't suggest me to use apt-get. I use wlan, that Ubuntu doesn't recognize and NDisWrapper doesn't work, no matter how hard I try.

---

### Post by RudolfMDLT on 2006-05-21
Hi, i'm new to ubuntu but I do know some stuff about XP. I think you could be overlooking one or two other problems.

It's been my experience on older chip sets that the IDE drive takes preference to the SATA drive when booting. one example I can think of right now is the Asus  P4P800 range of motherboards, specifically the VM division(I run one). And it took a while to get the BIOS to look for the bootstrap loader on the SATA drive.

As far as I know Grub replaces you current bootstrap loader because it handles the job much better than XP's. So replacing the IDE drive with a SATA one and not being able to boot from it, you would either not be able to get into any OS or just you're Linux OS. 

My advice is that 
1) put the SATA drive in as a 3rd drive and see if you can pick it up in the BIOS as a drive to boot from.
2) I feel more comfortable working in windows than ubuntu at the moment, so then I would advice you to use a program like Ghost to create en entire mirror copy of your 60GB drive onto the 250GB drive. Some drive mirroring applications require the source and destination partitions to be of exact same size. If you have an Ubuntu alternative you feel comfortable with please use it. If some one could recommend a Linux application for this I would also greatly appreciate it!
3) After the mirror has been completed you can safely remove the IDE drive and try and boot with you're SATA drive.
 
Another problem you might run into is the fact that grub will go looking for XP on  hda0,0 your primary drive that you had before Ubuntu. Now how you are going to tell grub that its needs to point to a SATA drive, i do not yet know. I have found some treads that you should look at also.

Almost every HOW TO on dual booting recommends installing windows first. 

Sorry for creating more questions than answers, but you have to be very well prepared before you attempt a heart transplant like this! Here's a list of threads and how to's you might want to look at. Your problems' solutions seems to be a combination of these.


For general installations(lookup dualbooting in the list):
[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

For restoring and editing Grub after XP installation:
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)
[http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu)

Some people had a similar problem...
[http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata](http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata)
[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)

---

### Post by kriding on 2006-05-21
It's been my experience that SATA is not natively supported by Windows, Even though the disk is present in the BIOS, from the many times I've reformated windows in the past I've needed a floppy disk with drivers taken from my motherboard drivers disk. During the setup, your asked if you want to install third party drivers, at this stage you select yes and put your floppy in the drive, the setup then installs drivers from your floppy and can then access the drive. I know this doesn't directly answer your question, but it may be worth considering before you attempt anything and find yourself in a position of reinstalling.

---

