---
title: "Ubuntu 14.04 Hostile to Boot from Windows Server Disc"
date: 2014-06-28
forum: Any Other OS
---

### Post by Robert_W_Murphy on 2014-06-28
Hopefully this is a good place for this question although it maybe could fit in the Installations and Upgrade general category.

I recently acquired a Dell PowerEdge 2900 for my own learning etc. I was going to have to wipe the current Windows Server installation out and rebuild it so I figured this would be a great time to just see what the Ubuntu server install process is like (I dual boot Ubuntu Desktop and Win7 on my laptop). I got it installed fine everything seemed great I poked around with a few commands and decided that I was ready to get back to my Windows Server.

I inserted my Windows Server 2008 R2 Enterprise disc into the drive and rebooted. When i was prompted I manually entered the BIOS boot options screen and selected to boot from the optical drive. It went to a blinking cursor and sat there for a bit like it was doing something but nothing ever happened. Then all of a sudden it kicked me into Grub and booted Ubuntu server. So I shutdown and tried again but this time I first checked the BIOS boot settings and found that the optical drive is set to boot before the HDD so I just let it run through the boot process and it just skipped right on past the optical drive like there was nothing there and went right into Grub and either went right into Ubuntu server or if I hit the up or down arrow fast enough it would let me select between Ubuntu server or some other options none of which allowed booting from the CD/DVD drive.

I thought maybe there was a problem with the disc so I took it out and plopped it into just a normal PC I had sitting next to me and tried booting the disc and it booted and loaded into the beginning of setup just fine so the disc works. I cant seem to get Grub or Ubuntu to allow me to boot from the CD/DVD drive, I haven't tried to see if its hostile to the same Ubuntu disc i used to install or not. 

I have seen multiple recommendations to restore the Windows boot loader but they almost all want you to start by booting a Windows disc which I cant do. I have dual booted desktops for years but this is the first time i have tried a *nux Server version. Does the server version do something different that I don't know about? Any advice? Thanks in advance!

---

### Post by Bucky Ball on 2014-06-28
*Thread moved to **Other OS/Distro Support**.*

Welcome. No. The reason your Win server disk is not booting would have nothing to do with your Ubuntu install. This is about the BIOS and the DVD, all happening BEFORE grub has anything to do with it. Grub has nothing to do with booting your Win disk.

---

### Post by Robert_W_Murphy on 2014-06-28
That's what I figured but it has booted other discs fine in the past, it booted the Ubuntu disc fine (I burned the iso myself), I booted the Win 2008 R2 disc fine on two other machines (I burned the iso for this as well on the same machine I created the Unbuntu disc on) one of which I completed an install. Matter of fact before I ran the Ubuntu server install I had booted off this same disc but decided to go ahead and try the Ubuntu install and now I'm having this problem. 

Is there some way to maybe add a CD/DVD boot option to the Grub menu along with the server option and I could try that?

---

### Post by Tadaen_Sylvermane on 2014-06-29
> **Robert_W_Murphy said:**
> That's what I figured but it has booted other discs fine in the past, it booted the Ubuntu disc fine (I burned the iso myself), I booted the Win 2008 R2 disc fine on two other machines (I burned the iso for this as well on the same machine I created the Unbuntu disc on) one of which I completed an install. Matter of fact before I ran the Ubuntu server install I had booted off this same disc but decided to go ahead and try the Ubuntu install and now I'm having this problem. 

Is there some way to maybe add a CD/DVD boot option to the Grub menu along with the server option and I could try that?

Is the server running UEFI or BIOS? If UEFI I have had a hell of a time getting a UEFI installation to boot anything other than itself at power on, even manually selecting something else at the boot menu. The only way I have been able to get an installer to boot under UEFI (when Ubuntu is already installed there ) is efibootmgr. Using that delete the 0000 option, should be just "ubuntu". Will boot fine after that is gone.

---

### Post by oldfred on 2014-06-29
Windows always wants a NTFS partition with boot flag or unallocated space. If drive is fully allocated to Linux Windows cannot see it and may think you do not have a  drive available to install into?

---

### Post by Robert_W_Murphy on 2014-06-30
> **Tadaen_Sylvermane said:**
> Is the server running UEFI or BIOS? If UEFI I have had a hell of a time getting a UEFI installation to boot anything other than itself at power on, even manually selecting something else at the boot menu. The only way I have been able to get an installer to boot under UEFI (when Ubuntu is already installed there ) is efibootmgr. Using that delete the 0000 option, should be just "ubuntu". Will boot fine after that is gone.

I don't remember when they started using UEFI but this machine is probably 4 or 5 years old so I would guess probably traditional BIOS but I will definitely check out this option. Thanks for the idea.

---

### Post by Robert_W_Murphy on 2014-06-30
> **oldfred said:**
> Windows always wants a NTFS partition with boot flag or unallocated space. If drive is fully allocated to Linux Windows cannot see it and may think you do not have a  drive available to install into?

I did format the whole drive to Ubuntu so I will check into this as well and since I don't care if the Ubuntu install survives I won't feel bad if I damaged the Ubuntu install re-partitioning the drive in part to NTFS.

---

### Post by Robert_W_Murphy on 2014-07-03
Thanks for everyone's advice and help but now I am having a totally unrelated problem. I finally remembered about GParted and I downloaded and burned the Live CD of it and used it to nuke the partitions on the Raid Array and I for them reformatted to NTFS. I then found out that even though I had nuked the partitions and reformatted them that when I used a DVD to boot, which Windows Server 2008 R2 Enterprise is...it said it didn't understand the file system. I then borrowed a copy of Server 2003, which is on a CD, from my workplace and it would let me boot into setup but now for some reason it doesn't detect that there are any drives. I went in and nuked the Virtual Disc in the Array and recreated it and reinitialized it so that everything would be fresh and clean but still no luck. It boots from the CD loads some of the initial files but when I tell it to install a fresh copy of Server it says it cant detect any discs.

Anyway long and short, it appears that something about the Ubuntu install and Grub were having some minor affect on how it was acting but the main problem appears to be that it doesn't understand a DVD for booting. I would see if there was a BIOS update but I cant get anything to install as now it doesn't even see that there is a disk installed in the system. Thanks for the help!:p

---

### Post by Bucky Ball on 2014-07-03
It would be a good idea to mark this as solved and start a new thread with a descriptive title for you new issue(s). It will increase your chances of getting support. ;)

---

### Post by Robert_W_Murphy on 2014-07-05
Bucky, I have marked it as complete and thanks for the advice I'm still trying to work through the other issues myself yet. Try not to get help until I absolutely have to...have learned a lot of things that way over the years.

---

### Post by Bucky Ball on 2014-07-05
Sure. Good luck. ;)

---

