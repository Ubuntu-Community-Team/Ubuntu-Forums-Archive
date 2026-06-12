---
title: "Where is the boot.ini file?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by Vish555 on 2007-04-29
Just wondering how to locate it because i can't find it. At the moment i am in ubuntu and cannot boot into xp. Any help would be great. Thx 

Vish

---

### Post by Cypher on 2007-04-29
Boot.ini is sitting in the system partition of Windows. Usually, that's C:\..

---

### Post by Vish555 on 2007-04-29
erm its not there. I thought it might be hidden. How do i find it?

---

### Post by whee on 2007-04-29
The exact location is C:\boot.ini of a partition where Windows is installed.

PS: It could be hidden, so you have to enable the option to view hidden files and folders.

---

### Post by Terl on 2007-04-29
> **Vish555 said:**
> erm its not there. I thought it might be hidden. How do i find it?

Yes, it is hidden.  It is in C:\  Make sure you check permissions to see hidden files.

Did you just install Ubuntu and now you can't get back to XP?  Or did something happen to your boot loader?

---

### Post by Vish555 on 2007-04-29
yeah i can't get back into xp. think the bootloader can't find xp. Why? And how do i show hidden files and folder?

---

### Post by Terl on 2007-04-29
> **Vish555 said:**
> yeah i can't get back into xp. think the bootloader can't find xp. Why? And how do i show hidden files and folder?

Did you allow Ubuntu to install the Grub bootloader?  What is your basic setup (ie, windows and Ubuntu on one disc, windows on one disk, Ubuntu on the other).  Is windows an option at all on the Grub screen (if you installed grub).

Oh, to see hidden files in windows:  Click my computer, when it opens hit tools on the menu bar and then folder options.  On the tab for view is a selection for "show hidden files".  If this is checked the hidden files will be visible.  Be careful with some of these.  Messing with some of them can break windows worse than it already is :)

---

### Post by Vish555 on 2007-04-29
yep windows is an options and grub did install. Windows gives the error: missing hal.dll file.

---

### Post by oilchangeguy on 2007-04-29
read this:
[http://support.microsoft.com/kb/330184/en-us](http://support.microsoft.com/kb/330184/en-us)

---

### Post by Vish555 on 2007-04-29
WOOT WOOT!!! I just fixed it.!!!!
Thx so much for all your help . All of u. I could hug all of you right now and i prob would if i knew where u lived. :P Thx again so much. I finally have a dual booting system. :D:D:D:D:D

---

### Post by Terl on 2007-04-29
> **Vish555 said:**
> WOOT WOOT!!! I just fixed it.!!!!
Thx so much for all your help . All of u. I could hug all of you right now and i prob would if i knew where u lived. :P Thx again so much. I finally have a dual booting system. :D:D:D:D:D

Most excellent.  Hey, you learned a lot too.  And you learned what the open source community is like.  The community is a major plus with Linux, and Ubuntu has one of the best.

---

### Post by whee on 2007-04-29
Oh wait, you can't find the partition in Ubuntu that holds the partition where Windows is installed? Or just the file?
Because if the boot.ini file is not there, then Windows is not able to boot.



Edit: Posted this too late, the issue seems to be fixed already :)

---

