---
title: "Ubuntu on two drives, how do I remove it from one?"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Krystoll Meth on 2007-03-27
Have Ubuntu running on two drives, had Edgy on one of them, then installed Feisty beta on the other.  Now that I have Feisty working great, how do I remove Ubuntu properly from the other drive (the Edgy one) without causing the bootloader to go into digital convulsions?

BTW, if any are curious as to why I have it on two drives, I had installed it on both in case I screwed something up terribly, and on the drive where Feisty now is, I attempted using the upgrade tool which didn't work well at all and did a clean install of Feisty on it.

---

### Post by tonyr1988 on 2007-03-27
This should work, but wait until someone smarter than me verifies it before you do it (or backup all your data, just in case):

Go into the Ubuntu you want to keep (Fiesty). Open up a Terminal:

> sudo apt-get install gparted
killall gnome-panel

Then go to System >> Administration >> GNOME Partition Editor

You can change the hard drive in the top-right corner of the screen. You can right-click and delete partitions from there. 

Then go back to your Terminal:

> sudo update-grub

---

