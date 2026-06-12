---
title: "Issues dual-booting Ubuntu with XP"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by flamingsole on 2007-07-19
Hello,

I'm making my first attempts to learn Linux, and in attempting to dual boot Ubuntu and XP, I think I've ruined my XP, and I'm unable to boot Ubuntu. I have a 250 GB hard drive that was previously running XP, and a 200 GB hard drive that was previously holding Apache, PHP, MySQL, etc.

I selected to install Ubuntu to the 200 GB drive, and everything seemed to go fine until the end, when there appeared to be an error creating something related to the boot. I couldn't access the lst file at this point. When I rebooted to make sure that XP was still ok, it was fine, and Ubuntu wasn't in the list. I tried using GRUB at this point to add Ubuntu to the MBR, and got an error message saying that this was unsuccessful.

At this point, I kept researching on Google, and many people seemed to suggest that if I unplugged my Windows hard drive temporarily, I could get Ubuntu working on the other drive and then return the Windows drive and have both. I tried this. At this point, I couldn't get anything to boot at all, from the hard drive or GRUB. When I plugged the Windows drive back in, I got the message "Error loading operating system". I loaded up Windows Recovery, and tried chkdsk. I think this was when I saw an error message telling me I had irreparable errors. At this time, many people suggested that I try fixmbr, which I did. Recovery said this was successful, but when I went to reboot nothing was changed. I tried booting Windows from GRUB as well, and also tried repairing the MBR from GRUB, and also tried uninstalling GRUB entirely from itself, and these all resulted in messages that the tasks were unsuccessful.

So, I can run Ubuntu from the CD, and GRUB and the Ubuntu cd know that there's an installation on the 200 GB hard drive, and GRUB is aware that there's a Windows installation on the 250 GB drive. Windows Recovery does not appear to be aware that there's a Windows installation.

I've been looking around for some time, but I haven't found a solution for my set of problems. I feel like I have probably fried Windows, but I want to find out if there are steps I might be able to take to recover it, or if there are steps that I might be able to take to access my new Ubuntu. If I could get an OS working on one of these hard drives, I could reinstall the other one on the other hard drive. Any help would be most appreciated. 

Thanks so much.
Jon

---

### Post by MythicalVax on 2007-07-19
First: if you cannot recover from the boot process failure, stay calm. Your data is still there. :) Investigate on how to mount your windows partition and use Ubuntu to back it up. 

Do this immediately to not regret later.

Second: you should be sure your windows hard disk is in the original place, plugged into the original cable: if not, it does change name and that is probably the remote cause.

The partition values in your c:\boot.ini may now have changed to something it is not correct.

Disconnect your linux hard disk, check that the BIOS is set to boot your windows hard disk and give it a try.

If it does not boot, plug your windows hard disk in another place, check the BIOS for the new value and reboot.

HTH.

---

### Post by flamingsole on 2007-07-19
Thanks for replying. I want to see if I understand correctly.

> **MythicalVax said:**
> First: if you cannot recover from the boot process failure, stay calm. Your data is still there. :) Investigate on how to mount your windows partition and use Ubuntu to back it up.

I've learned how to mount the windows partition into Ubuntu, and I can see the data on it. Ubuntu, though, is occupying my only CD/DVD drive since I can't seem to boot the installed version, but am relying on the Live CD version. Do you mean, then, that I should create an empty partition on the Ubuntu drive, and drag Windows data over to it?

> **MythicalVax said:**
> Second: you should be sure your windows hard disk is in the original place, plugged into the original cable: if not, it does change name and that is probably the remote cause.

I've verified that the windows drive is in its original place, with its original cable.

> **MythicalVax said:**
> The partition values in your c:\boot.ini may now have changed to something it is not correct.

I checked c:\boot.ini from the mounted disk. It appears as follows:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" 1 /fastdetect

The only thing different there from the example on Microsoft.com is the 1 that's right before /fastdetect. I'm not sure if this was there before, but Ubuntu says it does not have permissions to change it.


> **MythicalVax said:**
> Disconnect your linux hard disk, check that the BIOS is set to boot your windows hard disk and give it a try.

I tried this, and I still got the error loading operating system message. I don't think I have any other place for the windows drive to go. The Ubuntu drive is a SCSI, and the windows is an ATA.

Thanks for your help, and any further advice or ideas.

Jon

---

### Post by ddrichardson on 2007-07-19
Just a quick thought - you unplugged the larger drive - how were they connected? Were they on the same IDE channel and did you change the Master/Slave jumper?

---

### Post by flamingsole on 2007-07-19
The larger drive was connected by itself, and the smaller drive was connected with the CD/DVD drive as a slave.  Acording to the BIOS, they were not on the same channel. The larger drive was the Master on Channel 1, and the smaller one was the Master on Channel 2, with the CD/DVD as the Slave on Channel 2.

I didn't change the Master/Slave jumper, because I couldn't see one on the SCSCI drive (the smaller one). I worried about that when I was doing it, which I suppose should have been a red flag. Did that fry something?

Thanks for helping
Jon

---

### Post by ddrichardson on 2007-07-19
Sorry I didn't realise you were using SCSI (are they both SCSI?). EDIT: Don't bother I can see the answer now...;)

Let me get this right - Windows will not boot. Ubuntu will not boot. Does Grub run? Lastly is bios configured only to attempt booting from the first drive?

---

### Post by flamingsole on 2007-07-19
> **ddrichardson said:**
> Sorry I didn't realise you were using SCSI (are they both SCSI?).

Let me get this right - Windows will not boot. Ubuntu will not boot. Does Grub run? Lastly is bios configured only to attempt booting from the first drive?

Only the smaller one (that has Ubuntu on it) is SCSI. Windows is on an ATA. And yes, Windows does not boot. Ubuntu will boot from the Live CD, and that's it so far. Grub does run. It appears to recognize both Windows and the local installation of Ubuntu, but it doesn't appear to be able to boot either of them. I think BIOS must be only attempting the first one. I don't think I know how to configure that, though. Is that possibly part of the solution?

Thanks
Jon

---

### Post by ddrichardson on 2007-07-19
fixmbr should have removed grub from the master boot record. When you say grub is running - is it running only from the live cd or from the hard disk?

Have you used the live cd to backup important data?

---

### Post by flamingsole on 2007-07-19
I guess Grub isn't running, now that I think about it. I can boot it from its own CD that I created prior to trying to install Ubuntu. It isn't able to restore the mbr, though, for either OS.

I was somewhat confused about using the live CD to backup data. Would I create an empty partition on the Ubuntu drive, and copy files over to it? I was afraid this partition might end up being deleted somehow, depending on what steps I need to take from here. I can do that, though, if that should be the next step. I've been able to mount the Windows disk from the live CD.

---

### Post by ddrichardson on 2007-07-19
The partition wont be deleted if you choose "Manual" rather than "Use entire disk" during the partitioning phase of Ubuntu installation - so no worries there. You will need to specify a mount point and not format it of course.

Comparing your boot.ini against the one on Microsoft's site is misleading - as you have a combination of SCSI and IDE - although having said that the lines are correct for the first IDE drive, first partition:

multi(0)disk(0)rdisk(0)partition(1)

Ignore the first two parts - they relate to the interface type and how the booting is handled with respect to BIOS. The last two parts are the physical drive connection and the partition number. 

I'd check that your Windows drive is partioned as HDA1 and not something odd like 2 (one of my laptops is configured this way after resizing the drive), before we go any further.

EDIT One other thing, was windows installed on the drive in a folder called "Windows"?

---

### Post by flamingsole on 2007-07-19
When I look in GRUB, it says Windows is on partition 2, hd1.

---

### Post by ddrichardson on 2007-07-19
Excellent, your boot.ini is pointing at the first partition on drive one. That's why Windows isn't booting.

Change lines reading *multi(0)disk(0)rdisk(0)partition(1)* to *multi(0)disk(0)rdisk(0)partition(2)*.

---

### Post by flamingsole on 2007-07-19
The Ubuntu live CD tells me that boot.ini is read only and I don't have permissions to change it. Without it being a local installation, how can I edit the boot from Ubuntu?

---

### Post by ddrichardson on 2007-07-19
What about from the Windows Recovery Console?

---

### Post by flamingsole on 2007-07-19
I think I have to use bootcfg to edit boot.ini from the Recovery Console. I tried bootcfg /rebuild, and also bootcfg /add. I get the message: "Error: Failed to successfully scan disks for Windows installations. This error may be caused bya  corrupt file system, which would prevent Bootcfg from successfully scanning. Use chkdsk to detect any disk errors.

When I ran chkdsk, I get the error "The volume appears to contain one or more unrecoverable problems.

Is there maybe a way within the Ubuntu live CD that I can get permissions to edit boot.ini?

Thanks so much for your help thus far. I greatly appreciate it.

---

### Post by ddrichardson on 2007-07-19
You probably won't be able to do it from Ubuntu without a lot of messing around. There are live cd distros that support NTFS writing by default, such as [Puppy]("http://www.puppyos.com/test/") (latest beta). That will allow you to alter the file.

If that doesn't work then you need to think about a full re-install of Windows from a formatted drive. Backup is vital here.

Remember to install Windows before Ubuntu as Windows (except Windows 2000) overwrites the MBR.

No problems helping - I spent 45 minutes last night  on the phone trying to work out how my mother had managed to get her display to invert itself. :-)

---

### Post by flamingsole on 2007-07-19
I created and booted from a live CD of Puppy, and attempted to edit the boot.ini file on the Windows drive. I saved it, and it seemed to save properly, but then when I rebooted I still got the "Error loading operating system" message. I'm assuming it's time to format and reinstall Windows?

After I do this, I guess I'll need to format the second hard drive and install Ubuntu on it?

---

### Post by ddrichardson on 2007-07-19
Before you do that, try going into BIOS and autodetecting drives first.

---

### Post by flamingsole on 2007-07-19
BIOS detects both drives.

---

### Post by ddrichardson on 2007-07-19
I'm a little thrown by this as the message you're getting is usually associated with BIOS problems relating to LBA and disk size during XP installation. There's a knowledge base article (326676) on it, although it doesn't really offer a non-destructive solution.

Obviously the removal of the drive and the refitting has caused a problem, the setup problem is sometimes rectified by changing the drive's translation from Auto to Large in BIOS and rebooting.

Try this first and if you've no joy then its time to re-install.

---

### Post by MythicalVax on 2007-07-20
> **flamingsole said:**
> 
I checked c:\boot.ini from the mounted disk. It appears as follows:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" 1 /fastdetect

The only thing different there from the example on Microsoft.com is the 1 that's right before /fastdetect. I'm not sure if this was there before, but Ubuntu says it does not have permissions to change it.


[COLOR=Red]** Well, the 1 may be a problem or not (BUT PROBABLY IT IS).**[/COLOR]
As you can see in my C:\Boot.ini, no 1 is set, thus I think you can safely remove it.
[INDENT][I] [boot loader] 
timeout=30 
default=C:\Boot\UBUNTU.GNU 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional       " /fastdetect /NoExecute=OptIn 
C:\Boot\UBUNTU.GNU=" GNU/Linux UBUNTU 7.04 LTS - Feisty Fawn "
[/I][/INDENT]I have experienced very cryptic and horrible and never seen windows messages in 20 years of windows just for a single and wrong character in boot.ini just a few months ago, thus _I think that removing the 1 may help you to recover from incredible messages that may truly distort you from the real problem._

> **flamingsole said:**
> 
Is there maybe a way within the Ubuntu live CD that I can get permissions to edit boot.ini?


Yes, there is. It is not a matter of permissions, but of file system you need to run: you need to run **ntfs-3g** tools. (I still do not understand why they are not automatically delivered in the distro since reading and writing has been working safely for a long time, by now...)
You simply need a usb drive, even a small one, let's say a 128/256 Mb one to reformat as a special Linux partition.
You shall save your configuration there and then you will be able to even download and add your extensions (such as ntfs-3g) as well as the minimum repository updates you require/need to have all your utilities up and working.
(Gonna look for a link on how to do it: it will be a matter of 1 or 2 reboots to have everything you want on your usb key/drive).

When you will be able to run your ntfs-3g you will be able to read and write to evevery ntfs partition, on your computer as well as on any other you will be running your live distro with your usb key (a great and familiar recovery tool indeed).

(Sorry for taking a long time to answer, but I got no time)

---

### Post by flamingsole on 2007-07-20
Thanks for that suggestion. I edited and saved boot.ini again, and nothing changed. I'm going to go ahead and format the Windows drive, and reinstall Windows. Currently, I'm moving important data from the Windows drive to my wife's laptop. The Ubuntu live CD fortunately recognizes that the two systems are networked, so it's going pretty smoothly.

After I reinstall Windows and get the data on there that needs to be there, I suppose I'll try again to install Ubuntu. Other than not removing any drives from the system, are there any brief pointers you'd like to share? I had found what I thought was a very thorough tutorial on dual-booting XP and Ubuntu, and followed all the steps to the degree that I've posted them here. Obviously I missed something, though.

Here's hoping for better luck this time...

---

### Post by ddrichardson on 2007-07-20
To be honest I've never had many problems with dual booting as long as I've installed Windows first. I hope you have more luck this time around. ;-)

---

### Post by MythicalVax on 2007-07-23
Sorry for your final decision, flamingsole.
Just for a future reference, this is a [link]("http://www.cyberciti.biz/tips/ubuntu-linux-live-cd-save-data-desktop-information-on-usb-device.html") to the persistent ubuntu live configuration.
FIY - With regard to it (and my live Dapper), the label I successfully adopted was **casper-rw** instead of caper-cow.

---

### Post by flamingsole on 2007-07-23
So, I'm wondering if the following scenario would work. I've started moving in this direction, and am currently installing Windows in the hopes that it will work.

Master Hard Drive:

Partition 1: empty for now - 200 Megabytes
Partition 2: Windows XP

Then, installing Ubuntu on the Slave drive, telling it that the empty partition on the Master drive is where /boot should be installed. I've seen this as a recommended solution for those who are doing a clean install of both operating systems. It is said that after Ubuntu is installed, the first partition where /boot is added will become active, and will allow me to run Windows and Ubuntu.

Any thoughts on the possibilities of success with this?

Thanks.

Jon

---

