---
title: "Grub Errors 13, 17. Dual Boot 2 HDD"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by Innomado on 2007-04-17
4.17.2007  22:59
Thanks to Confused57, dstew, and rinzwind for the help. Grub and everything everything else seems to be working fine now.

---------------------------------

Over the past two days I have successfully installed 6.10 on my secondary hard drive without harming the install of Windows XP on my primary drive or harming the data in the extended partition on the secondary drive. I ran into my share of problems, but I did it.

With the BIOS set to boot from drive 0 windows boots normally from it's boot loader. Set to drive 1 the BIOS boots Grub which gives me a list of operating systems. From that list all Ubuntu options return and error 17 and the Windows option returns an error 13. 
Using the Super Grub Disk I can force Ubuntu to boot and am composing this post from said OS, (also why I referred to this install as successful) but I have had no apparent benefit trying to repair grub with the disk.

I would very much like to be able to boot either OS from grub without having to resort to the Super Grub Disk or to changing my BIOS setting every time I want to boot one system or the other. I've been searching the forum and looking at different guides since Saturday evening but have obviously met with no luck in finding a solution. I am grateful for any help people can give.

Also, from some of the threads I've read this data should be helpful. If there is any other information I can share just let me know.  

fdisk -l results
hda contains 1 partition with Windows XP installed
hdb contains my Ubuntu install(hdb1) with it's swap(hdb3) and an extended partition(hdb2) containing hdb5 - hdb9.
> 
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2741    22017051   83  Linux
/dev/hdb2            5239       25472   162529605    f  W95 Ext'd (LBA)
/dev/hdb3            2742        2872     1052257+  82  Linux swap / Solaris
/dev/hdb5            5239        8501    26210016    7  HPFS/NTFS
/dev/hdb6            8502       11765    26218048+   7  HPFS/NTFS
/dev/hdb7           11766       15681    31455238+   7  HPFS/NTFS
/dev/hdb8           15682       24819    73400953+   7  HPFS/NTFS
/dev/hdb9           24820       25472     5245191    7  HPFS/NTFS
OS entries in menu.lst
> 
title        Ubuntu, kernel 2.6.17-11-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.17-11-generic
boot

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
chainloader    +1


---

### Post by Rinzwind on 2007-04-17
Error 17: should be because the disc can not be mounted.
Did you do something inside your PC? Rearrange discs or something like that?
Did you change the boot-order in your BIOS? 

It looks to me your 
/boot
is currently not at the location Grub thinks it should be found. 

It should be possible from within grub to issue some commands.

If you type this inside grub:

root (hd1,1)
setup (hd0)

does that help?

---

### Post by Innomado on 2007-04-17
From what I understand menu.lst and fdisk -l say that grub is being pointed to the correct drive and partition. (hdb1 translates to hd1,0).

If I understand this ([**http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands**)]("http://www.gnu.org/software/grub/manual/html_node/Command_002dline-and-menu-entry-commands.html#Command_002dline-and-menu-entry-commands") right then root (hd1,1) will designate my extended partition (hdb2) as grubs root device. 
How will this help, that's just an extended partition for data storage. Ubuntu is on hdb1 (hd1,0) so what will that do?  And I don't want grub on my windows drive so why would I use setup to install it onto drive (hd0)? 
By setting the BIOS to boot from hd1 (my secondary drive) I can already get grub to come up. Putting grub on hd0 will just mean that I can't reset my BIOS to boot from hd0 to boot up Windows (a safety net I want to keep).

Also if using root and setup like you say doesn't work how do I undo what they change so that I can keep troubleshooting from a (somewhat) stable state?

(Please understand I'm grateful for the help and I'm not trying to be critical here but I'm as interested in getting a full understanding of how the solution works as I am in finding a solution.)

---

### Post by Innomado on 2007-04-17
Just a gentle bump. Thanks ahead of time for any help.

---

### Post by confused57 on 2007-04-17
Boot to your Ubuntu drive hdb, in the grub menu, highlight your Ubuntu entry, press "e", then change root from (hd1,0) to (hd0,0), then press "b" to boot...this is temporary, but can be made permanent in your /boot/grub/menu.lst.

To boot Windows from grub your entry should probably be something like this:

```
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by dstew on 2007-04-17
I agree with confused57. When you changed boot order, the numbering of the disks also changed for grub. When you boot /dev/hdb first, it becomes (hd0). When you boot /dev/hda first, /dev/hdb is (hd1). When you installed linux, and grub, /dev/hdb was (hd1), so that is what ended up in the menu.lst file. If you are going to boot from /dev/hdb from now on, you will need to change the menu entries as confused57 says. However, if you change your boot order again, grub will fail again.

Best to pick a boot order, install, and don't change it. People do what you did out of a concern that grub will do something bad to /dev/hda, where windows is. They do not want to let grub go into the MBR of the first disk. This is a mistake. Sometimes people will unplug a disk, install, then plug the disk back in. Bad idea. Trust grub with your first disk MBR. If you don't like it, you can always put the Windows boot loader back with fixmbr from the recovery console of the Windows recovery CD.

---

### Post by Innomado on 2007-04-17
That worked. Windows will boot fine with those modifications to GRUB. I assume that editing the windows entry in menus.lst will make that permanent.

If I am interpereting correctly then your script redesignates hd0 and hd1 so that hd0 is designated hd1 and hd1 becomes hd0 (is there more to it than this?). GRUB then boots from what it views as hd1 (which was hd0) and windows works. 
What I am unclear on is why this works.
Any thoughts on the error 17 returned when booting ubuntu?

By the way, thanks for those links in your sig. They came in handy when I was working on the problems I had Saturday I just can't seem to pick out what parts of them will help out with my current prediciment.

---

### Post by Innomado on 2007-04-17
So grub decides on hd# designations every time it runs.
When I have BIOS boot from hd1 (my secondary hard drive) Grub views hd1 as hd0 and hd0 (primary drive) as hd1.

Modifying confused57's script and entering it into the linux entries of menu.lst should fix the problem them.

Would these be the correct changes?
> 
title Ubuntu, kernel 2.6.17-11-generic
**root (hd0,0)**
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
[B]map (hd1) (hd0)
map (hd0) (hd1)[/B]
boot

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
**root (hd0,0)**
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.17-11-generic
[B]map (hd1) (hd0)
map (hd0) (hd1)[/B]
boot

---

### Post by dstew on 2007-04-17
I think you will only need to change the root statements. The map statements are only needed for booting windows.

---

### Post by confused57 on 2007-04-17
> **Innomado said:**
> That worked. Windows will boot fine with those modifications to GRUB. I assume that editing the windows entry in menus.lst will make that permanent.

If I am interpereting correctly then your script redesignates hd0 and hd1 so that hd0 is designated hd1 and hd1 becomes hd0 (is there more to it than this?). GRUB then boots from what it views as hd1 (which was hd0) and windows works. 
What I am unclear on is why this works.
Any thoughts on the error 17 returned when booting ubuntu?

By the way, thanks for those links in your sig. They came in handy when I was working on the problems I had Saturday I just can't seem to pick out what parts of them will help out with my current prediciment.

dstew has explained quite well how grub identifies hard drives and there's not much I can add.

When you installed Ubuntu, your hard drive bios boot order was Window's drive, then Ubuntu drive; therefore your Window's drive was (hd0) and Ubuntu (hd1).  When you boot first to your Ubuntu drive, grub then recognizes your Ubuntu drive as (hd0), therefore you need to make the necessary modifications in your menu.lst & I'd recommend leaving your system set up to boot first to your Ubuntu drive.  Windows insists on being the first OS in order to boot and the mapping commands "fools" it into thinking it is the first OS...the mapping commands are not needed with Ubuntu, it doesn't care where it's located in relation to other OS.

You'll also need to change the groot entry in your menu.lst from (hd1,0) to (hd0,0):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

