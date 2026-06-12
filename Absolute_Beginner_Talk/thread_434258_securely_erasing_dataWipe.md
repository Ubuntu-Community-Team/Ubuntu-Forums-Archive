---
title: "securely erasing data/Wipe"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by atmartin50 on 2007-05-05
Hi all,

I was using an open source program called Eraser in my XP days, which effectively deleted files and had an easy-to-use graphic interface. Unfortunately it does not seem to be available for Linux.

I found the program Wipe in Synaptic and proceeded to download and install it. However, I'm not sure how to launch it. Is there a GUI for it? If not, which command do I use to run it? Typing 'wipe' does not seem to do it? Could it be that I'm missing some other files which are needed to use the program?

Any help would be much appreciated!

---

### Post by yabbadabbadont on 2007-05-05
wipe is a command line tool.  You just need to use it in a terminal window.  Example: "wipe filetobewiped"

Run "man wipe" for details.

---

### Post by jfinkels on 2007-05-05
> **atmartin50 said:**
> Hi all,

I was using an open source program called Eraser in my XP days, which effectively deleted files and had an easy-to-use graphic interface. Unfortunately it does not seem to be available for Linux.

I found the program Wipe in Synaptic and proceeded to download and install it. However, I'm not sure how to launch it. Is there a GUI for it? If not, which command do I use to run it? Typing 'wipe' does not seem to do it? Could it be that I'm missing some other files which are needed to use the program?

Any help would be much appreciated!

The command line program "shred" will get this done for you. Type ```
man shred
``` for more information.

If you still want to use wipe, type ```
man wipe
``` for more information on usage.

---

### Post by bashologist on 2007-05-05
This might not be what you're looking for but it's similar at least if not; There's a program for securely erasing entire hdds. It's called Darik's Boot and Nuke. It was on g4tecktv once. [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by starcraft.man on 2007-05-05
I have used dban before, and so have many of my tech friends. It is a great utility to wipe drives, I can't recommend it highly enough if your mission is simply to wipe a whole drive of its data and make sure its unrecoverable.

---

### Post by yabbadabbadont on 2007-05-05
> **starcraft.man said:**
> I have used dban before, and so have many of my tech friends. It is a great utility to wipe drives, I can't recommend it highly enough if your mission is simply to wipe a whole drive of its data and make sure its unrecoverable.

The only way to make sure that it is unrecoverable is to use acid or extreme heat (enough to melt the platters).  Otherwise the data (at least some of it) can be recovered if the attacker is willing to spend enough time, money, and has the proper equipment.  Further, modern drives will sometimes relocate bad sectors on the fly without any notice to the user leaving the original untouched...

---

### Post by atmartin50 on 2007-05-17
Thanks for your speedy replies, folks!

I will give both Wipe and Shred a try. I must admit that the former Windows user in me would prefer something with a GUI, but that's an urge which I can repress.

---

### Post by Wim Sturkenboom on 2007-05-17
from man shred
> CAUTION: Note that shred relies on a very important assumption: that the filesystem overwrites data  in  place.
This  is  the  traditional way to do things, but many modern filesystem designs do not satisfy this assumption.
The following are examples of filesystems on which shred is not effective:

* log-structured or journaled filesystems, such as those supplied with AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

* filesystems that write redundant data and carry on even if some writes fail, such as RAID-based filesystems

* filesystems that make snapshots, such as Network Appliance's NFS server

* filesystems that cache in temporary locations, such as NFS version 3 clients

* compressed filesystems

This probably will apply to any wipe utility.

---

### Post by hyper_ch on 2007-05-17
A simple way to "securely wipe" your data is to just encrypt the whole partition... as long as the encryption is strong it doesn't matter if the data contained within is securely wiped :)

---

