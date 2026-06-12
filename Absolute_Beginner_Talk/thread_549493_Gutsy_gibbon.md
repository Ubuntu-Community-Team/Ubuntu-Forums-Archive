---
title: "Gutsy gibbon"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by jrharvey on 2007-09-12
I am new to Ubuntu and have found that it is the best OS ever (even over OS X). I have feisty right now but heard all this talk about the new Gutsy that is coming out. What makes it different and why should I upgrade??? When it does come out do I have to erase fiesty or is there an upgrade option???

---

### Post by Tyke91 on 2007-09-12
there's no one specific reason to switch... but it will be more efficient, easier to use, and will have more features (like one of those spiffy desktop searches)

when it comes out there will be an option to upgrade, but i'd rather start over again... back up your data and reinstall for the best install :D

---

### Post by RedSquirrel on 2007-09-12
> **jrharvey said:**
> I am new to Ubuntu and have found that it is the best OS ever (even over OS X). I have feisty right now but heard all this talk about the new Gutsy that is coming out. What makes it different and why should I upgrade??? When it does come out do I have to erase fiesty or is there an upgrade option???

I'm not sure about new features, but it should fix some of the bugs that Feisty has. If you're happy with Feisty, there's no rush to upgrade/reinstall.

It comes out next month, probably towards the end of the month. A new version of Ubuntu is released every six months.

The version number is year.month. Feisty, for example, was released in April 2007, so it is Ubuntu 7.04. Gutsy is 7.10. ;)

---

### Post by bodhi.zazen on 2007-09-12
You should be able to upgrade feisty once gutsy is available.

You can also consider making a separate /home (or /data) partition to make upgrading a little easier ...

HTH

---

### Post by jrharvey on 2007-09-13
My only complaint about fiesty is that it doesnt have a dock option (like OS X) built into the gnome desktop. I mean it should be an option. The panel is pretty cool but I wish it had more options. Do you think that Gutsy will add more options such as that or is it a Gnome thing and not the OS?

---

### Post by philinux on 2007-09-13
> **bodhi.zazen said:**
> You should be able to upgrade feisty once gutsy is available.

You can also consider making a separate /home (or /data) partition to make upgrading a little easier ...

HTH

I have a /home folder would that get overwritten in the upgrade?

---

### Post by Terl on 2007-09-13
> **philinux said:**
> I have a /home folder would that get overwritten in the upgrade?

Is it a separate /home partition...not folder?  Did you set up a separate partition when you installed?  If you did set a separate home partition when you install then new version you just tell it not to reformat your /home partition.

---

### Post by tito2502 on 2007-09-13
> **jrharvey said:**
> My only complaint about fiesty is that it doesnt have a dock option (like OS X) built into the gnome desktop. I mean it should be an option. The panel is pretty cool but I wish it had more options. Do you think that Gutsy will add more options such as that or is it a Gnome thing and not the OS?

There are a few docks you can try out, Avant is alright and Kiba isn't bad. Might be a little tricky for a beginner to get going mind.

There is no real reason Ubuntu doesn't have a dock, it probably just doesn't suit it. I, personally, think it sacrifices too much workspace area and doesn't add that much functionality.

instead of a dock I like to drag the icons of my most used programs onto the panel.

---

### Post by philinux on 2007-09-13
> s it a separate /home partition...not folder? Did you set up a separate partition when you installed? If you did set a separate home partition when you install then new version you just tell it not to reformat your /home partition.

It's just a folder thats how it was installed. What's the best plan cos I intend to upgrade to gutsy.
[edit]
 sudo fdisk -l
Password:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14477   116286471   83  Linux
/dev/hda2           14478       14593      931770    5  Extended
/dev/hda5           14478       14593      931738+  82  Linux swap / Solaris

---

### Post by bodhi.zazen on 2007-09-13
Well, the upgrade should go without any problem.

If you want to re-install and keep all your data in /home you need to move /home to a separate partition :

Like this : [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by jrharvey on 2007-09-13
Its not that big of a deal to keep all my files. I dont have anything that Is really important yet. As for the dock....... I just feel like all of the other options are waaaay to memory hungry and don't really function the same. I tried them all and surprisingly settled for the Gdesklets starter bar because it didn't require beryl. I keep having problems with it and even though i have a brand new computer it still has alot of bugs for me at least. AWN seemed promising but I can't seem to get this black screen from behind it.

---

### Post by bodhi.zazen on 2007-09-13
> **jrharvey said:**
> Its not that big of a deal to keep all my files. I dont have anything that Is really important yet. As for the dock....... I just feel like all of the other options are waaaay to memory hungry and don't really function the same. I tried them all and surprisingly settled for the Gdesklets starter bar because it didn't require beryl. I keep having problems with it and even though i have a brand new computer it still has alot of bugs for me at least. AWN seemed promising but I can't seem to get this black screen from behind it.

You are gettin so off topic you might want to start a new thread. 

Who would think to look for a question on AWM in a thread titled "Gutsy gibbon" ???

At any rate, see this thread : [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

> _**[SIZE="4"]Notes (please read!):[/SIZE]**_
**AWN requires a compositor** (like beryl or compiz) to work properly. 

**AWN is still early in development, and contains many bugs.** *Please* help development by reporting any bugs you find on the project's homepage (see above).

---

