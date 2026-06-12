---
title: "Installing ubuntu on different distro"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by verby on 2006-11-22
i have 3 partitions.
win xp, swap, linux (mepis)
i'd like to install ubuntu on linux partition.
1. do i have to format this partition again?
2. do i need swap partition in ubuntu?
3. how to make that winxp can 'see' (transfer) files in ubuntu and vice verse?
thnx.

---

### Post by taurus on 2006-11-22
1.  Yes, you need to resize your partitions to create an empty space to install Ubuntu on it!

2.  You can use the same swap space for both Mepis & Ubuntu.

3.  Yes, there is a way that you can see Linux partitions in XP and you can access your NTFS (XP) from Ubuntu.

---

### Post by BarfBag on 2006-11-22
> **verby said:**
> i have 3 partitions.
win xp, swap, linux (mepis)
i'd like to install ubuntu on linux partition.
1. do i have to format this partition again?
2. do i need swap partition in ubuntu?
3. how to make that winxp can 'see' (transfer) files in ubuntu and vice verse?
thnx.

Edit - not sure whether you want to keep your Meptis partition or not.  If you want to, don't follow my instructions for deleting the partitions.

I've found that the easiest way to install Ubuntu with a partition layout like the one you have is to delete the swap and Mepis partitions (via Windows) and set Ubuntu to "use the largest contiguous free space."

To delete the 2 partitions from Windows, go to Control Panel > Administrative Tasks > Disk Management.  Explore around in there (I'm not in Windows) until you find a rectangle divided with your partitions.  Right click, and delete both of them.  Please note - your MBR will still have Grub installed to it, so be sure to have an Ubuntu CD on hand before you do this.  You won't be able to boot into Windows until you install Ubuntu (you'll get a boot error).

As far as I know, XP can't read or write to ex3 partitions (which is what Ubuntu uses).  Ubuntu can mount the NTFS partition (XP) and read/copy the files, but can't write to it.  Just follow the steps below if you want to read/copy the files on your NTFS partition.

1.  Fire up a terminal.  Applications > Accessories > Terminal.

2.  Copy and paste (in Linux, this is VERY comfortable; highlight the text and click inside the terminal with your scroll wheel) the first quote and press enter.  Then do the same with the second quote.

> mkdir /media/windows/

> sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

Setting it to automatically mount it every time the system starts up is a little trickier.  If you install Ubuntu and want to do it, just PM me.

---

### Post by ethan961 on 2006-11-22
In order to read and write to the Linux partition (Ext2 or 3), you need the Ext2 Driver for windows - you can get it at [www.fs-driver.org](www.fs-driver.org) in the form of and exe. file which sets everything up, and even though is says Ext2, it can write to Ext3 (which is the same as ext2 except w/ file journaling). AND it is not experimental like NTFS RW in Linux.

---

### Post by tuxcantfly on 2006-11-22
if interested in ntfs write support, see this: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by verby on 2006-11-23
thank you all for input.
barfbag... the instructions for del partitions under winxp and installing ubuntu on "use the largest contiguous free space" worked lika a charm.
thnx

---

