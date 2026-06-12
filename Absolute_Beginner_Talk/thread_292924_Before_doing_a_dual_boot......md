---
title: "Before doing a dual boot....."
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by storybookscribe on 2006-11-04
Is it possible to have a pc dual boot if you only have Ubuntu and then want to add WinXP?  Or do you have to have WinXP on the pc first?

If you can do it with Ubuntu installed first, are there step by step instructions to show an absolute beginner how to do it without the beginner knowing a lot of jargon/lingo?

---

### Post by i.am.canadian on 2006-11-04
I could be wrong, I'm quite the beginner myself, but my understanding is that it is easiest to install linux after windows for the simple reason that Windows will overwrite your master boot record (the part of your harddrive that keeps track of the operating systems on your computer).  If you install Windows first, then linux, linux will automatically install GRUB (GRand Unified Bootloader) and configure it to work with both windows and your linux distribution.

So, the short answer is, as far as I know, install windows first.

---

### Post by annda on 2006-11-04
see my answer to your previous post. if i wasn't clear (i was trying to type really fast), just ask.

---

### Post by lemonsCC on 2006-11-04
This is quite possibly the most complete dual boot guide on the net....

[http://www.hezardastan.org/breezy_xp_dualboot/en/]("http://www.hezardastan.org/breezy_xp_dualboot/en/")

:mrgreen: :mrgreen: :mrgreen:

Oh yeah:  windows first; ubuntu second, its all in that guide.

---

### Post by mo79 on 2006-11-04
Do you plan to dual boot with two drives (i.e. one OS each drive)? If so, you can do it this way, which is nice and neat:

1. Make sure only your master drive hard drive is connected and install Ubuntu on it. Whether you dual boot or not, Ubuntu installs GRUB (it's bootloader and potential multiple OS bootloader) aswell.
2. Remove your master hard drive from the computer (go with me here) and put in your second/new hard drive into the master position. Install Windows on that.
(*You can install Windows/Ubuntu first; the order doesn't matter. The point here is to get each OS working per drive first.)
3. Put the Ubuntu drive back on master and the Windows drive as slave.
4. When you boot your computer it will automatically boot into Ubuntu, so run the program 'Terminal' in the Accessories menu. Then type (press Enter after each line). You will be asked for your password.: 

cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

In the text editing window that comes up, paste the following before the line '###BEGIN AUTOMAGIC KERNEL LIST':
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

And before the word 'hidden' in the file, put a # so it becomes '#hidden' (don't add the quotes). You can also change 'timeout' to say, 10 seconds in this file. It will make sense - I hope.

When you reboot, you'll get a menu in which to choose what OS you want. If after 10secs you don't make a choice it automatically goes into Windows (you can automatically make it go into Ubuntu by putting the 'Windows XP' code above, at the bottom of the list). If you get some kind of weird error message (tame if boots as normal, change 'root' in the above code to 'rootnoverify' You may also have to make sure your BIOS has both discs 'on'.

I've taken this info from [here.]("http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot")

It's how I dual booted. Message me if you need any help. ;) You may need to edit again if there's a slight difference in partitioning (which there shouldn't be if you're clean installing.)

The beauty of this is if you want rid of Ubuntu, just put XP back on Master and remove or format Ubuntu. If you want to remove XP you can simply undo the above code changes and format the Windows drive.

---

### Post by gn2 on 2006-11-04
Here's another (similar) way with two drives: [http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)

---

