---
title: "grub error 29 after deleting ubuntu partition"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by brallan on 2007-03-24
major screw up - i installed on my aging laptop (NO CDrom) as a dual boot XP/ubuntu then discovered there really wasn't enough room on the harddisk (20GB now in 2 parts + a swap) to comfortably use both. Though i am happy with ubuntu, i share it with a frriend, so I needed to go back to just XP.  i thought i would be ok deleting the partitions with partition magic, and just living with the grub boot screen even though it would no longer be necessary. I figured that grub was installed on the MBR of the first partition. I must be very wrong about this, because after deleting the partition, grub is dead! This is a REAL bummer since now i can't even reinstall XP now that the CDROM is broken.

does anyone know if i can fix grub or restore my XP MBR?  It  DOES have a floppy.

thanks,
brian

---

### Post by Wally68 on 2007-03-24
Try [this]("http://www.ntfs.com/mbr-damaged.htm"), I just googled it.

---

### Post by Herman on 2007-03-24
Hello brallan,
> major screw up No, it's a trivial matter.
We have a MBR in the first sector of our hard disks, (every hard disk is given one as soon as the first partition is created).  The MBR and the first track of the hard disk (63 sectors) do not belong to any operating system and they are not formatted with any file system.
Regardless of whether you happen to have Windows or not, the first operating system's file system never starts until sector 63.
So the MBR does not belong to Windows, it belongs to you or I or whoever owns the hard disk.

All bootloaders come in two or three stages (sort of like an insect). The MBR is far too tiny for a whole bootloader to fit into, only 446 bytes of space are allowed there, because the partition table takes up 64 bytes, and one sector is 512 bytes. Therefore, regardless of whether you use Grub, Lilo, or Windows NTLDR bootloaders, the real (main, useful) part of the bootloader lives in your operating system partition. Only a very small 446 byte 'stage1', or 'IPL' is the only part of any bootloader that can be written to such as small space as the the hard disk's MBR. That's basically just a 'pointer' to make the MBR point to the desired bootloader in the appropriate partition.

Now that you have deleted the Ubuntu partition, you have deleted grub along with it. The 'IPL' in your MBR is just pointing into empty space. So you can't boot from the hard disk's MBR right now, but you can from a floppy disk or a CD.

Your Windows bootloader is still fine, and so is your Windows boot sector, (the first sector of your WIndows partition). All you need to do is use a CD or a floppy disk to re-write the tiny wee IPL code or 'stage1' for the Windows NTLDR bootloader to the little space in your MBR. That will make your MBR point to your Windows partition once more. 
There are many way to do that, and they are all quite simple. Take your pick from any of the methods listed in the following link: [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

I agree with Wally68, (nice link, Wally68) but that page only has this at the bottom of it to tell you what to do about it, 
> The simplest way to repair or re-create MBR is to run Microsoft's standard utility called FDISK with a parameter /MBR, like
    A:\> FDISK.EXE  /MBR
FDISK is a standard utility included in MS-DOS, Windows 95, 98, ME.You might want to refer to the link I gave you for more details about exactly how do do that, unless you choose one of the other things listed there instead. 

Regards, Herman :)

---

### Post by brallan on 2007-03-24
wow, thanks! FANTASTIC! well, i downloaded a nice little floppy image called smart boot manager, and as soon as it booted up and i chose the partition, it booted XP! now i guess i will just be booting from a floppy until i get some other boot manager installed. THANK YOU THANKYOU THANK YOU!

---

### Post by Herman on 2007-03-24
GAG Boot Manager is one of the options listed on that page I already linked you to. GAG can run from a CD or a Floppy or be installed to MBR. It installs to MBR and the first track of the hard disk, so it doesn't get deleted when you delete a partition. It's free and it's only a small download, and it's Open Source, so you can trust GAG Boot Manager. Lots of other Ubuntu users already use it and like it. You might be interested in taking a look at it too. :)

Regards, Herman :)

---

### Post by brallan on 2007-03-24
i wound up downloading the bootdisk.com 98SE OEM and doing the fdisk /mbr option. i was a bit surprised that it was downloadable, and that it indeed worked with XP. Thanks sooo much for your excellent advice, Herman.

brian

---

