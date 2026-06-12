---
title: "Ubuntu Convert Needs Help Exorcising Windows"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by Ender Black on 2007-04-12
Nicely done Ubuntu folks... I am ready to take the deep plunge and go 100% GNU/Linux - Ubuntu.  Everything on my HP Pavillion dv9000 works as advertised.  My favorite game (Eve Online) runs smooth as butter on wine.  Every application I have added from the repositories has been superbly executed.   And now under Feisty Fawn, networking couldn't be easier.  Hell, my webcam even works.

I have been working with a dual-boot on XP.  I had XP on one HDD and Ubuntu on the other HDD.  What is the preferred method of booting the XP so I have 60GB of extra-storage.  Do I boot into XP and run C:\format C:\ from the command prompt?  Or can I do it from the Ubuntu side?

I searched the forums but everything came up with "How do I uninstall Ubuntu?"  

Oh BTW.. Anyone want to buy my slightly used Zune Media Player... I guess I won't be needing that anymore.  I can't wait for the Cowon iAudio D2 to arrive at my door.

Cheers,
Ender

---

### Post by KIAaze on 2007-04-12
[edit]
[Before proceeding, back up your MBR!]("http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/")
[/edit]

If you don't have anything important on your windows partition anymore, just launch Gparted or QTparted (if you don't have them, install them).
These programs both allow you to delete the windows partition and resize your Linux partition.
Before running them, make sure that the windows partition is unmounted.
(if you run them from a live CD, that problem doesn't exist)

[Gparted=partition editor with GTK interface (Gnome style), QTparted=partition editor with QT interface (KDE style)]

Both programs being almost exactly the same except for visual style, the procedure for both is as follows:
1)Delete the NTFS partition.
2)Resize the Linux partition.

The interface is very intuitive, so I don't think you'll need this additional details, but anyway:
There will be a bar representing the HD with all partitions. Select the NTFS partition, right-click, choose delete.
Select the Linux partition, right-click, choose resize. Resize to the maximum.

And don't worry about testing things because as long as you don't click apply, nothing happens and there is a confirmation box first. ;)
The only thing is that the more instructions you give, the longer it will take to execute them.
So avoid giving unnecessary instructions like creating a partition, then resizing it, then removing it for example.

---

### Post by Ender Black on 2007-04-12
ahh.. didn't know they had to be unmounted... thanks for the super quick reply!

---

### Post by KIAaze on 2007-04-12
Ah, wait!
It might be a good idea to back up the MBR first.

I forgot to talk about that.
However, in any case, even if you already have deleted the windows partition, it shouldn't be a problem to get things working again if there are problems...

---

### Post by tux_rox on 2007-04-12
How do you unmount the Windows partition?

---

### Post by KIAaze on 2007-04-12
Supposing it's mounted on /mnt/win, just do:
```
umount /mnt/win
```
And if necessary, use sudo:
```
sudo umount /mnt/win
```

---

### Post by Dtree on 2007-04-12
Hi,
After days of reading the doom n gloom posts about everything going wrong, it does my heart good to hear someone  post an "iT WORKS" thread. Ill keep trying )

---

### Post by lamalex on 2007-04-12
it shouldn't really be that hard as long as you know what you're doing. Just install gparted and make sure you have a grub livecd handy (just in case) and instructions on how to use it. that's all you need.

---

### Post by KIAaze on 2007-04-13
Just in case:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")
[http://www.linuxforums.org/forum/suse-linux-help/66252-removing-windows-completely.html]("http://www.linuxforums.org/forum/suse-linux-help/66252-removing-windows-completely.html")

I hope everything works. I'm sorry for having forgotten to mention that.
I already removed Debian once from my PC by simply deleting its partition, but I never removed the Windows partition, which is the first partition.
I don't know exactly how the MBR and Grub work, but since re-installing windows causes problems,  deleting its partition might too.

In any case, the data should be safe and the Grub re-installation should work.

However, if after the deletion of the windows partition, you can reboot into GNU/Linux without problems, all you would have to do would be to delete the entry about windows in the /boot/grub/menu.lst file.

edit:
[How to back up the MBR (Master Boot Record):]("http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/")
> Create a backup of your MBR by doing a:

$dd if=/dev/hdx of=MBR-backup bs=512 count=1

That should read &#8220;create a disk dump of the input file, which is /dev/hdx (change to hda, or hdb or sda, depending on where the MBR is on your computer), and save it in the output-file MBR-backup in the directory from where the command is issued. Backup the first sector only, while you are at it&#8221;.

Now that is the backup of your MBR. Restore it later using:

$dd if=MBR-backup of=/dev/hdx bs=512 count=1



---

