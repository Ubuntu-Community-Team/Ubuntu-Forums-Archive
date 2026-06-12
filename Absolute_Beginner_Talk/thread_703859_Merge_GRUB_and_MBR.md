---
title: "Merge GRUB and MBR"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Misbah on 2008-02-21
I  posted in the installation forum but it didn't get much help, aside from my own help. Quick summary:

Installed XP on 1st HD with second HD SATA channel unplugged.
Installed Ubuntu on 2nd HD with first HD SATA (XP install) channel unplugged.

Did this for privacy reasons, didn't want people to see the second ubuntu drive as it had all my sensitive and private info. Neither drive knew the other existed this way, and I just enabled/disabled the respective SATA channels in the BIOS when I needed to switch OS'es. Need for privacy is gone so I wanted to merge the drives so they can see each other because now it's annoying not being able to soft dual boot from a boot loader and access files from the other drive when I'm on one of them.

Activated both channels and booted up with XP as boot drive to see what would happen. XP loaded, installed second HD, volume shown, but not readable due to EXT3 file system. Rebooted with ubuntu as boot drive, saw local disk, mounted, NTFS file system fully readable.

Fixed not being able to read EXT3 while in windows by installed FS-driver. Works perfectly.

Then instead of having to enable/disable SATA channels to switch OS's, I have to change the boot disk priority, same problem kind of.

This is where I'm at right now. 2 remaining problems.

1) I still don't want to have to go into the BIOS and change the boot order whenever I want to switch. How can I get reference GRUB in MBR (I feel XP should be the boot drive, and MBR the dominant boot loader, with GRUB inside it referencing the second physical hard drive as Ubuntu OS. I don't know how to do this, I've seen lots of threads on it, but mostly for single partitioned drives or shared partitions, not two separate drives.

2) FSdriver auto mounts my / and /home partitions (dont mount swap). Ubuntu doesnt auto mount my local XP disk. have to manually mount after start up and dismount before shutdown. Would like to automate this.

If I can get those two remaining problems out of the way, I think I will have merged the two successful. Just want to be able to use a boot loader and have access to Ubuntu from XP and vice versa smoothly. Thanks for all the help guys.

---

### Post by Rotaj on 2008-02-21
Hopefully this is the answer to what you want to do.

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by dcstar on 2008-02-21
> **Misbah said:**
> ..........
1) I still don't want to have to go into the BIOS and change the boot order whenever I want to switch. How can I get reference GRUB in MBR (I feel XP should be the boot drive, and MBR the dominant boot loader, with GRUB inside it referencing the second physical hard drive as Ubuntu OS. I don't know how to do this, I've seen lots of threads on it, but mostly for single partitioned drives or shared partitions, not two separate drives.

2) FSdriver auto mounts my / and /home partitions (dont mount swap). Ubuntu doesnt auto mount my local XP disk. have to manually mount after start up and dismount before shutdown. Would like to automate this.
..........

1/ Do a forum search for "Restore Grub", you will find instructions on how to set it up as the boot loader, and then add this to the end of your /boot/grub/menu.lst file (it may need "tweaking" for your particular setup):

```
title		Microsoft Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

2/ Install the **pysdm** package and use it to set up the mounting.

---

