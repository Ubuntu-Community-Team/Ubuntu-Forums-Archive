---
title: "Windows has safe mode to fix problems? And Ubuntu?"
date: 2012-02-05
forum: Any Other OS
---

### Post by bonedriven on 2012-02-05
I have reinstalled the os 8 times in two days due to that ubuntu randomly can't boot up. 

Is reinstallation the only solution to solve a can't-boot-up problem?

---

### Post by ikt on 2012-02-05
Ubuntu has recovery mode.

Hold down shift while the computer boots up.

Do you get any error messages on the screen when the computer doesn't boot up? or are there any images or anything?

---

### Post by bonedriven on 2012-02-05
Thank you. 

It is a persistent pendrive OS, which to me is ridiculously unstable (The one I installed in my virtual machine works well though.)

Actually this time I'm having a problem logging in.

After a system update, I created a new admin account with password. Now after restart, I can see my account name but no box for enter my password. Instead it's a "log in" button, on which if I click, it shows "authentication failed". Now I am out of the OS.

---

### Post by Paddy Landau on 2012-02-05
> **bonedriven said:**
> It is a persistent pendrive OS...
Which version of Ubuntu did you install on the pendrive, and what method did you use to do so?

---

### Post by bonedriven on 2012-02-05
Currently it's Mint 12. I think it's almost the same with Ubuntu right?
I have tried universal-usb-installer and LiLi. The most recent one is built by LiLi, on a 8G pendrive, and the persistent capacity is 4G.

Now I can't even have a log in screen, there are many errors about :

EXT2-fs(loop1): error: ext_lookup: deleted inode referenced [random number here]
error: EXT2_free_blocks: bit already cleared for block [random number,e.g 839088)]

---

### Post by Paddy Landau on 2012-02-05
Mint is based on Ubuntu, but it is not part of the Ubuntu family. This thread should have been put in the [Other OS/Distro Talk]("http://ubuntuforums.org/forumdisplay.php?f=401").

If you follow the instructions on the [Ubuntu download page]("http://www.ubuntu.com/download/ubuntu/download") for creating a USB (section 2), it may work -- but as it's Mint, not Ubuntu, I cannot be sure of that.

I would suggest that you check the MD5 sum of your download (to ensure that it has downloaded correctly); completely reformat your pendrive; then try again to create your pendrive.

If you want to try the Ubuntu family, use either the default Ubuntu if your computer is fast enough and has enough RAM (it is much slower from a pendrive than is a native installation), or [use Lubuntu]("https://wiki.ubuntu.com/Lubuntu"), which is designed for speed.

EDIT: You may find that FAT 32 works better with a pendrive than ext2 or ext4.

---

### Post by howefield on 2012-02-05
Thread moved to "*Other OS/Distro Talk*" and prefixed appropriately.

---

