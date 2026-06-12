---
title: "Remove Ubuntu from XP machine"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by larryj on 2005-12-04
I've played with Unbuntu for a couple of months, and would like to remove it from my XP Home computer.  I'll probably install it on a stand-alone box, but for now, want to get this machine back to normal.

I'll need to do the following, and need some help so things don't get screwed up.

Remove Unbuntu, the partition created for it, and the dual-boot menu.

My hard disk was originally partitioned into C: for Windows, and D: for miscellaneous files.  when Unbuntu was installed, both of these logical drives shrunk by about 50 percent.

How doI get it all back..?  Are the tools for doing this on my Unbuntu install CD..?

Thanks..!

---

### Post by ajgreeny on 2005-12-04
Need more info on where your ubuntu partitions are or you could end up deleting your winXP and not linux.  Show a print out of your fstab file and it will be much easier to tell you how to delete the correct partitions and reformat to fat32 or ntfs to use for windows again.

Having sorted out that you'll need to get rid of grub and restore your windows master boot record by using the install disk for xp and going to the repair console and doing a fixmbr (look for details of this in a google search).  If you don't have a full install disk for windows but a system restore disk instead, you could have problems however, so proceed with caution.

---

### Post by daki on 2005-12-04
I know to remove grub from the mbr, if that's where you installed it, you run the command fdisk /mbr, but I can't remember if XP has the fdisk command.  If not, you might be able to find it on the internet.  As far as the partitions go, you could run mmc from start menu under run, then from Add/Remove Snap-in, click add, then double click disk management, then in the new window click finish, then okay, and that will give you access to all the partitions on your hard drive, where you can delete, or reformat, or whatever.  You might want to do some research into these things before you mess with them because I haven't used them in a long time, but I remember that's how I did it before.  Hope this helps.

---

### Post by Terry of Astoria on 2005-12-04
OK here. I found the thread you want probably. 
[http://ubuntuforums.org/showthread.php?t=76095&highlight=uninstall+ubuntu+partition+windows](http://ubuntuforums.org/showthread.php?t=76095&highlight=uninstall+ubuntu+partition+windows)

---

### Post by tonysathre on 2005-12-04
ya xp doesnt have fdsik, boot into recovery mode and use fixmbr to replace your MBR

---

