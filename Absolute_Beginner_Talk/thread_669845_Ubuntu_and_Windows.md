---
title: "Ubuntu and Windows"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Red Rebel on 2008-01-16
Currently have a machine with Windows XP installed (NTSF filesystem). Would like to dual boot with Ubuntu. Already have a seperate installation of Ubuntu on another HD. Rather than installing Ubuntu from scratch,  would like to, somehow, take an image of current Ubuntu Install. and copy it onto the Windows HD. I realize that the XP partition will have to be shrank to make room for the Ubuntu installation.Should be able to use Gparted live CD for that task.  Current Ubuntu installation (the other hard drive), is installed under the ext3 file system. Would like to, then, use Grub as my bootloader. Would like to also be able to access all  Windows directories from terminal. Can anyone give me detailed instructions for my specific situation? Any help would be greatly appreciated...

---

### Post by aysiu on 2008-01-16
> **Red Rebel said:**
> Currently have a machine with Windows XP installed (NTSF filesystem). Would like to dual boot with Ubuntu. Already have a seperate installation of Ubuntu on another HD. Rather than installing Ubuntu from scratch,  would like to, somehow, take an image of current Ubuntu Install. and copy it onto the Windows HD. I realize that the XP partition will have to be shrank to make room for the Ubuntu installation.Should be able to use Gparted live CD for that task.  Current Ubuntu installation (the other hard drive), is installed under the ext3 file system. Would like to, then, use Grub as my bootloader. Would like to also be able to access all  Windows directories from terminal. Can anyone give me detailed instructions for my specific situation? Any help would be greatly appreciated...
I think your best bet would be to install Ubuntu from scratch (do a barebones installation with a mini.iso if you think the regular installation would take too much time).

Then use [this tar backup method](http://ubuntuforums.org/showthread.php?t=81311&highlight=howto+back+up+restore) to back up your current installation and then restore it to the other computer. You may have to adjust the /etc/fstab file, though.

---

### Post by rbc on 2008-01-16
Just to be clear....Ubuntu is installed on a completely separate computer, not a second HD on the same computer, right?

---

### Post by Red Rebel on 2008-01-17
Well, actually, the ubuntu installation is installed in a seperate hd that is not installed on any computer. I can install the Hd on a computer for back up purposes if need be.

---

### Post by rbc on 2008-01-17
Unless there was something dear to you about the computer setup that Ubuntu used to be on, I's follow aysiu's advice. You smarter folks out there correct me if I'm wrong, but I don't think one can make a duplicate of a HD, then just throw it into a computer with different hardware. if it's just certain files you want off the old Ubuntu HD, just copy them, do the fresh install, put them back onto the new dual boot

---

### Post by thelatinist on 2008-01-17
Yeah, you'll run into all sorts of hardware problems if you try to do that.  Is there a particular reason you don't want to do a fresh install of Ubuntu?

---

### Post by Red Rebel on 2008-01-23
well, the main reason I do not want to do a fresh install is, that, I have a lot of software and plugins installed, some of which where difficult to install for a newbie like me. However, I am begining to realize, that a clean Ubuntu install may be easier after all. Since I have Xp now on this computer. The first thing I should do is shrink the partition down with Gparted live CD right?

---

### Post by thelatinist on 2008-01-23
> **Red Rebel said:**
> Since I have Xp now on this computer. The first thing I should do is shrink the partition down with Gparted live CD right?

First thing to do is defragment your Windows partition several times and backup your essential data.  *Then* you can resize that partition with the GParted live CD.

---

