---
title: "Help ext3 partition not mounting"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by carl123 on 2006-08-05
Man I'm getting really p'd. I've successfully over written the windows MBR with grub. ( which wasn't easy coz there is no way of doing it inside ubuntu that I know of so i had to do it with a grub floppy.) So now I get grub when I boot up the machine. I can boot into windows fine. But i still cant boot into the Ubuntu partition. It tells me it cant mount the partition. I've got a feeling it might be becasue ext3 is not supported by grub.

When i use the root command like this:

root (hd0,1)
It recocnises it as a ext2

Shouldn't this say ext3 or is this normal?

Any ideas on how to get the dam partition to mount?

---

### Post by louis_nichols on 2006-08-05
Grub certainly supports ext3. Now, I don't exactly remember the outputs, but I think it shows ext3 partitions as ext2 anyways. That's because it's pretty much the same thing: ext3 is just a journaled ext2.

Now, the important thing is what exactly happens when you try to boot. What error message do you get? Do you see any of the ubuntu bootsplash screen? Also, can you please paste here the contents of the file /boot/grub/menu.lst  ? This can be done from windows, if you install drivers for ext2/ext3, such as [ext2fsd]("http://ext2fsd.sourceforge.net/") or [ext2ifs]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm")

---

### Post by catlett on 2006-08-05
> **carl123 said:**
> Man I'm getting really p'd. I've successfully over written the windows MBR with grub. ( which wasn't easy coz there is no way of doing it inside ubuntu that I know of so i had to do it with a grub floppy.) So now I get grub when I boot up the machine. I can boot into windows fine. But i still cant boot into the Ubuntu partition. It tells me it cant mount the partition. I've got a feeling it might be becasue ext3 is not supported by grub.

When i use the root command like this:

root (hd0,1)
It recocnises it as a ext2

Shouldn't this say ext3 or is this normal?

Any ideas on how to get the dam partition to mount?

```
sudo grub-install (hd0)
```This command from the ubuntu terminal will install grub to the mbr of the first hard drive. No disrespect but you must not have searched very hard if you came to the conclusion that grub cannot be installed from within a linux system and that grub does not support ext3. [http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall)

If you are having the mount issue, edit the ubuntu entry to rootnoverify. This will keep grub from trying to mount the partition. For example if Ubuntu was on /dev/hda2
```
title     Ubuntu
rootnoverify   (hd0,1)
chainloader  +1
boot
```

---

### Post by carl123 on 2006-08-05
Its all good now.

It decided to work. I think installing the boot loader may have done something. I have grub as my boot loader now and I can boot into windows and ubuntu successfully. Yay.

Ubuntu is annoying in that there is no option to install the bootloader AT ALL if your creating the partitions manually.

Thanks for all your help

---

