---
title: "Can't find &quot;Disks Manager&quot; to make Windows partition available"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by John RG on 2006-12-31
New user.  New PC.  Installed Windows XP first then Untubu Edgy 6.1.  Most things work.  I'm trying to see my Windows partition but can't.  I've found these instructions:
Make Windows partitions available from Ubuntu

Windows partitions should be automatically available from any Ubuntu system. If they are not, you can make them available using the Disks Manager.

   1.	Open System &#8594; Administration &#8594; Disks.

      					
   2. Select the correct hard disk, and click Partitions.

etc.  But I can't find "Disks Manager"...  I've looked in the Package Manager, Applications etc.  No luck.  What have I missed?

Thanks

John

---

### Post by NeoLithium on 2006-12-31
In gnome, there's the 3 menus available, click on system first, move down to the administration part in that menu, and then you should be able to select disks from there.

---

### Post by John RG on 2006-12-31
No, tried that.  I see a Device Manager, a Gnome Partition Editor, Update Manager etc etc, but no Disks Manager.

---

### Post by NeoLithium on 2006-12-31
Curse me for not having used GNOME in a while...does it have anything in the device manager?

---

### Post by John RG on 2006-12-31
Found a previous posting on this: [http://ubuntuforums.org/showthread.php?p=1931861&highlight=disks+manager#post1931861](http://ubuntuforums.org/showthread.php?p=1931861&highlight=disks+manager#post1931861)

Apparently "Disks Manager" was in Dapper but is not in Edgy.

---

### Post by handy on 2006-12-31
**@JohnRG**,  You will have to edit your **/etc/fstab** & create a folder in **/media/*"your choice?*"**

There is info' on this in the supplied help installed on your computer, it is also easy to find by searching the forum.

Please don't take me the wrong way, this is not a RTFM response, I'm just trying to point you in the right direction :) 

Searching the forum for **fstab** will solve your problem pretty quickly... :KS 

**[Edit:]**  How could anyone expect a new user to know that **fstab** is what they should be looking for?!

All the best for the new year!

---

### Post by moshuptrail on 2006-12-31
Another solution would be to erase Edgy and re-install Ubuntu Dapper (6.06).
Disk Manager is included there.  Also, Dapper is sort of tried and true and I would recommend it over Edgy for new users.

---

### Post by Bartender on 2006-12-31
Hey, guys , unless the Windows drive or partition has been addressed via fstab it won't magically appear via the Disk Manager anyway.  I tried that way back when.  Follow aysiu's directions (or any other version) for making Windows drives auto-mounted via fstab.  I think you have to reboot.  Maybe not?

I do miss Disk Manager.  I thought it was handy.

---

