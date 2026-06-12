---
title: "Noob questions: Xserver and mounting"
date: 2005-05-17
forum: Absolute Beginner Talk
---

### Post by zenlord on 2005-05-17
Hi,

First off, I would like to post a general Linux-question: What book or other instrument could be recommended for a complete Linux-newbie, considering:
- I have learnt how to operate/install/modify windows and several apps on my own;
- I have learnt how to build/tune/overclock PC's on my own;
- I have learnt how to build websites using HTML/CSS/PHP/MySQL on my own;

Since I hate reading 500 pages of theory, I think something like '500 problems and their solutions' would be best for me, but I doubt this exists. Of course, I could crash several linux-fora, but I feel kinda awkward being a complete newbie :)

Then, my Ubuntu-questions (5.04):
1. How do I mount a windows-partition (FAT32 / NTFS)? I recently installed a dual boot Ubuntu/Win2k on an older machine and everything went perfect. I was even able to uninstall FF 1.0 through add/remove progs ( \\:D/ ) and install FF 1.0.4 with adobe reader in terminal (what an accomplishment!! - still: much more than I was able to do with SuSe9 a while ago). I would however like to play some music residing on my othe partition that I cannot mount (or don't know how to do it)...

2. On another machine (x64 - Ati Radeon x800xl) I was not able to start the live CD: the Xserver could not be started. This is probably caused by Ati and its drivers, but all I got was a DOS-like screen. If the same happened to me when installing Ubuntu 5.04 on this system, could I just use the Ati-guides and type all commands in this screen? In other words: Is this screen a root-terminal? And if/when this succeeds, how do I start Xserver / Gnome?

3. When shutting down, I can tick the box next to 'save my settings'. Which settings are saved? Do these settings include the auto-mount of partitions mounted as in question 1? Or are these settings about simply changing backgrounds?

THX!!
PS: If you can reply with solely linking me to answers, that's ok - I'm willing to learn, but have difficulties to find out where to start...

Zl.
PS: thx Ubuntu and Canonical to send me the requested cd's - passing them on as we speak!

---

### Post by Ali_Baba on 2005-05-17
Here you can find answer to your first question about mounting. [http://www.ubuntuforums.org/showthread.php?t=34578](http://www.ubuntuforums.org/showthread.php?t=34578) :)

---

### Post by Laemel on 2005-05-17
1.  You'll probably want to put it into your /etc/fstab file so that it's always mounted, rather than manually mounting it after every boot.  So, type```
$ sudo gedit /etc/fstab
``` and add a line that looks something like this```
/dev/hda1  /home/zenlord/Windows vfat  defaults,umask=0000  0 0
``` So, the first part is what partition it is.  if you're not sure, you can look through the avaliable partitions with:```
fdisk -l
``` (that's a lowercase L btw).  The second part is the folder to mount it in.   You can do that wherever you want, just make sure the folder exists and that you have access to it.  "vfat" tells Linux that's it's a FAT partition, and umask=0000 gives users read/write access to it.

For more info on mounting windows partitions, check out the "Setting your fstab" section [here](http://gentoo-wiki.com/HOWTO_Mount_MS_Windows_partitions_(FAT,NTFS)#Setting_your_.2Fetc.2Ffstab)

2.  Yes, it's just a terminal.  Normally, if the prompt ends in a $ you have user privaleges, and if it ends in a # you have root access.  Of course you can always just use sudo if you need root access and don't have it, so either way you can do what you need to.  If you get it set up, you can type "startx" or just reboot to start X.

3.  Your "Window settings" are stored.  That means that for any application that supports it, it will save the "state" of the program.  For instance, if you have a terminal window open, when you log in again that window will still be there, in the same spot and everything.  If Gaim is running, it will come back after you restart, etc.  It doesn't mean stuff like your wallpaper. That stuff stays there by itself.  It's just talking about applications.

---

### Post by zenlord on 2005-05-17
THX all!

Will be dealing with this stuff after work, but I don't expect many problems here, considering your detailed answers!

again, thx!

Zl.

---

