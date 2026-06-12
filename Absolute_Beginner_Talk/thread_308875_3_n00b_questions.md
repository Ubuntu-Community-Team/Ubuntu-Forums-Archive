---
title: "3 n00b questions"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by turrican_dx on 2006-11-28
Hello, I'm yet another Linux convert, but so far I'm familiarising myself with Ubuntu usage, and I won't install it just yet. However, please take a moment to read my planned installation steps. My PC is part of a Windows Active Directory domain.

1- Remove older HD, connect newer one, then insall Ubuntu 6.10
2- Connect older HD to Win2K3 server, set up shares to transfer data later (burning to DVDR is troublesome for me)
3- Set up Kerberos authentication and/or configure Samba
4- Re-connect WinXP HD and modify boot-loader to include other OS.

Now, I have a few questions that I'd appreciate answering.

1- Can I copy my old files via Windows share if I successfully authenticate against Active Directory (via installign Kerberos client - I haven't checked but Ubuntu has one I reckon)? I want NTFS and ext partitions to be mutually exclusive.

2- Is it feasible to modify the GRUB loader? (I currently have zero info about Linux MBR - or the equivalent of it) Would Windows like it, or is the ideal situation for Windows to be on the primary drive (and subsequently install Linux and let it modify Windows MBR)?

3- Does Ubuntu 6.10 include ext4? Is this the best thing since sliced bread? or should I stick with good old ext3?

Thanks for your time. :-D

---

### Post by igknighted on 2006-11-28
Why not just transfer the data directly from the windows HD?  Taking it out and transferring from a server seems like a rather ridiculous step unless you have a specific reason to do so.  Ubuntu can install onto your other HD then you can just transfer from one drive to the other, way easier.

---

### Post by turrican_dx on 2006-11-28
I'm paranoid, I crash hard disks pretty frequently. That's why ;) Also my PC has to be in the domain to access shared resources (and vice versa, where applicable).. I know it won't be a walk in the park but I really want to become an Ubuntu user :D Another reason for one of my questions about the boot-loader is that I want Windows to be a secondary disk (mostly for gaming), so basically I'm asking if it's feasible to add another OS to Linux MBR at will (in the Windows universe it's rather easy to add or remove OS entries from boot.ini)

---

### Post by CatKiller on 2006-11-29
Personally I'd be tempted to ignore that Win2K3 server altogether and instead use a procedure like

Swap XP hard drive for new hard drive
Install Ubuntu on new hard drive
Add XP drive as slave
(Optional)Edit menu.lst (similar to boot.ini, but for GRUB) to add an XP boot option - you could instead use your BIOS settings to determine which OS to boot from, which keeps the two OSes even more distinct
(Optional)Use [these instructions]("http://www.psychocats.net/ubuntu/mountwindows") to mount your NTFS partition(s) in Ubuntu as read-only.

I don't know anything about Active Directory or Kerberos, which is probably why I'd not bother using it for file transfer :)

---

### Post by igknighted on 2006-11-29
Ok, what you are proposing as far as the file transfer should work, however I will make one more plug for leaving your HD as is.  When you install Ubuntu (I would recommend using the alternate install disk, esp. if you are paranoid.  It's a text based installer and not as pretty as the live CD one, but its more stable) it will show both hard drives in your computer.  You could remove it before this stage, but it will create more work later on (plus, any time you handle a hard disk you are risking data loss).  Select the disk you want Ubuntu on and let it set up the partitions.  You can then review and make sure that nothing important is being over written.  You may also select a mount point for the windows disk (I use /windows... if you are new to linux there are no drive letters, to /windows would then be roughly equivalent to D:/).  After confirming the partition setup, the install should proceed (you may need to answer a few more questions first) and when it is done it will ask you where to install GRUB (the bootloader).  It should show you that Windows is also installed, and if it does then it is safe to overwrite the MBR, you can boot into both OS's from GRUB.  To access data from the windows drive once in Ubuntu all you need to do is navigate to the /windows folder.  It is certainly possible to set up access to the windows disk after the install and also add it to grub, but it is significantly easier to let Ubuntu do the work for you at install.

---

### Post by Sef on 2006-11-29
> 3- Does Ubuntu 6.10 include ext4? Is this the best thing since sliced bread? or should I stick with good old ext3?



No, it doesn't.  Fiesty Fawn might though.  I wouldn't install it now as installing ext4 would wipe out the data on your partition and I don't know how stable it currently is.  I will upgrade to ext4 as it matches one feature of reiferfs that I like - fragmentation should become a thing of the past with ext4.

---

### Post by turrican_dx on 2006-11-29
Many thanks to everyone who responded :) I think I'll stick to dual boot via BIOS, and ext3 (since Edgy doesn't have v4). Mounting NTFS volume for read-only purposes is very safe from what I gathered, which is excellent.

as from the AD domain I have to join it so I reckon that means lots of late nights at the shell I guess :mrgreen:

---

