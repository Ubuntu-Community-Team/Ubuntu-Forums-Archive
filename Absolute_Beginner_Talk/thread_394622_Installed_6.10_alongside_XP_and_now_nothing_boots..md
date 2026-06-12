---
title: "Installed 6.10 alongside XP and now nothing boots. Gulp!"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Beastie Boy on 2007-03-27
Hello all, and thanks for reading :) 

After a lot of deliberation, I decided to install and learn a flavour of Linux. I tried a few Live CDs and settled on Ubuntu. I really like the interface and there seems to be loads of community support, such as this great forum.

My current (or pre-Ubuntu) configuration is as follows:

250 GB SATA drive. Partition 1 - NTFS 45GB with XP SP2 installed, Partition 2 for the remaing drive, NTFS.
160 GB SATA drive. Just 1 partition, NTFS.
2 x 80 GB PATA drives, NTFS, connected in a Mirrored Raid using built in Raid controller.

My first step was to resize my 45 GB XP partition down to allow 8 GB free space. I did this using Partition Magic in DOS. After a reboot, I found everything to be OK. XP booted fine so no problems there.

I then booted the Ubuntu 6.10 Live CD and ran the installer. My first surprise was that all my drives were found and recongnised! So far so good. The Mirrored Raid appeared as 2 seperate drives, but that doesn't bother me, I guess this is a driver issue.

I went through the installer, chose to manually configure my drives, created a 7.5 GB partition for Ubuntu and a 512 MB partition for the swap file.
The first problem came when I selected the 7.5 GB part as root "/" and the 512 MB as /swap. The installer complained " No root selected".
Undeterred, I ran GParted outside the installer, remade the partitions, re-ran the installer and everything went well. Way, way quicker than an XP install!

I chose the option to reboot, removed the Live CD and waited.

"NO SYSTEM DISK OR DISK ERROR. INSERT SYSTEM DISC AND PRESS ENTER"

Bummer. My first worry was that I had made a wrong selection and erased all my other drives. I booted Ultimate Boot CD for Windows (UBCD) and found all my stuff intact. Phew!

I'm assuming now that there is a problem with GRUB and the dual boot process. This is where I am stuck. Not only is this my first Linux install, but also my first attempt at dual boot. Not a good combination. I looking for some advice on the best (read safest) way to proceed.

Should I;
Run my XP install CD, Recovery Console, type fixmbr to overwrite GRUB and try to get my XP install booting. Then try to reinstall GRUB to boot either OSs,

or try to find the problem with GRUB and rectify. Bear in mind that I had never heard of GRUB before yesterday :confused: 

or some other option.

Also (and please don't hate me) I need XP to remain as my default OS as my wife and kids also use the PC and are not yet ready to be converted.

I have looked at the links in the sticky to try and find a solution, but most problems seem to be based around GRUB not finding or booting either OS, and not the PC failing to boot altogether.

Any help very much appreciated. If anymore info is required, please let me know.

Cheers, Beastie.
P.S. Sorry for the long post.

---

### Post by overdrank on 2007-03-27
> **Beastie Boy said:**
> Hello all, and thanks for reading :) 

After a lot of deliberation, I decided to install and learn a flavour of Linux. I tried a few Live CDs and settled on Ubuntu. I really like the interface and there seems to be loads of community support, such as this great forum.

My current (or pre-Ubuntu) configuration is as follows:

250 GB SATA drive. Partition 1 - NTFS 45GB with XP SP2 installed, Partition 2 for the remaing drive, NTFS.
160 GB SATA drive. Just 1 partition, NTFS.
2 x 80 GB PATA drives, NTFS, connected in a Mirrored Raid using built in Raid controller.

My first step was to resize my 45 GB XP partition down to allow 8 GB free space. I did this using Partition Magic in DOS. After a reboot, I found everything to be OK. XP booted fine so no problems there.

I then booted the Ubuntu 6.10 Live CD and ran the installer. My first surprise was that all my drives were found and recongnised! So far so good. The Mirrored Raid appeared as 2 seperate drives, but that doesn't bother me, I guess this is a driver issue.

I went through the installer, chose to manually configure my drives, created a 7.5 GB partition for Ubuntu and a 512 MB partition for the swap file.
The first problem came when I selected the 7.5 GB part as root "/" and the 512 MB as /swap. The installer complained " No root selected".
Undeterred, I ran GParted outside the installer, remade the partitions, re-ran the installer and everything went well. Way, way quicker than an XP install!

I chose the option to reboot, removed the Live CD and waited.

"NO SYSTEM DISK OR DISK ERROR. INSERT SYSTEM DISC AND PRESS ENTER"

Bummer. My first worry was that I had made a wrong selection and erased all my other drives. I booted Ultimate Boot CD for Windows (UBCD) and found all my stuff intact. Phew!

I'm assuming now that there is a problem with GRUB and the dual boot process. This is where I am stuck. Not only is this my first Linux install, but also my first attempt at dual boot. Not a good combination. I looking for some advice on the best (read safest) way to proceed.

Should I;
Run my XP install CD, Recovery Console, type fixmbr to overwrite GRUB and try to get my XP install booting. Then try to reinstall GRUB to boot either OSs,

or try to find the problem with GRUB and rectify. Bear in mind that I had never heard of GRUB before yesterday :confused: 

or some other option.

Also (and please don't hate me) I need XP to remain as my default OS as my wife and kids also use the PC and are not yet ready to be converted.

I have looked at the links in the sticky to try and find a solution, but most problems seem to be based around GRUB not finding or booting either OS, and not the PC failing to boot altogether.

Any help very much appreciated. If anymore info is required, please let me know.

Cheers, Beastie.
P.S. Sorry for the long post.

Hi this thread may help you, If you can reinstall the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Hope this helps and good luck!

---

### Post by Bias on 2007-03-27
As this is a fresh install i would go with the fix what is already there option first. Recovery console etc.

Once thats done you can try Ubuntu again, I would not go for the manual option though, choose the disk then let it take the free space seems to work well.

Good luck

Nick.

---

### Post by tommcd on 2007-03-27
What likely happened, since you have a mix of sata and pata drives, is that grub went to the pata drive instead of the sata. See this:
[https://help.ubuntu.com/community/GrubHowto?highlight=%28ide%29%7C%28sata%29%7C%28grub%29](https://help.ubuntu.com/community/GrubHowto?highlight=%28ide%29%7C%28sata%29%7C%28grub%29)
Scroll down to "changing the disk grub is installed to". If that seems difficult, and reiinstalling grub doesn't work from the above post, then disconnect all hard drives except the one ubuntu is on and reinstall ubuntu. You can create mount points for the other drives and add them to /etc/fstab after ubuntu is installed.

---

### Post by Beastie Boy on 2007-03-27
Thanks for the replies.
> **tommcd said:**
> What likely happened, since you have a mix of sata and pata drives, is that grub went to the pata drive instead of the sata. 

If GRUB has installed stage 1 to my PATA drives, how can I tell and how do I remove it? Do I even need to remove it if  I rewrite the mbr on my SATA boot drive?

> **Bias said:**
> Once thats done you can try Ubuntu again, I would not go for the manual option though, choose the disk then let it take the free space seems to work well.

Good luck

Nick.

When I was running through the installer, the only options were the auto one which said 'Format entire drive' or the manual option. I didn't want to run the risk of actually formatting the whole drive and so I went with the manual method.

After reading the posted links, I think I'll try to get my XP install running again and then install GRUB seperately. There seems to be lots of info regarding doing this. Super GRUB Disk looks as though it is just the sort of thing for noobs like me.
I'll try it this evening and report back.

Thanks again.

Cheers, Beastie.

---

### Post by dstew on 2007-03-27
I think the error message you got (NO SYSTEM DISK OR DISK ERROR. INSERT SYSTEM DISC AND PRESS ENTER) is being sent from your BIOS, not from grub or your OSs. It means that the device you designated as the boot drive in your BIOS was not bootable. If you had told your BIOS to boot from the CD, and then you took out the CD, it would give you that error. Alternatively, it is looking or a boot loader on the MBR of a disk that never had on, like your storage disks. 

I suggest you enter your BIOS setup and look at the boot options, and if possible change the boot order or boot device to a disk that you think should be bootable. If it seems to be pointing to the correct disk, consider re-intalling grub on that disk.

---

### Post by Beastie Boy on 2007-03-27
Yes, you are right, the error is definately generated by the BIOS. By boot sequence is set to 1) CD Drive  2) Hard Disk Drive. As far as I can tell, there is no option to specify a particular HDD, and so if no bootable CD is present, I think it checks all HDDs for a MBR.

What worries me is that it doesn't seem to be able to find one.

Cheers, Beastie.

---

### Post by dstew on 2007-03-27
Probably the safest thing to do would be to restore your Windows bootability with the recovery console and fixmbr. Then relax, and think for a while about re-installing grub.

---

### Post by Beastie Boy on 2007-03-29
Solved.

First of all I tried the Recovery Console on the XP installation disc and ran *fixmbr*. Although this reported as worked, the PC still would not boot. Same error.
At this point I started thinking that my drive was faulty.

After a lot of messing around, I decided to unplug my other drives (non OS) and try the Super Grub CD. I selected 'Fix boot of Linux' and rebooted.
This time the Grub OS selection menu appeared! At least my MBR was now OK. However, none of the listed OSs would boot. I received an error 'Partition does not exist'.

I now suspected that my Grub menu.lst file was incorrect and as tommcd said earlier, Grub had detected my PATA drive as the first drive, when in fact it was the third drive.

Using Super Grub CD again, I forced a boot of my Ubuntu installation (3rd option on the Linux menu), opened the terminal and entered;

```
sudo gedit /boot/grub/menu.lst
```

(I wouldn't have known that a week ago :)  )

Sure enough, my OS installations were listed as being on (hd2,#) instead of (hd0,#).

Once corrected, everything was sweet.

And so once again, well written Open Source software was able to succeed when MS own installer could not boot it's OS. There a moral there somewhere. 

My only other problem was that after auto downloading and installing the updates, my menu.lst file reverted back to the incorrect drive numbers, but at least I now knew how to correct it :) 

Many thanks for all your help.

Cheers, Beastie.

---

