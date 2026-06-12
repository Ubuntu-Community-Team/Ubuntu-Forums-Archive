---
title: "What is Lost &amp; Found?"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by MoebusNet on 2006-12-13
I have installed a couple of windows only applications to run in wine. I am running Edgy Kubuntu. Now they show up under Menu > Lost & Found. Does this indicate a problem of some kind? If so, what do I do about it?

---

### Post by haxer on 2006-12-13
I wonder to ;)

---

### Post by MoebusNet on 2006-12-13
Be kind. If it wasn't a serious question I wouldn't have posed it. This is the newby thread, no?

---

### Post by habtish on 2006-12-13
Read explanation here [http://www.linux.com/guides/Linux-Filesystem-Hierarchy/lostfound.shtml](http://www.linux.com/guides/Linux-Filesystem-Hierarchy/lostfound.shtml)
> 
 Linux should        always go through a proper shutdown. Sometimes your system might crash        or a power failure might take the machine down. Either way, at the next        boot, a lengthy filesystem check (the speed of this check is dependent on        the type of filesystem that you actually use. ie. ext3 is faster than ext2        because it is a journalled filesystem) using fsck will be done. Fsck will        go through the system and try to recover any corrupt files that it finds.        The result of this recovery operation will be placed in this directory.        The files recovered are not likely to be complete or make much sense but        there always is a chance that something worthwhile is recovered. Each        partition has its own lost+found directory. If you find files in there,        try to move them back to their original location.


---

### Post by MoebusNet on 2006-12-13
habtish - Thank you for your reply. However, as I indicated in my original post, when I installed these applications they showed up on the Kubuntu Desktop under Menu > Lost & Found. These are new installations and the computer has not lost power or been shut down. Is this the same thing you refer to? If so, what should I do?

I will bookmark the Linux.com website; thank you for that.

---

### Post by real_ate on 2006-12-13
hey MoebusNet, i have a suggestion that i hope will not be taken the wrong way. i believe you should ALWAYS be able to bring things down to a "why it happened" and "how to do (or not do) it again". but does it really matter that they are in the lost and found? just move them is my suggestion... 

please don't take that as a brush off cos i'm not about that! just as a method of getting towards the "why", did you resart the pc after installing the programs or were they there as soon as it was finished installing?

---

### Post by MoebusNet on 2006-12-13
real_ate - sorry i took so long to get back; i was out to lunch (seriously!) you are asking my very question: does it matter if the applications i installed wound up in "lost & found" in the menu? is this an indicator that something is amiss (even though the applications work well)? if so, what do i need to do to fix this? if not, should i move them to the menu (under for example: games or office)?

---

### Post by roachk71 on 2006-12-13
This isn't really a problem. The Lost & Found submenu is simply a place where (after some updates and distribution upgrades) application entries which don't fit into the other categories are linked, so they can be used later.

If anything's been done about the menu editor crash bug, you could use that to move the links into the appropriate categories.

---

### Post by MoebusNet on 2006-12-13
thank you roachk71! i think that answers all of my questions. i do appreciate the help (bowing)

---

### Post by roachk71 on 2006-12-13
Oops!

I forgot to add: I'm not sure whether they've placed kmenuedit in the system menus. If they haven't, type kmenuedit in the command line (use Alt-F2).

---

