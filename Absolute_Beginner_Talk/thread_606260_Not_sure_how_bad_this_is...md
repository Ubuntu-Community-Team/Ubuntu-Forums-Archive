---
title: "Not sure how bad this is.."
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-11-07
[FONT="Arial"][SIZE="2"][/SIZE][/FONT]

Hi all..

Not sure how bad I screwed up but was trying to speed up the boot process and upon restarting received this error:

"kernel panic" not syncing: vfs unable to mount root fs-unknown block 0.0

How bad is it?  And do i need to reinstall ubuntu for things to work again?

---

### Post by llamakc on 2007-11-07
What did you do to "speed up the boot process"?

---

### Post by sports fan Matt on 2007-11-07
All i remember dloing was removing the splash screen from startup through terminals so that i only saw text starting the machine then it booted..other then that im not sure..that couldnt have done it though im almost certain..

Does the crux of the message say "HEY!, What are u attempting cause i cant boot the machine?"

---

### Post by dhobbs on 2007-11-07
It can't mount your root drive.

The vfs is the virtual file system used to mount or access your actual drive.  It can't do this so it's obviously in a state of panic.  I guess it's like going home and realizing that your home is no longer there.

FUBAR, in other words.

You should probably look into using a LiveCD to repair the boot image, or something like that.  I'm doing a google search now to see if I can find anything.

---

### Post by sports fan Matt on 2007-11-07
Dh,

Thats what i figured, luckily i have a desktop install cd that I can boot from and in a short period of time it should be up and running.  I figured I fubared the drive when I saw that error.  I am not all that new tp computers ..:)  Thanks again:)

---

### Post by dhobbs on 2007-11-07
As a suggestion for the future, if you make changes to grub or to the splash image, resolution, or whatever, it's not a bad idea to run.```
sudo update-initramfs -u -k `uname -r`
```

That should rebuild the boot image that you will be using so it doesn't try to do things it shouldn't.

---

### Post by sports fan Matt on 2007-11-07
Dh,

Thanks..I must say the community is very friendly and the terminals arent honestly as hard as I thought.  Its not as hard as I thought learning linux and the payoffs are major..I have even burned the cd for a friend and the wife wants ubuntu when we get her own computer..Thanks again

---

### Post by 3rdalbum on 2007-11-07
Did this hack that you tried involve editing an entry in the GRUB bootmenu list? (which is how I would get rid of the splash screen, personally)

If so, then you might have accidentally forgotten to put a space between two arguments in the boot menu, with one of the arguments being the location of the filesystem.

At the GRUB bootmenu, go into your Recovery Mode entry, and once you're into Ubuntu, check the modifications you made to the menu.lst.  If you don't have a Recovery Mode entry, highlight your Ubuntu kernel entry and press the "e" key twice. Then scroll back using the arrow keys and have a look. If you find that a space is missing, add one in, then press Enter and get out of there, then boot the entry.

---

