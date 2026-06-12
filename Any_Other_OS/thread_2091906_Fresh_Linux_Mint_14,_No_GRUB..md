---
title: "Fresh Linux Mint 14, No GRUB."
date: 2012-12-06
forum: Any Other OS
---

### Post by jamedfor on 2012-12-06
Hi All, I hope this is not a redundant post or common issue, but I couldn't solve my issue myself or by searching other threads and google.

Yesterday I installed Windows 8 on a small partition, followed by Linux Mint 14 MATE on another small partition with plans to make the rest of the space shared. However, I never got a GRUB menu at startup! I tried following the instructions on the GRUB info page from google by doing something like:

     # grub-install /dev/sda

but I don't really know my way around GRUB, and when I rebooted I just got the grub prompt that looked like 

     grub>

and I couldn't get out. I used the install USB I used to run Mint from USB, from which I did something like:

     install -d /mnt/mount  !!to create a mount point
     mount /dev/sda1 /mnt/mount     !!sda1 is the Mint partition
     grub-install --root-directory=/mnt/mount sda

This got me back where I started, and I don't want to risk losing computer access again, so I came for help! any advice would be appreciated.

Thanks!!!
-John

---

### Post by dannyboy79 on 2012-12-06
might i suggest downloading and using a program called "boot repair". i haven't used it but I see many who have success with it in fixing grub issues and such. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jamedfor on 2012-12-06
Thanks for the tip dannyboy!

That got me a GRUB menu, though unfortunately it only includes Mint, there is no Windows 8. Is there another quick fix to this too?


EDIT: Nevermind, this looks pretty easy. I'll give it a go!

-John

---

### Post by ubume2 on 2012-12-06
From your usb disk after it boots to desktop

Go to a terminal

do sudo fdisk -l

so you can determine the linux partition you want to create grub in.

Then from the command line

```
$ sudo mount /dev/sda5 /mnt  
```

Mine is sda5. yours is likely different

```
 sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you are in the partition you need to create a grub in.

```

#grub-install /dev/sda               **mine is sda. yours may be different
#update-grub 
```

After you update grub you should get a list.  It should include Windows

You are not done.

```

#exit
$sudo umount /mnt/sys
$sudo umount /mnt/proc
$sudo umount /mnt/dev
$sudo umount /mnt
```

Then reboot, remove the USB device. You should see a grub menu with Linux Mint & Windows.

---

### Post by jamedfor on 2012-12-06
ubume, I tried your method and I just installed the grub on /dev/sda. after updating the grub the list returned looks like:

Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic

the initrd item doesn't look like windows... any suggestions? I haven't done the unmounting part yet.

---

### Post by oldfred on 2012-12-06
Moved to Other OS.

Post link to BootInfo report that Boot-Repair creates.

ubume2's grub reinstall is the full chroot method which can be used when the two line mount & install method does not work. 

But usually Boot-Repair just fixes things.

---

### Post by jamedfor on 2012-12-06
oldfred, thanks for reminding me to post the log from boot-repair:

[http://paste2.org/p/2569606](http://paste2.org/p/2569606)

there's an error about a cat something that may be the problem, I've seen errors about cat before.

Also, the ~22000 lines of invalid argument errors may indicate somethings wrong :P

-John

---

### Post by Chdslv on 2012-12-06
Try with Quantal and check whether Grub would see Win 8.

With Mint 14; go to /etc/apt/sources.list and *block* the Nadia repo, by adding # in front of it and,
add
> deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) quantal main  deb-src [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) quantal main
and then update.

Install grub-pc or reinstall it
and check whether your win8 is seen.

if not,
> sudo apt-get install boot-repair
and run boot-repair as root. While working, it'd see your win8.

---

### Post by oldfred on 2012-12-06
I do not know what the broken pipe error is that generated all the error lines.

But you have Windows in sda5 which cannot be.

Windows only boots from a primary partition with the boot flag or sda1 thru sda4. So if you moved it from sda1 its boot.ini is wrong. Or if it was a second install some or most of its boot files were in the first install. Also PBR will be wrong.

Since it did not post boot.ini which script normally does it may be other issues in the XP NTFS partition?

Only with XP there are work arounds to make it work in a logical partition, but it would be better to move it back to a primary. Based on your partition table it looks like you just just use fixparts to convert to primary. Probably still would need repairs to boot.ini and PBR. NTFS partition have to have the same start and size info in the PBR - partition boot sector as the partition table. Normally chkdsk from XP will fix that, but you need boot flag and XP in a primary partition for chkdsk to work well.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

    
Then use gparted to move boot flag to new XP primary partition and use a XP disk to run chkdsk. And edit boot.ini with correct partition.

---

### Post by ubume2 on 2012-12-06
> **jamedfor said:**
> ubume, I tried your method and I just installed the grub on /dev/sda. after updating the grub the list returned looks like:

Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic

the initrd item doesn't look like windows... any suggestions? I haven't done the unmounting part yet.

Well, could be something about Windows 8.

From command line sudo chmod +x /etc/grub.d/30_os-prober.

Then sudo update-grub.


If you don't see Windows generated after you press the update-grub command, there is a problem.  I haven't had any problem with Win 7 grub item being generated. I've used the method described in post 4 with Linux Mint, and have had no problems.

---

### Post by jamedfor on 2012-12-06
Hi oldfred, thanks for the input! 

I installed Windows 8 to a new partition from an old XP one into some newly created space, I assume that's why it is at sda5. Based on your post:

1. I assume sda2 would be better?
2. I just installed these OSs, would it be easier to just erase everything, install windows 8 to sda1, then follow with sda2 for Mint and sda3 for swap?
3. when I look at gparted, I see sda1 first, followed by sda5 with no space in between. Is this setup a candidate for your method?

Let me know if theres any more data you need!

-John

---

### Post by oldfred on 2012-12-06
Only because you have not used all the primary partitions could you use fixparts to convert.
It probably would be better to reinstall. Then you can totally reorganize partitions.

But especially with Windows 8 I would also want another NTFS shared data partition. Windows 8 is always hibernated, just in different levels. Turning off hibernation helps a little, but you still should not write into the Windows system partition. Best to set as read only.

Since linux is ok with logical partitions I would try to make a lot of drive extended for logical partitions.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Chdslv on 2012-12-06
Windows always installes itself to the first partition, actually using one small and one big partition, so it should be in sda1 & sda2. If not, install it again. Then, install the Ubuntu distro with Quantal base, which is geared to work with Win 8's restrictions. Mint has the Quantal base, so it should "see" the Win8 partition.

The new grub-pc of Quantal cannot be set up the old way, by using sudo grub-setup /dev/sda, hence the need to use of YannUbuntu's Boot-repair.

Anyway, once Win8 is installed in the beginning of your hard disk, and a good Qunatal based distro is installed in the next nearest partition--not in a primary one--you should be able to "see" Win8 in the grub.

If you still don't see that, re-install grub-pc, and that grub-pc should br from Quantal repos. You can watch the work in the Terminal and while finishing, grub-pc would find Win8. If not, you should use Boot-repair and let it correct the problem.

And, if the problem persists, you have to install Quantal in another partition, so that Quantal would take up the grub. But, you won't be able to uninstall Quantal, if you want to dual boot. 

As, Mint says that it had been built from the mini.iso, something might've gone missing, which Quantal has.

You should read Jesse's article about his problems of getting away from the Win8's restrictions in the last week's Distrowatch. [http://distrowatch.com/weekly.php?issue=20121126](http://distrowatch.com/weekly.php?issue=20121126)
Jesse gives a running commentary how he managed to get rid of the Secure Boot problem. You may learn something from there.

The moral out of this; don't get caught to Microsoft's machinations, and if you really want to use MS Windows, use Win7. 

Finally, I looked at Win8 and my personal feeling is that Win8 would go the same way as Vista, but that's another story.:P

Good day!

Ch

---

### Post by YannBuntu on 2012-12-07
Hello

```
cat: write error: Broken pipe
FIBMAP: Invalid argument
FIBMAP: Invalid argument
...
```

is not important, it 's a minor bug of BootInfoScript: [http://sourceforge.net/apps/trac/bootinfoscript/ticket/2](http://sourceforge.net/apps/trac/bootinfoscript/ticket/2)
and it is not the cause of your problem.


Your problem is that your Windows8 has missing boot files:

```
Boot files:        /bootmgr /Windows/System32/winload.exe
(...)
/mnt/boot-sav/sda5/ may need repair.
```

**Solution:**
1) Use a Windows disc this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) , until you get direct access to Windows
2) then use Boot-Repair to recover your GRUB menu

---

### Post by jamedfor on 2012-12-08
Thank you all so much for your quick responses and time spent helping me! In the end, I gave up trying to fix my setup. Because I had just installed these systems, I used a USB drive to erase all partitions and installed windows 8 on sda1 and sda2 (it needs 2 partitions, a source of my initial problems.) and followed up with linux mint installed on a new sda4 partition. This way the grub loader installed properly and my problems are solved!

Thanks again,
John

---

