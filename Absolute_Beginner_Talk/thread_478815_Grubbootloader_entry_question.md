---
title: "Grub/bootloader entry question"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Fenryr on 2007-06-19
Cheers, folks. Question: Why does Linux appear TWICE on the boot list when I start my machine? There is an option to choose which OS to boot into, and the top TWO entries, as near as I can tell, are BOTH the same linux partition. I ended up re-running the install after resizing both partitions (lost WinXP in the process and had to reinstall THAT, too, but no big deal), and now there seems to be two identical Ubuntu installs...Is this normal, and if not, how do I get RID of the superfluous listing?
Thanks,
Wulf

---

### Post by yabbadabbadont on 2007-06-19
The first one is your normal boot option.  The second one is to boot into single user mode (recovery) and is used whenever an update (or you) break your normal installation.

---

### Post by Tomosaur on 2007-06-19
The default setup is to include both an ordinary Ubuntu entry, and an Ubuntu Recovery Mode entry. This is standard with any Ubuntu install.

As time goes on and you update your machine, you will install kernel updates. When this happens, you will see your grub list grow. At first glance, it looks like duplicate entries, but if you examine the kernel versions, you will find that each kernel has two entries (normal, and recovery mode). I would suggest you do this, carefully check each entry, chances are you will see that they are slightly different.

Now, you can get rid of the superfluous entries pretty easily, by simply editing your /boot/grub/menu.lst file, scrolling to the bottom, and removing the entries you don't want (each entry begins with 'title' and end with 'boot'). However, I wouldn't recommend this course of action, as there are better ways of going about it:

You can set a limit on how many different kernel versions the grub menu will show. Scroll up the menu.lst file and find the line which says 'howmany=all'. Change it to a number of your choosing. I would recommend you use 'howmany=2', so that if the latest kernel version introduces problems, you can revert back to an old version easily.

Check the link in my sig for a GUI method of doing this.

---

### Post by Fenryr on 2007-06-19
right, I should've clarified that...Can't quote chapter and verse, but there is, in this orde:
a 'linux' option, 
then a 'recovery mode' option, 
then ANOTHER linux option, followed by a 
SECOND 'recovery mode' option, 
THEN "Other operating systems: Windows XP"...

As I said, the first two options, or groups of two if you count both the normal and recovery mode as a single option...It LOOKS like Linux is listed TWICE...Or am I reading this all wrong?

---

### Post by chamberlain2006 on 2007-06-19
To delete the second entry, open your grub config file as root

gksudo gedit /boot/grub/menu.lst

and put #'s in front of the whole section pretaining to the entry.  Then save it and run

sudo update-grub

And then it should be good.

---

### Post by bgissal on 2007-06-19
The four listings of the linux kernel are most likely, in this order:

1. The newest Linux kernel
2. The recovery mode for the newest kernel
3. An older kernel
4. A recovery mode for the older kernel

On a fresh install of the LiveCD, I think this is standard. They usually include the older kernels because there may be some issues with newer kernels that may not be yet resolved.

---

