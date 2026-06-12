---
title: "ibook g3 &quot;reinstall&quot;"
date: 2009-01-20
forum: Apple Hardware Users
---

### Post by blampars on 2009-01-20
I've been using this laptop just to play with, mess around and generally screw things up to learn to fix them.

I originally installed ubuntu server 8.04

Is there any way I can use aptitude to remove all the packages and take me back to a base server install? There's so many packages on here it'd take me forever to seek out and remove what I dont want, and I'd just like to start completely over.

Oh, the reason for this question is my cd drive no longer works, so I cant format and reinstall that way ;)

thanks for your time,
-b

---

### Post by pxwpxw on 2009-01-20
> **blampars said:**
> I've been using this laptop just to play with, mess around and generally screw things up to learn to fix them.

I originally installed ubuntu server 8.04

Is there any way I can use aptitude to remove all the packages and take me back to a base server install? There's so many packages on here it'd take me forever to seek out and remove what I dont want, and I'd just like to start completely over.

Oh, the reason for this question is my cd drive no longer works, so I cant format and reinstall that way ;)

thanks for your time,
-b

If you have enough space on your hard disk, the easiest solution is probably to make a second clean ubuntu installation.
Howto depends on what existing systems (Macos, linux ) and partitions you have, and whether you have a workable existing gparted or parted in ubuntu on the HD.

---

### Post by blampars on 2009-01-20
well, i only have a 10gb hard drive, 4 of which is free space at this point.

I seem to have found something of interest _[here]("http://ubuntuforums.org/showthread.php?t=261366")_, even found a list of installed packages on a fresh 8.04 ubuntu server install in that thread.

I'm just having problems using this list to remove everything but the packages listed for the server install..

I think if I could get that going, I'll have done what I had in mind. :)

this is the command I've found to use to uninstall all but the base packages (from the list i have, named package.selections)
```
sudo dpkg --set-selections < /home/username/package.selections && apt-get dselect-upgrade
```

however, I end up with the following
```
could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

not sure where to go from this point, but I think i'm headed somewhat in the right direction.  I shall keep looking.

any more help or thoughts would be appreciated!
-b

---

### Post by pxwpxw on 2009-01-20
> **blampars said:**
> well, i only have a 10gb hard drive, 4 of which is free space at this point.

I seem to have found something of interest _[here]("http://ubuntuforums.org/showthread.php?t=261366")_, even found a list of installed packages on a fresh 8.04 ubuntu server install in that thread.

I'm just having problems using this list to remove everything but the packages listed for the server install..

I think if I could get that going, I'll have done what I had in mind. :)

this is the command I've found to use to uninstall all but the base packages (from the list i have, named package.selections)
```
sudo dpkg --set-selections < /home/username/package.selections && apt-get dselect-upgrade
```

however, I end up with the following
```
could not open lock file /var/lib/dpkg/lock - open (13 permission denied)
unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

not sure where to go from this point, but I think i'm headed somewhat in the right direction.  I shall keep looking.

any more help or thoughts would be appreciated!
-b

You need to add 'sudo' in each part of the command -

 && sudo apt-get dselect-upgrade

Yes try removing packages, but if you are unlucky it can result in a mess - then the re-install is often quicker and easier.

---

### Post by blampars on 2009-01-20
> **pxwpxw said:**
> You need to add 'sudo' in each part of the command -

 && sudo apt-get dselect-upgrade



ah yeah i see now where I went wrong there.

I ended up doing essentially the same thing, just one command at a time using this guide _[here]("http://inportb.com/2007/10/24/how-to-save-a-list-of-installed-packages-and-reinstall-the-packages-later/")_

thanks for your patients and time,
-b

---

### Post by pxwpxw on 2009-01-20
> **blampars said:**
> ah yeah i see now where I went wrong there.

I ended up doing essentially the same thing, just one command at a time using this guide _[here]("http://inportb.com/2007/10/24/how-to-save-a-list-of-installed-packages-and-reinstall-the-packages-later/")_

thanks for your patients and time,
-b

OK, that is a good reference, I sometimes have the same problem.

---

