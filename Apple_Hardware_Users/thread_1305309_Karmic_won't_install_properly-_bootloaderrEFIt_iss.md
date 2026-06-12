---
title: "Karmic won't install properly- bootloader/rEFIt issues, it appears"
date: 2009-10-29
forum: Apple Hardware Users
---

### Post by spencercarran on 2009-10-29
I'm running a MacBook 3,1, Ubuntu and assorted derivatives have historically installed without too much trouble on this machine.

Installing Kubuntu Karmic seemed to go fine, but when I rebooted rEFIt showed an icon for "Boot Legacy OS" where Tux should have been, and of course failed to boot from that partition. Partition Tool in rEFIt does not offer to fix the problem like it usually does.

I have a sneaking suspicion this is related to the adoption of GRUB 2 in Karmic. Can anyone confirm? Has anyone run into a similar situation, or have any idea how to get Karmic running on a MacBook?

---

### Post by itagaki on 2009-10-29
exactly the same here. i installed grub onto my ubuntu ext4 partition.

```

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    126319094  Mac OS X HFS+
 3      126319095    230533938  Basic Data
 4      230533939    234440189  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    126319094  af  Mac OS X HFS+
 3 *    126319095    230533938  83  Linux
 4      230533939    234440189  82  Linux swap / Solaris

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 126319095:
 Boot Code: Unknown, but bootable
 File System: ext3
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 230533939:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris
```

---

### Post by spencercarran on 2009-10-29
^My partition table is identical to yours, minus the swap.

---

### Post by ColdLunch on 2009-10-29
I'm getting the same problem here with a Macbook 1,1.

---

### Post by spencercarran on 2009-10-29
So we've confirmed this issue exists. And yet there are several threads of people with other Karmic problems, implying that their installations worked fine... what are they doing differently than us?

I may just reinstall using the old grub and see if that fixes it. If it does, I'll post back here.

---

### Post by hanzomon4 on 2009-10-30
Remove refit and just hold down the option key on boot. I'm on the same hardware without any problems.

---

### Post by Derrick Zuk on 2009-10-30
I am also having this issue on my MacBook Pro (4,1). I installed grub onto my Ubuntu ext4 partition. Is this a problem with refit? Do I need to wait for an updated version? I can't remove refit as I also have a Windows partition I use.

Thanks..


(Edit)
By the way, I installed the 64-bit version of 9.10. Not sure if that would make a difference. In the past, I've only tried 32-bit.

---

### Post by linuxopjemac on 2009-10-30
Is this problem only occurring with kubuntu, or also with ubuntu 9.10?

---

### Post by Derrick Zuk on 2009-10-30
> **linuxopjemac said:**
> Is this problem only occurring with kubuntu, or also with ubuntu 9.10?

My problem is with Ubuntu 9.10.

I did end up getting into the system by rebooting, holding the option key, and selecting the Windows option from the boot camp menu. It loaded grub and I was able to boot into Ubuntu.

I've looked at a couple of other threads around and I think the problem might be the new ext4 file system. Refit might not support it yet? I'm not sure exactly, but if refit won't work for some time, are there alternatives that support triple booting and will boot into an ext4 partition with grub2 (if either of those is the problem)?

Thanks..

---

### Post by linuxopjemac on 2009-10-30
what happens if you set the boot flag to the root partition of your Linux system with gparted with the LiveCD and then in rEFIt you go to a terminal and sync manually with "gptsync", reboot and try again ?

---

### Post by Derrick Zuk on 2009-10-30
> **linuxopjemac said:**
> what happens if you set the boot flag to the root partition of your Linux system with gparted with the LiveCD and then in rEFIt you go to a terminal and sync manually with "gptsync", reboot and try again ?

Why with the LiveCD? If I can boot into Ubuntu from the Windows boot camp option, can I do it directly from there? I'll try it out.

(Edit)
Isn't the boot flag already set to the root partition?

---

### Post by linuxopjemac on 2009-10-30
The boot flag is probably set already, but I read that if you just have a look with gparted then some magic occurs...just try it out, it won't harm.

---

### Post by Derrick Zuk on 2009-10-30
> **linuxopjemac said:**
> The boot flag is probably set already, but I read that if you just have a look with gparted then some magic occurs...just try it out, it won't harm.

You were right. That did the trick. There wasn't any flag on the Ubuntu partition, so I set it to the boot flag and manually synced refit's partition table. I can now boot into Ubuntu 9.10 from the Legacy OS option in refit. It's still kind of annoying that it shows up as Legacy OS instead of Linux, but at least it works. Thanks so much for your help!

---

### Post by linuxopjemac on 2009-10-30
Nice! I will install Karmic Koala the coming weekend on my MacBook 2,1. I wanted to have this sorted out before that :D.

by the way, I don't know how to change the behaviour of rEFIt from Legacy OS to Linux. Maybe someone else knows this ?

---

### Post by linuxopjemac on 2009-10-30
[http://ubuntuforums.org/showthread.php?t=1298801](http://ubuntuforums.org/showthread.php?t=1298801)

---

### Post by spencercarran on 2009-10-30
> **linuxopjemac said:**
> what happens if you set the boot flag to the root partition of your Linux system with gparted with the LiveCD and then in rEFIt you go to a terminal and sync manually with "gptsync", reboot and try again ?

Running gptsync tells me that the partition tables are already synchronized, so it does nothing. Holding down option and selecting Windows also fails to boot.

It is unlikely to be a Kubuntu-specific problem, all *buntu variants use the same grub.

Specifically: I put everything for my installation in one ext4 partition, including telling it to install the bootloader there. This has always worked in previous versions of Ubuntu.

---

### Post by natrium42 on 2009-10-30
To show linux icon in rEFIt with GRUB2, just hex edit refit.efi:
Change byte at 0x012CE from 0x00 to 0x0D
Change byte at 0x310B2 from 0x00 to 0x0D

Or you could wait for the next version of rEFIt.

About the non-rEFIt way... it's too annoying to hold option key IMO...

---

### Post by hanzomon4 on 2009-10-31
I find it elegent... don't like muddying up my system with needless bits. REFIT is great by the way, I just no longer have a need for it.

---

### Post by linuxopjemac on 2009-10-31
can't seem to mount the GPT partition with mount /dev/sda1 /mnt/tmp
I don't see anything in there, anyone ? I like to hexedit that file...(see up)

---

### Post by linuxopjemac on 2009-11-02
can anyone help me mounting and editing that refit.efi file please ?

---

### Post by natrium42 on 2009-11-02
> **linuxopjemac said:**
> can anyone help me mounting and editing that refit.efi file please ?You can do it through OSX.

---

### Post by Leet Sher on 2009-11-02
For some reason, rEFIt does not sync partitions at all for Ubuntu 9.10. You have to use the LiveCD and install gptsync. After installed, go into the terminal and type:
```
sudo gptsync /dev/sda
```

---

