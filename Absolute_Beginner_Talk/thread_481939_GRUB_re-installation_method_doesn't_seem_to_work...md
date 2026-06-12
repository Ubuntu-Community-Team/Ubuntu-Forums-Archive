---
title: "GRUB re-installation method doesn't seem to work..."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Miki01 on 2007-06-23
Hey everyone, its been a while since I've posted on the forums.

I've recently upgraded from 6.06 to 7.04.

The installation went fine until the Ubuntu installer messed with my Windows partition and somehow deleted the .dll file that Windows uses to communicate with my computer's hardware (that's not good ;)). At the time, GRUB was working fine, can boot into Fiesty with no problems, but WinXP just had the no-boot issue. So taking what I've learnt from cooperative-ed at a computer store, I stick my WinXP disc in the drive and repair it with chkdsk. All is well with XP.

But I noticed something when booting into Windows XP... GRUB isn't showing up! I noticed that when I went looking for Ubuntu on the boot menu!

So I boot up Fiesty's live CD and go on google (since I'd have to reboot if I just googled while in XP).

I've found the "sudo -i, find /boot/grub/stage1, root (hd0,x), setup (hd0)" method.

I've read on Ubuntu's resident wiki that it's better to run "setup (hd0,x)" instead of "setup (hd0)", since it installs GRUB in Ubuntu's partition, rather than the master boot record.

I tried it both ways and NONE have worked...

Here's what I got for each:

"setup (hd0,x)"

> ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0,5)
setup (hd0,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 12: Invalid device requested
grub> quit
quit

and running "setup (hd0)"

> ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 12: Invalid device requested
grub> quit
quit

What seems to be the problem? My Ubuntu partition is taking up quite a bit of space on this small 80GB HDD I'm using, so I'd like to be able to make use of it.

Would anyone know how to fix this?

Thanks in advance for your replies, it is greatly appreciated!

---

### Post by confused57 on 2007-06-23
You might want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
see if it will boot Feisty, if it does, then you might be able to troubleshoot the problem.

---

### Post by molly_001 on 2007-06-23
Most of the time hal.dll is actually PRESENT and IN GOOD WORKING ORDER even though you are told by the NTFS bootloader that it is corrupt or missing.

I just spent ... oh, 12 hours ... with the same exact problem after installing 7.04 onto an OEM machine.  If you need help getting back to a correct NTFS boot, let me know.

In your situation (and indeed anytime I find boot issues) I just install "GAG Boot Manager" onto the mbr ... it's a bootable .iso you can burn.  Again, if you need help with that, let me know.

My day yesterday went from ... hal.dll error ... using Windows Recovery to fix that ... fixing the mbr and boot.ini ... doing a Repair Install of Win XP sp2 ... etc ... but I was never able to boot into ext3.  But good old GAG Boot Manager saved the day (and all night) for me by giving me constant access to the NTFS boot.

---

### Post by Miki01 on 2007-06-25
Thanks guys, I'm going to try confused57's method first. I'll get back to this thread if I have any problems.

molly_001, GAG Boot Manager actually looks pretty nice. I like the graphic interface, its less 'technotic' like the standard chart-style GRUB.

---

