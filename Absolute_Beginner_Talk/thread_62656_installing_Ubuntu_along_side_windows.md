---
title: "installing Ubuntu along side windows"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by Draconum on 2005-09-05
Hey,
ok I'm downloading the Ubuntu system right now. and I'm planning on installing it on a 50 gig partition on my hardrive... I just want some tips so make sure everything goes smoothly since I've never installed two OS on one system... ontop of the fact that I've never used linux.
Thanks.


Chris

---

### Post by ubuntme on 2005-09-05
It is no problem, linux is nice and live well with windows on another partition.  You just need to know which partition you want to install on :)

You will get a boot menu called grub where you choose which dist to run.  Ubuntu will be the default, but you can change that to windows if you wish (after the install).

Good luck with your install!

---

### Post by Steve1961 on 2005-09-05
You might want to take a look at the following guides before you do anything.  

[https://wiki.ubuntu.com//WindowsDualBootHowTo](https://wiki.ubuntu.com//WindowsDualBootHowTo)
[https://wiki.ubuntu.com/Installation/I386](https://wiki.ubuntu.com/Installation/I386)

You will need to shrink your 50gb partition if you have no more free space, as well as creating a small swap file.  Format the first partition as ext3 and mount it as root - you'll see these options in the installer.  Just highlight them and press return to see the options available, and follow along.  Make sure you also format the swap partition

After the partitioning stage everything else is mostly automatic.  The installation will install grub in your mbr and when you re-boot you should be able to access ubuntu or windows from the grub menu.  Just make sure you don't choose the 'take over entire disk' option.

---

