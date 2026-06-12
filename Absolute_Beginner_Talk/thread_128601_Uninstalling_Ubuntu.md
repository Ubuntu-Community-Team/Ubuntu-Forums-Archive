---
title: "Uninstalling Ubuntu"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by dave154 on 2006-02-11
hey

i had just installed ubuntu after partitioning my windows hardisk

other members of my family have found some problems with using xp, though i inisist it isnt connected with the installation of ubuntu, i have to unfortunately uninstall it

i've heard that just deleting the partition creates problems with the boot process (something about boot sector with GRUB)

im wodering what's the correct way to uninstall ubuntu from my system

---

### Post by eriefisher on 2006-02-11
I think the cleanest way is to back up all data and settings etc and reload windows fresh. This would be a fresh clean install which is regularly needed with windows anyway.

eriefisher

---

### Post by dave154 on 2006-02-11
i guesss i was looking for a more simple solution... i have gparted on live cd.. i i just deleted ubuntu partition.. would have solve or create problems

---

### Post by aysiu on 2006-02-11
Microsoft has instructions for this right [here](http://support.microsoft.com/default.aspx?scid=kb;en-us;314458).

---

### Post by akniss on 2006-02-11
If you just delete the ubuntu partition, you'll have to 'fix' the MBR so that grub doesn't have trouble.   I think the easiest way to do what you want would be to first use your windows install disk to rebuild the MBR to its preferred state.  (I think if you search the forums for fixmbr you can find instructions to do that.)  After the machine is booting into windows while ignoring ubuntu, you can use the disk management in XP to delete and recreate the ubuntu partition(s) to NTFS.  The only caveat to this method would be that your family will have to get used to having a separate partition on the hard drive.  (its best to do this with windows anyway, so you can store your files separate from the OS.)  However, when windows doesn't return to normal, they may still blame you since the partitions are still different than they were... and if you reinstall a fresh windows, they will say they were right since reinstalling made it 'work' again.  no win situation, i suppose.

---

### Post by SumoJim on 2006-02-11
If you haven't already. Maybe you could first find out what they say XP is doing funny and reasearch the problem eg. google it to see if anyone else has had that problem... If you can fix the problem with XP then maybe your family will let you keep Ubuntu.

---

### Post by eriefisher on 2006-02-11
[QUOTE=SumoJim]If you haven't already. Maybe you could first find out what they say XP is doing funny and reasearch the problem eg. google it to see if anyone else has had that problem... If you can fix the problem with XP then maybe your family will let you keep Ubuntu.[/QUOTE]

I agree, this is most likely a XP problem with a fix somewhere. That would be the first step if you want to keep Ubuntu.

eriefisher

---

### Post by dave154 on 2006-02-11
thanks for the help guys... im going through the process of fixmbr, one thing though... the unallocated partition, the one that use to have linux on it, can i cmobine that with the windows partition? or at least part of it with windows (i have 12 gigs just sitting around). gparted keeps giving an error meassage when i try to resize the ntfs to its full disk size

thanks again, cant wait to get my own computer to put linux on with no fuss

---

### Post by eriefisher on 2006-02-11
You could just format it as a FAT32 partition. Windows and Linux will read that. It will look like another drive in windows with another letter. This way after you fix the original XP problem you still have a partition to reload Ubuntu onto. Maybe.

eriefisher

---

