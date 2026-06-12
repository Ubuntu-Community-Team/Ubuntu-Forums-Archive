---
title: "Re-installing Grub under Edgy"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by John E on 2007-02-17
When I used to use Dapper, there were several occasions when I needed to re-install Grub. This was the procedure, if I remember it correctly:-

1) Boot up from the live CD
2) Open a terminal window
3) Type: Grub
4) Type: root (hd0,5)  ## 0 & 5 being correct for my installation
5) Type: setup (hd0)
6) Type: quit
7) Type: exit

Now that I've upgraded to Edgy, the above procedure isn't working any more. After stage 4, I get the message "Selected disk does not exist". I've even tried booting up with my old Dapper live CD but that doesn't make any difference. Can anyone explain this - or show me a way to re-install Grub without needing to re-install Ubuntu? Thanks.

---

### Post by petit.padavoine on 2007-02-17
Have any of your disks changed since?
(hd0,5) is the equivalent of /dev/hda6 in the Linux filesystem.
Is that where Grub should go? Does the partition exist?

---

### Post by John E on 2007-02-17
> **petit.padavoine said:**
> Have any of your disks changed since?Yes and No..! Since the upgrade to Edgy, I've copied everything to a larger hard drive. However, the partition layout is absolutely identical to my previous drive (in fact, I've still got the old drive and I can confirm that they're identical). Ultimately, I'll be using the extra space to try out OpenSUSE.

> **petit.padavoine said:**
> (hd0,5) is the equivalent of /mnt/hda6 in the Linux filesystem. Is that where Grub should go?In theory yes - but I did notice that after upgrading to Edgy, a partition that was previously (say) /dev/hda6 has now become dev/evms/hda6. Might this have something to do with my problem?

> **petit.padavoine said:**
> Does the partition exist?Yes. /dev/hda6 (or /dev/evms/hda6, as it's now called) is a valid ext2 partition holding Ubuntu 6.10.

---

### Post by petit.padavoine on 2007-02-17
I'm stumped.
If /dev/evms/hda6 is mounted as the root (/) of your Linux filesystem, (hd0,5) should be the right location to install Grub to... (in theory :D)
Hope you get your answer...

---

### Post by John E on 2007-02-17
Thanks - can you just check my instructions? For example, have I got the syntax right? e.g. is root (hd0,5) correct - or should it be root hd(0,5) ?

Also, I believe there's a way for Grub to produce a list of mounted volumes (something like typing **cat /**) but I can't quite remember the full procedure.

---

### Post by John E on 2007-02-17
Oops - how embarrassing.... at stage 3, I should have typed '**_sudo_ grub**'. :redface:

---

### Post by bulldog on 2007-02-17
If you aren't sure on which partition ubuntu is installed,try the find command.
```
find /boot/grub/stage1
```this will return the right location for you.
This is used after the ```
sudo grub
```command

---

### Post by morkenGNU on 2007-03-17
I like this way to reinstall Grub: 

Just create an additional partition (only 50MB, ext2, reduce e.g. the swap partition by that amount) 
and boot a CD with [Damn Small Linux]("http://distrowatch.com/table.php?distribution=damnsmall").

Installation from DSL LiveCD:
[I]Right click anywhere on the desktop
Apps - Tools - Frugal Install - Frugal Grub Install[/I]

When you install DSL it also installs Grub. Afterwards you edit your **menu.lst** in the **/boot/grub** directory of your 50MB DSL partition. Damn Small (or Dime Size) Linux is also a good additional fallback and rescue system.

---

### Post by morkenGNU on 2007-03-17
Another way is to make a backup of the master boot record (containing Grub) with dd in a root terminal 
and restore it if something happens. 
(quote from [http://wiki.linuxquestions.org/wiki/Dd]("http://wiki.linuxquestions.org/wiki/Dd#Backing_up_your_Master_Boot_Record_.28MBR.29."))

> _Backing up your Master Boot Record (MBR)_
You should do this before you edit your partition table so that you can put it back if you mess things up.

```
 dd if=/dev/hda of=/root/hda.boot.mbr bs=512 count=1
```

If things mess up, you can boot with Knoppix, mount the partition containing /root (hda1 in this example) and put back the MBR with the command:

```
 dd if=/mnt/hda1/root/hda.boot.mbr of=/dev/hda bs=512 count=1
```

Obviously, if you have a GPT system (like the intel mac for instance) this will need some adjustment.

see: [http://forum.onmac.net/showthread.php?t=136](http://forum.onmac.net/showthread.php?t=136)

You can backup only the MBR and exclude the partition table with the command:

```
 dd if=/dev/hda of=/root/hda.mbr.noparttab bs=446 count=1
```

---

