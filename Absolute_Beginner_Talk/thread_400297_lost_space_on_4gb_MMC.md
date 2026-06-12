---
title: "lost space on 4gb MMC"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by ushills on 2007-04-03
I have a 4gb MMC that I have lost space on.

I deleted some files from it then emptied the trash folder, my PDA reports it having 560Mb free (so does my work PC).  Ubuntu says it only have 76Mb free.

Any ideas why this should happen.

---

### Post by jvc26 on 2007-04-03
Try going to the pda, viewing hidden files and then checking that the .Trash folder is empty. If its not, go and get rid of the files in it, as it may not have recognised that you deleted the trash.
Il

---

### Post by Michaelt74 on 2007-04-03
Did you run a backup? If so, this could possibly be the problem:

[http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/](http://opensourceroolz.wordpress.com/2007/02/01/backing-up-and-the-driver-space-eater/)

---

### Post by ushills on 2007-04-04
I didn't backup my memory card and the .trash folder is definately empty, Windows reports now over 500Mb free and Linux is still saying less than 100Mb.  In windows I can copy more information to the card in Linux I cannot due to insufficeient space.

It appears as if Linux is storing the file space available rather than checking each time the card is mounted.

I am running out of ideas and solutions.

---

### Post by Jetjoint on 2007-10-16
This is a bit of a crazy work around .......... I have the same problem........but it works for me.

After inserting the card or usb stick I start gparted. I select that drive from the pulldown menu top right.
I then right click on the entry for that drive in the main window and select unmount.

I then go up to the Gparted menu top left and select refresh devices.

Magically the missing space reappears .....

To use the drive just remount it by selecting it from the Computer menu........


Hope this helps

---

