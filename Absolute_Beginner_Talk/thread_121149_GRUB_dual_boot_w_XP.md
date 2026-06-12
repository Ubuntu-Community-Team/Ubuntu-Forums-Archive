---
title: "GRUB dual boot w/ XP"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by AirIntake on 2006-01-24
Ok, I had XP on my primary hard drive and I decided to install Ubuntu on my secondary drive. During the installation I remember being asked where I would like to install GRUB, and I chose my primary drive with XP on it, thinking that if the Ubuntu install failed, that it would still look on my primary drive, find GRUB, and boot into XP anyways regardless of how my Ubuntu drive was doing. Upon messing around with GRUB, it appears that the GRUB boot file is on my secondary Ubuntu drive in /boot/grub/menu.lst. My problem is, what if my Ubuntu drive fails, or I remove it/format it to do something else with it (it is an old drive and could fail). I just don't want to lose the ability to boot into XP just by removing a drive that doesn't even have XP on it. Can somebody offer some insight?

---

### Post by Kapre on 2006-01-24
[QUOTE=AirIntake]Ok, I had XP on my primary hard drive and I decided to install Ubuntu on my secondary drive. During the installation I remember being asked where I would like to install GRUB, and I chose my primary drive with XP on it[/quote]

Airintake - I think you just deleted your XP. If what you did was install Ubuntu on your primary drive with XP on it, it will be overwritten (thus you loose your XP).

You can also check if you still have XP (which I'm not so positive about) is when the GRUB loader boots (see if you have choices).

K

---

### Post by AirIntake on 2006-01-24
XP and Ubuntu both have their own HD and I can dual boot into XP and Ubuntu just fine right now. I'm just wondering what will happen if I remove my Ubuntu drive, which seems to have GRUB on it (even though I thought I chose to put it on my primary (XP) drive). I guess what I want is to be able to remove my Ubuntu drive without losing the ability to boot into XP.

---

### Post by linuxden on 2006-01-24
[QUOTE=AirIntake]XP and Ubuntu both have their own HD and I can dual boot into XP and Ubuntu just fine right now. I'm just wondering what will happen if I remove my Ubuntu drive, which seems to have GRUB on it. I guess what I want is to be able to remove my Ubuntu drive without losing the ability to boot into XP.[/QUOTE]

Then you would just have to reeinstall the windows boot loader using the windows XP CD... Its not a problem.... And very easy to do... ;o)

---

### Post by Kapre on 2006-01-24
[QUOTE=AirIntake]XP and Ubuntu both have their own HD and I can dual boot into XP and Ubuntu just fine right now. I'm just wondering what will happen if I remove my Ubuntu drive, which seems to have GRUB on it. I guess what I want is to be able to remove my Ubuntu drive without losing the ability to boot into XP.[/QUOTE]

Airintake - Misread your 1st post. Anyways, if you say that you install GRUB in you primary HD (MBR) and you'll remove (which you can test by removing the power to your 2nd HD so it wouldn't be detected) the 2nd HD, XP will still function but there will be an error on your GRUB. The GRUB menu list always resides on your Linux HD/partition.

K

---

### Post by linuxden on 2006-01-24
[QUOTE=Kapre]Airintake - Misread your 1st post. Anyways, if you say that you install GRUB in you primary HD (MBR) and you'll remove (which you can test by removing the power to your 2nd HD so it wouldn't be detected) the 2nd HD, XP will still function but there will be an error on your GRUB. The GRUB menu list always resides on your Linux HD/partition.

K[/QUOTE]

as said in my previous post when you get the error just reeinstall GRUB...

---

### Post by AirIntake on 2006-01-24
So does the menu list somehow get pushed to the primary MBR? I just don't see how GRUB would know what my boot options are if the drive with the menu list is gone. 

It's good that it's not too hard to recover though.

Thank you guys so much for your quick helpful replies. This is my first try with any Linux (other than live cd's) and I'm glad I found the distro with a good community.

---

### Post by linuxden on 2006-01-24
[QUOTE=AirIntake]Thank you guys so much for your quick helpful replies. This is my first try with any Linux (other than live cd's) and I'm glad I found the distro with a good community.[/QUOTE]

In my mind its the best community around...!!

Been checking it out for a while...

---

### Post by dueY on 2006-01-24
[QUOTE=AirIntake]So does the menu list somehow get pushed to the primary MBR? I just don't see how GRUB would know what my boot options are if the drive with the menu list is gone. 

It's good that it's not too hard to recover though.

Thank you guys so much for your quick helpful replies. This is my first try with any Linux (other than live cd's) and I'm glad I found the distro with a good community.[/QUOTE]

No the menu.lst does not get pushed to the MBR.  GRUB wouldn't know what your boot options are without menu.lst.  If you wanted to save your Windows after your Linux was gone you would need the Windows CD to boot into recovery console and type "fixmbr" and "fixboot".

---

### Post by AirIntake on 2006-01-24
Thanks again!
Would it be possible to tell GRUB to look for menu.lst on my XP drive somewhere instead of my Ubuntu drive? My XP drive is NTFS....

---

### Post by dueY on 2006-01-24
[QUOTE=AirIntake]Thanks again!
Would it be possible to tell GRUB to look for menu.lst on my XP drive somewhere instead of my Ubuntu drive? My XP drive is NTFS....[/QUOTE]

I believe it is possible to have the Windows default bootloader (NTLDR) load GRUB such that you don't need to touch the MBR at all.

---

### Post by AirIntake on 2006-01-25
Are there instructions on how to do this somewhere?

---

### Post by precek on 2006-01-25
[QUOTE=AirIntake]Are there instructions on how to do this somewhere?[/QUOTE]

Take a look e.g. onto <http://www.vsubhash.com/writeups/multiboot_os.asp>.

---

### Post by jaseywasey on 2006-01-25
Hello
i had real problems getting my PC to dual boot and haven't got it to work satisfactorily. It's probably down to my inexperience rather than anything else. If I messed up then I used a bootable floppy disk to fdisk /mbr to fix the mbr and allow me to get back to Windows and try dual booting another day. There are free versions of fdisk about and it might be on the XP disk (fix mbr??). The point is I could try this a few times, mess up and still get back to XP. I found this URL really useful:
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)
Matthew J. Miller's HOWTO: Dual Boot Linux and Windows on a Laptop

The only difference I had was that I didn't have a fat32 partition on my hard disk. You need to fat32 bit to swap some info from linux to XP. Instead I just got an empty floppy disk, mounted that (something new to me!) and copied the file to a floppy. I have one hard disk with primary-XP, primary-ubuntu, data-NTFS,data-NTFS

My PC now uses windows bootloader to allow me to choose between XP and Ubuntu *and then* GRUB starts up and offers more Ubuntu options. It's not quite right but I can use Ubuntu now. Also the NTFS drives are mounted but obviously not usable (not that I wanted to).  

Not sure if this helps?
Jason

---

