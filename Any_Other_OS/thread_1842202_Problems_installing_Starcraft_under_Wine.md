---
title: "Problems installing Starcraft under Wine?"
date: 2011-09-10
forum: Any Other OS
---

### Post by Tywuzhere on 2011-09-10
Hey, I recently wiped my hard drive and fully installed the latest version of Linux Mint... I know it's not exactly Ubuntu 11.04... But, it's at least a version of Ubuntu, so I figured the folks around here might be able to help out.

Anyway, I put Wine on my computer and I've been trying to install Starcraft for awhile. I've tried various walk-throughs, hoping to figure it out, but nothing ever worked. I kept getting the error :" BLOCKED: The file 'file:///media/SCDisc1/StarCraft%20(Windows).exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit." I eventually found the problem, though.
My disk for Starcraft ( I have the original 1998 disk, but I lost the authentication code for it, so I bought the new 'Battlechest' about a year ago.) is under read-only. I went into permissions and tried to change the thing to read and write, as well as executable, but it would not let me because it said,"Sorry, could not change the permissions of "StarCraft (Windows).exe": Error setting permissions: Read-only file system."

Does anyone know how I could fix this? If I can get it to run as executable, then Wine should install it just fine...

---

### Post by Enigmapond on 2011-09-10
You may have better luck by installing playonlinux, which is available in the repos. Then just install the game through there.

---

### Post by Tywuzhere on 2011-09-11
Thanks, I'll give that a shot

---

### Post by Perfect Storm on 2011-09-11
Moved to Other OS/Distro Talk.

---

### Post by NightwishFan on 2011-09-11
I am not sure about how to fix this, I just copy the files off the cd and run them from a folder. Does not work with every game though.

---

### Post by sffvba[e0rt on 2011-09-11
> **NightwishFan said:**
> I am not sure about how to fix this, I just copy the files off the cd and run them from a folder. Does not work with every game though.

This case it isn't so simple... I do however give a +1 to using PlayonLinux... got SC2 to work perfectly on Ubuntu using it a while back.


404

---

### Post by Tywuzhere on 2011-09-11
Hmmm, well PlayOnLinux was a lot more straightforward than Wine, and it at least detected my Starcraft disk.
However, when I click on the SCdisk1 option in the install menu, it then tells me that the disk is not found...

So, I might try to copy the files over and run it manually that way.

I got Dwarf Fortress, and a few Windows applications to work just fine with Wine, so I know that my version of Wine is working just fine... So far it's only had trouble with Starcraft.

---

### Post by NightwishFan on 2011-09-11
Well I only use Wine to play SC1, so the problems with it are:

[LIST]
[*]On some GPUs it is very slow for some reason. There is a patch to fix it but it breaks other games so only useful for people like me that only play starcraft or have different wine installs. If you are using Nvidia you can set a key to opengl and it fixes performance.
[*]Battle.net menus look terrible, you have to switch desktops and switch back to clean them up after a while.
[*]Pretty much it, it runs great.
[/LIST]

---

### Post by sffvba[e0rt on 2011-09-12
Oops... when I see Starcraft my mind automaticaly thinks SC2... I have no experience with SC1 though :oops:



404

---

### Post by NightwishFan on 2011-09-12
You should get some experience. :) It was (still is) a fantastic game. It is from back before games were so 'hand holding'. So it becomes quite a skill to be decent in it.

To the op, please tell us if you can get it working. :) I have a third option to copying files off of the cd, you can make images of the cd and mount them.

---

