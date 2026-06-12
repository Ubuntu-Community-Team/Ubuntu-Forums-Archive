---
title: "GRUB won't let me switch back to Windows"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by EarnestLearner on 2007-02-10
Hi. I'm trying to figure out how to switch back to Windows XP. I'm not leaving the community. Ubuntu is great. I just would like to be able to switch as my needs change.

I have Ubuntu Edgy Eft and Windows XP Home CDs with me. My system is set to boot from CD. I have tried and failed to load Windows after running the recovery console. I kept getting GRUB error 17, I have followed the instructions on the Microsoft support page to use fdisk to delete all partitions and it seemed like it worked. Everything goes according to plan except that GRUB hangs around to give me the error 17.

I am using the Live CD right now. Any ideas?

---

### Post by BarfBag on 2007-02-10
Do a fresh install instead of recovery.  That will clear the MBR, remove grub, and give you a fresh system.  This will delete all of your data, though.  You can back it up through the live CD.

---

### Post by EarnestLearner on 2007-02-10
I think there is some confusion. I have no data to backup. I don't want to dual boot or partition anything. I have a Windows recovery CD (bootable CD used to restore the OS).

I'm running the Live CD. I would like to install Windows XP and have it load without the aforementioned GRUB error. If there's a way to clear the MBR using the Live CD, I would appreciate the instructions to do that.

Thank you.

---

### Post by mikeescott on 2007-02-10
I have done that with Max-Blast 10.48 from Maxtor. It is a hard drive install and utility disk. I used it to repair the MBR after a bad install of Linux a few times. It removes Grub and tells it to start the main os.

---

### Post by EarnestLearner on 2007-02-10
Will it work on a Western Digital hard drive?

Here's my sudo fdisk -lu:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   156296384    78148161    7  HPFS/NTFS

```

---

### Post by EarnestLearner on 2007-02-10
Does anyone know how to make Windows XP boot without getting grub error 17?

---

### Post by jordanmthomas on 2007-02-10
go into recovery mode from the XP CD.  (it's a DOS prompt)
type 
```
FIXMBR
```
It will ask if you are sure.  If you are sure, let it do its thing. then type
```
exit
```
and you will reboot into Windows

---

### Post by EarnestLearner on 2007-02-10
Sorry. I can't get back into the DOS prompt. It appears that my only options are:

1. hitting delete to get into CMOS or BIOS
2. hitting r for recovery options (which takes me to a system recovery console [not DOS])
3. hitting nothing and getting grub error 17.

---

### Post by jordanmthomas on 2007-02-10
Hit R
the recovery console is what you're looking for.
Or is the recovery console a 'let windows repair this for you' type of deal?

On my XP disc, it will let me log into an installed Windows if I go to the recovery console, which is very DOS-ish.  Maybe you need to get a hold of a full XP disc.  Maybe your disc is an OEM disc with that feature removed or something.

---

### Post by EarnestLearner on 2007-02-10
Mine is OEM that does the following:

Makes my drive NTSF, copies files to the drive, and starts Windows XP (SP1) with factory shipped drivers and software.

I get to the part where it asks me to take out the CD and restart. Then I get the grub error during boot.

---

### Post by jordanmthomas on 2007-02-10
hmmm...any way you could borrow a full install disc from somebody so you'd have the recovery console?

I believe you could fix the MBR if you could get a Windows 98 floppy as well.
Gotta love OEM installs, no?

---

### Post by EarnestLearner on 2007-02-10
I'll try my Windows 2000 Pro CD and let you know how that turns out :P

Thanks for your suggestions.

---

### Post by EarnestLearner on 2007-02-10
Seems pretty hopeless at this point. Win2K was able to format the drive into NTSF *again* and then finished copying its files. It then rebooted my computer and I was presented with the grub error 17.

So I'm back to square one.. using the Live CD to ask for help here.

---

### Post by mikeescott on 2007-02-11
Yes, it will work on a Western Digital drive. I used it on my 320gb SATAII WD drive trice when getting the same "error 17" from grub.
Maxtor is owned by Seagate now. Here is a link to the software:

[http://www.seagate.com/staticfiles/maxtor/en_us/downloads/maxblast4.exe]("http://www.seagate.com/staticfiles/maxtor/en_us/downloads/maxblast4.exe")











> **EarnestLearner said:**
> Sorry. I can't get back into the DOS prompt. It appears that my only options are:

1. hitting delete to get into CMOS or BIOS
2. hitting r for recovery options (which takes me to a system recovery console [not DOS])
3. hitting nothing and getting grub error 17.

---

### Post by moshuptrail on 2007-02-11
do you have ANY bootable disks around the house? 

You just need to get to a DOS prompt somehow. The comands fixmbr, or fdisk /mbr
will both do the trick.

I'm not sure what a grub error 17 is, but I'd guess it's that grub can't find what it's looking for.

So an alternate approach might be to bring up the Live CD and use Gparted to shrink your windows partition and install Linux in the area created by shrinking.  I know you didn't want to do that but it WILL get you past the grub error.  Once Linux is installed grub will create a dual-boot menu.

You'll like the speed of Linux installed a lot better anyway.

---

### Post by drb08jd on 2007-02-16
I don't know if you're having the same problem still, but here's what I did to fix it on my computer which only has OEM Windows.

1.) Use System Rescue Cd ([http://www.sysresccd.org/](http://www.sysresccd.org/)) to use GParted to format the whole drive to NTFS.

2.) Use fdbasews ([http://www.freedos.org/freedos/files/](http://www.freedos.org/freedos/files/)) to make a Live CD DOS prompt, hit option 1, option 3, then @ the "A:\", type "fdisk /mbr".

3.) Do the OEM Windows install.

hth

> **EarnestLearner said:**
> Hi. I'm trying to figure out how to switch back to Windows XP. I'm not leaving the community. Ubuntu is great. I just would like to be able to switch as my needs change.

I have Ubuntu Edgy Eft and Windows XP Home CDs with me. My system is set to boot from CD. I have tried and failed to load Windows after running the recovery console. I kept getting GRUB error 17, I have followed the instructions on the Microsoft support page to use fdisk to delete all partitions and it seemed like it worked. Everything goes according to plan except that GRUB hangs around to give me the error 17.

I am using the Live CD right now. Any ideas?

---

### Post by rccharles on 2007-02-16
> **EarnestLearner said:**
> Mine is OEM that does the following:

Makes my drive NTSF, copies files to the drive, and starts Windows XP (SP1) with factory shipped drivers and software.

I get to the part where it asks me to take out the CD and restart. Then I get the grub error during boot.

It seem that your windows restore isn't re-writing the Master Boot Record MBR. You should be able to use superGrub.  It doesn't use the MBR to boot Windows or any other partition.  You will still have to figure out a way of restoring the MBR to windows format.  I'd look around the internet for a Windows restore MBR program.

An option would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org...on=screenshots](http://supergrub.forjamari.linex.org...on=screenshots)

You cursor down to the line you want.

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.

I wrote superGrub out to cd and it worked for me. You can boot your partition even without grub on the partition.

This wouldn't be a permanent solution, but it would get you started.


Robert

---

### Post by sardion on 2007-02-16
Boot from the ubuntu livecd, start the install process and get to the part where it asks about the hard drive.  Choose erase entire disk.  Let it do the erase but before it gets into installing, just kill it (power down even).

Then boot of the windows disc.  It will work fine.

You will of course be erasing your entire hard drive by doing this.

---

### Post by Resurrection on 2007-02-16
I recommend this:

[The Ultimate Boot CD]("http://www.ultimatebootcd.com/")

UBCD has tools on it to including FIXMBR which will wipe out grub and reinstall the windows boot record.  It also has a tool for wiping a MBR on a hard drive clean.  If all else fails that should allow you to do a clean Windows install.

And its a handy tool to have around in your software library.

---

### Post by donsalo on 2007-12-26
I am not sure how nervous I should be about using the ubcd tools to write a new mbr.  Could one of you really experienced people help me with a few of the choices on the ubcd, so I don't destroy my son's computer... I've been researching the grub error 17 issues for many hours... It seems that I need to rebuild the MBR on this laptop.  I have the ubcd, booted with it and looked around a little, but I have not been able to find any clear steps on what I should do.  Thanks for any help you might have.  My sons wants to play his new game, he is getting sad... I had to get rid of ubuntu on his machine to make room for the new game.  It worked fine til we shut it down to go to bed last night...

---

