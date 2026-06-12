---
title: "[SOLVED] Deleted some files; No space"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-03-13
I have 100GB hard drive. Divided into 3. The first 2 are NTFS formatted with Windows XP in it. And of course the last one is ext3 formatted.

Now, I experienced a weird thing. In Hard Drive 2, NTFS, I deleted some more than 500MB of file, via Ubuntu, now I have confirmed that the file is already deleted. But the problem is, I did not recover any space. I need those space or more space to backup my files to DVD because I can't download new movies, lack of disk space.

I really need some storage right now, because the partition where Ubuntu is installed, only has 300MB of free space.

What happened to the deleted files of Hard Drive 2? I did not gain free spaces, so how can I recover the files or where did it go? The trash is empty.

---

### Post by Rocket2DMn on 2008-03-13
The deleted files are in a .Trash-[yourusername] directory in the root of the mount point of that drive.  In nautilus, navigate to /media/*mountpoint* and hit CTRL+H to see hidden files, you will see the folder there.  Open it and delete the contents, then they will be gone for good.
Alternatively you can navigate from terminal:
```
cd /media/*mountpoint*/.Trash-[yourusername]
rm *
```
As always, be careful with the rm command.

---

### Post by scragar on 2008-03-13
your partitions all have a set size, freeing space on one partition will not free space on another.

there are a few commands you can run to try free up some memory, although I don't think it will be too much:
```
sudo apt-get autoremove
sudo apt-get clean
echo "" > ~/.bash_history
```and if your not running as root you can always try:
```
rm -v ~/.*~
```this will remove the backups made automaticly made by programs like gedit.

---

### Post by FuturePilot on 2008-03-13
> **Rocket2DMn said:**
> The deleted files are in a .Trash-[yourusername] directory in the root of the mount point of that drive.  In nautilus, navigate to /media/*mountpoint* and hit CTRL+H to see hidden files, you will see the folder there.  Open it and delete the contents, then they will be gone for good.
Alternatively you can navigate from terminal:
```
cd /media/*mountpoint*/.Trash-[yourusername]
rm *
```
As always, be careful with the rm command.
Yes, try that. With NTFS partitions it seems that anything in the Trash from that partition will not show up in your Trash. You have to try and manually remove them from the .Trash folder on that partition.

---

### Post by karlo on 2008-03-13
> **FuturePilot said:**
> Yes, try that. With NTFS partitions it seems that anything in the Trash from that partition will not show up in your Trash. You have to try and manually remove them from the .Trash folder on that partition.

Thank god! I saw it! Is this a bug? Anyway how can I restore some of the files? I can find any restore buttons.

---

### Post by Rocket2DMn on 2008-03-13
There is no built in method of returning files in the .Trash folders to their original locations.  When you deleted them initially, it just moved them there like a drag and drop procedure, it doesn't remember where it came from.  You will have to restore each file to its respective location manually.

---

### Post by karlo on 2008-03-13
Upon finding the directory where the files are and deleting them, here's the results:

[[IMG]http://www.imageox.com/graphic/thumbs/199590-Screenshot-th.png[/IMG]](http://www.imageox.com/share/199590-Screenshot.png)

Then I can't remove the Windows directory...

[[IMG]http://www.imageox.com/graphic/thumbs/199591-Screenshot-th.png[/IMG]](http://www.imageox.com/share/199591-Screenshot.png)

---

### Post by Rocket2DMn on 2008-03-13
Are you just deleting a WINDOWS directory as in C:\WINDOWS ?
I hope you know what you're doing, but to answer your question, you can try from the terminal:
```
cd /media/sda3/.Trash-karlo
rm -R WINDOWS
```
As always, be very careful with the rm command - it cannot be done!  Use with caution.  Post any output here.

---

### Post by alphaniner on 2008-03-14
Try the command line method:

make your way to the trash directory:

```
cd /media/sd3/.Trash-karlo
```

then

```
rm -fvr WINDOWS
```

-fvr means 'force verbose recursive'
force: because it is a non-empty directory
verbose: output exactly what happens with each file/folder
recursive: delete files with in the directory and all subdirectories

---

### Post by karlo on 2008-03-14
> **alphaniner said:**
> Try the command line method:

make your way to the trash directory:

```
cd /media/sd3/.Trash-karlo
```

then

```
rm -fvr WINDOWS
```

-fvr means 'force verbose recursive'
force: because it is a non-empty directory
verbose: output exactly what happens with each file/folder
recursive: delete files with in the directory and all subdirectories

I decided to delete my WINDOWS directory because Windows won't boot anymore. At the same time, I have VirtualBox, which enables me to run Windows using a Virtual Machine which runs fast, just like you were actually on Windows XP in real time.

Now, is there a way to delete the Windows directory via GUI? Also, I deleted some directories of my NTFS drive with some files on it, everything was deleted successfully. I was able to recover more than 10 GB of space. But why does the Windows directory, not deleted?

**UPDATE**

I tried deleting it via Terminal. I received the following message:

```
karlo@karlo-laptop:/media/sda3/.Trash-karlo$ ls
WINDOWS
karlo@karlo-laptop:/media/sda3/.Trash-karlo$ sudo rm -fvr WINDOWS
[sudo] password for karlo:
rm: cannot remove directory `WINDOWS/assembly/GAC_32/System.EnterpriseServices/2.0.0.0__b03f5f7f11d50a3a': Operation not supported
```

---

### Post by Rocket2DMn on 2008-03-14
If you want to clear off the windows partition, backup any data you need from it, then reformat it, that's the correct way to go about this.  Depending on your setup, it may be possible grow your root partition to use that newly freed space.

---

### Post by karlo on 2008-03-16
Well, I just wanted to delete the Windows directory. It's impossible that you can't delete the directory under linux right? Because linux does not use any windows files, right?

---

### Post by Rocket2DMn on 2008-03-16
You should be able to delete it, but since it appears you can't, you can try booting from the LiveCD, mounting it and deleting it from there instead.  Otherwise you should just reformat the partition with GParted.

---

### Post by karlo on 2008-03-16
> **Rocket2DMn said:**
> You should be able to delete it, but since it appears you can't, you can try booting from the LiveCD, mounting it and deleting it from there instead.  Otherwise you should just reformat the partition with GParted.

Let me try... or do you think I have to be root?

---

### Post by Rocket2DMn on 2008-03-16
You should only need RW permissions, but being root might help.  You need to have write enabled on the drive, see Applications->System Tools->NTFS Configuration Tool

---

### Post by karlo on 2008-03-16
> **Rocket2DMn said:**
> You should only need RW permissions, but being root might help.  You need to have write enabled on the drive, see Applications->System Tools->NTFS Configuration Tool

Everything else is enabled since I used Ubuntu, that's why I can write anything to my NTFS drive except to delete the Windows directory.

Also it's a been annoying to see Windows XP in the boot menu before Ubuntu starts. I wonder how you can delete it.

And can I set the hda5 hard drive to boot instead of hda2 or hda3?

---

### Post by Rocket2DMn on 2008-03-16
The options for booting are in GRUB's menu.lst file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
You can delete the windows entry and the bottom that looks something like this:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

I don't understand what you're saying about setting the hda5 hard drive to boot instead of hda2 or 3.  The partition with the boot flag (*) is where GRUB is I believe.  It's possible this is on the ntfs partition, you should leave it the way it is unless you want to reinstall GRUB.  Again the best way to go about setting it correct is to reformat the partition, don't give it a boot flag, reinstall GRUB and have the boot flag go there.

---

### Post by karlo on 2008-03-16
> **Rocket2DMn said:**
> The options for booting are in GRUB's menu.lst file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
gksudo gedit /boot/grub/menu.lst
```
You can delete the windows entry and the bottom that looks something like this:
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

I don't understand what you're saying about setting the hda5 hard drive to boot instead of hda2 or 3.  The partition with the boot flag (*) is where GRUB is I believe.  It's possible this is on the ntfs partition, you should leave it the way it is unless you want to reinstall GRUB.  Again the best way to go about setting it correct is to reformat the partition, don't give it a boot flag, reinstall GRUB and have the boot flag go there.

What happened if I made some errors? If that happens what to do? Boot into some live cd and modify the grub file?

How will I know my GRUB's version? Can I update it?

---

### Post by Rocket2DMn on 2008-03-16
If you make errors so bad that you can't book into Ubuntu, you would load the LiveCD, mount your root filesystem, then restore the backup I told you to make with
```
sudo cp /path/to/mount/point/boot/grub/menu.lst.backup /path/to/mount/point//boot/grub/menu.lst
```
If you can access the recovery mode kernel, you could run
```
cp /boot/grub/menu.lst.backup /boot/grub/menu.lst
reboot
```

---

