---
title: "[SOLVED] urgent - external disk doesn't mount"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by kleo skywalker on 2008-01-09
So I urgently need to get my data off this portable hard disk. I plugged it in the USB port, but get some kind of an error message saying it can't be mounted.
The text in the error message box won't get selected so I'm attaching a screenshot.

In case this helps, the manual on the CD that came with the disk says the following about Linux:
> Driver Installation for LinuxTM Kernel 2.4, or Later
No drivers are required. Plug your StoreJetTM 2.5 SATA into a USB port and mount it.
1. First create a directory for the StoreJetTM 2.5 SATA.
               Example: mkdir /mnt/Storejet
2. Then, mount the StoreJetTM 2.5 SATA.
               Example: mount &#8211;a &#8211;t msdos /dev/sda1 /mnt/Storejet

I'm not sure what means. The manual also says that its NTFS by default.

Could someone please help me with this asap? I'm sitting here with the disk plugged in but since it won't mount, I can't unmount/eject it because I can't risk the data or the borrowed disk.

Thanks.

---

### Post by Pevichaey5 on 2008-01-09
install i think its called FOS or FOSS it allows you to read/write NTFS file systems

---

### Post by kleo skywalker on 2008-01-09
> **thexero said:**
> install i think its called FOS or FOSS it allows you to read/write NTFS file systems

I searched Synaptic for FOS and FOSS - no results.

---

### Post by Pevichaey5 on 2008-01-09
check [here](http://sourceforge.net/project/showfiles.php?group_id=13956)

---

### Post by kleo skywalker on 2008-01-09
> **thexero said:**
> check [url=http://sourceforge.net/project/showfiles.php?group_id=13956]here[/rul]

Thanks, I'm looking at this but don't seem to get it.
I've crossed a mountain range of stupidity and bother to recover data from a damaged hard disk, and want a simple way to mount this external disk and see my data.

---

### Post by vanadium on 2008-01-09
This is a common problem. It is caused by unproperly disconnecting the drive, but also by disconnecting the drive from a Windows system in hibernation (congratulations, Microsoft!).

Like the error message tells you, the ntfs filesystem on the drive is unclean and needs to be checked. Ubuntu won mount a damaged ntfs system because that could corrupt it further.

The drive will need to be connected to a Windows system (the ntfs file system is a proprietary file system of Microsoft, so open source developers do not know all the details of the file system). There, it could be sufficient just to properly disconnect the drive or shutting down Windows completely for the drive to be clean again. To play it safe, i would run a disk check using the Windows tools, then disconnect it properly.

---

### Post by kleo skywalker on 2008-01-09
> **vanadium said:**
> This is a common problem. It is caused by unproperly disconnecting the drive, but also by disconnecting the drive from a Windows system in hibernation (congratulations, Microsoft!).

Like the error message tells you, the ntfs filesystem on the drive is unclean and needs to be checked. Ubuntu won mount a damaged ntfs system because that could corrupt it further.

The drive will need to be connected to a Windows system (the ntfs file system is a proprietary file system of Microsoft, so open source developers do not know all the details of the file system). There, it could be sufficient just to properly disconnect the drive or shutting down Windows completely for the drive to be clean again. To play it safe, i would run a disk check using the Windows tools, then disconnect it properly.

Lucky I have access to a Windows system. I'll try this right away. If just disconnecting it properly doesn't work, what checking tools do I run?
Also, since the disk can't be mounted on my Ubuntu system, can I just unplug it?

---

### Post by kleo skywalker on 2008-01-09
Please excuse my impatience, but I'm sitting with that disk plugged in!
If it's not mounting (and therefore can't be unmounted), can I just unplug it or is that risky?

---

### Post by Pevichaey5 on 2008-01-09
to be safe, i would turn off the device it is pluged in to

---

### Post by tigerplug on 2008-01-09
> **thexero said:**
> install i think its called FOS or FOSS it allows you to read/write NTFS file systems

I thought NTFS support was included in Gutsy Gibbon?

---

### Post by tigerplug on 2008-01-09
> **kleo skywalker said:**
> Please excuse my impatience, but I'm sitting with that disk plugged in!
If it's not mounting (and therefore can't be unmounted), can I just unplug it or is that risky?

Yes you can unplug it if you are not reading/writing to it and HAVE NOT read or wrote to it since you plugged it in ;)

---

### Post by Pevichaey5 on 2008-01-09
i might be a little behind times, but i haven't tried to read/write an ntfs partition in a while as i have no need to, but i'll find out tonight if support has been added if so good news :S kinda lol

---

### Post by kleo skywalker on 2008-01-09
vanadium, thanks a lot. I plugged it into a Windows system, did a safe remove and plugged it into my Ubuntu system. I'm copying my data now :D

---

