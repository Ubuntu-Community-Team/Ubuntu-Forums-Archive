---
title: "Just restored my rig from backed up home. Some progs not installed now is this normal"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-30
Like mplayer for instance that I installed ages ago is not installed now I've restored from a system hard disk crash. I've restored from my backed up home folder. All I've got is the pre-installed default program set for Ubuntu.

Is this normal ?

---

### Post by julian67 on 2007-09-30
Applications are not usually installed in your home folder. All those hidden .files are configuration files (your settings). 

It's not clear if you just restored only /home or your whole OS.  Or if you only backed up /home or if you backed up the whole OS but stored it in /home. Or if you had made an incremental backup of various parts of the OS and stored it in /home. 

If you make it clear what you backed up and how, and what you restored and how then it should be easy to answer any question you have.

---

### Post by philinux on 2007-09-30
ok my system crashed big style with loads of errors reported by fsck. So I backed up my home folder then completely reinstalled ubuntu. I had no other choice. Still need to check my hard drive as well. Not sure how to do that though.

---

### Post by julian67 on 2007-09-30
OK this means you only have the default Ubuntu application set installed now. Applications are almost always installed in /usr/bin/  or /usr/local/bin/    but in your /home folder you still have all the settings from your old install. This is very useful and will save you lots of time. But you do need to install your applications again. 1st make sure your fresh install is up to date by updating the repositories and running the updates checker. Then add any 3rd party repos you need and then install the applications you like. You'll find they see your old /home settings files and set themselves up just like before with everything remembered :-)

If you have enough spare disk space to back up your /home then it would be a great idea to back up the whole disk to an external drive for the future. There are some excellent free tools available for this. I like clonezilla-live for disk cloning....can save you from hardware/power failures and from yourself too :)

edit: the ubuntu installer should have checked your hard drives already, and they are routinely checked at boot as well. If you want to do it manually read the man page for fsck.

---

### Post by philinux on 2007-09-30
Cheers this is as I suspected. Breathing a sigh of relief just to get home folder back with settings as you say. Also plugins gone from firefox etc i suppose I'll have to sort this out too.

Hard disk is 250 gig so Iwas going to create a home partition as most people suggest but this means having to reinstall software again after a reinstall of ubuntu etc.

---

### Post by julian67 on 2007-09-30
> **philinux said:**
> Cheers this is as I suspected. Breathing a sigh of relief just to get home folder back with settings as you say. Also plugins gone from firefox etc i suppose I'll have to sort this out too.

Hard disk is 250 gig so Iwas going to create a home partition as most people suggest but this means having to reinstall software again after a reinstall of ubuntu etc.

Firefox plug-ins should still be there but when you made the new install and started firefox for the first time it will have created a new profile. If you copy your old firefox profile over your new one everything will be as before, bookmarks, extensions, history etc. 

A separate /home partition is very useful and doesn't mean any inconvenience, the opposite in fact. For example if you have a separate /home partition you can nuke your / partition and reinstall and not touch /home...all your personal data and settings are preserved. You can change distros or run several different distros sharing the one home folder. You can take it further and even have /usr on a separate partition and preserve your 3rd party/extra applications even when you format / and start again. This is something you should research though as there are drawbacks and dangers, the biggest of which would be underestimating the amount of space you need for /usr and filling the partition, rendering the OS unusable until you realised what happened and fix it.

edit: hopefully you won't need to re-install again if you stick to Ubuntu. the upgrade process seems much better than it used to be and if you have a decent back up regime then even a total hard drive failure doesn't require a re-install, just a disk to disk or image to disk clone.....but keep your backup disk outside of your PC ;-) and ideally in a different secure physical location.

---

