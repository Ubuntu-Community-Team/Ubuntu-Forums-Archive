---
title: "What's the correct way for removing the invisible system folders?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-08-10
I just deleted my /(root) folder and re-installed my Ubuntu.  When I browse to my /home folder I can see that there are traces of 3rd party programs from before I deleted /(root).
What's the correct way for removing these invisible system folders?

Like I still have what seems to be system files for Automatix
.automatix

Do I just delete the folders I don't want manually if so.  How do I know which .invisible folders I can and cannot touch?

---

### Post by reacocard on 2007-08-10
> **jingo811 said:**
> I just deleted my /(root) folder and re-installed my Ubuntu.  When I browse to my /home folder I can see that there are traces of 3rd party programs from before I deleted /(root).
What's the correct way for removing these invisible system folders?

Like I still have what seems to be system files for Automatix
.automatix

Do I just delete the folders I don't want manually if so.  How do I know which .invisible folders I can and cannot touch?

You can just delete them. All these hidden folders contain are your personal settings, so at worst you'll just have to redo your settings if you delete something wrong. A good idea is to make a new folder and simple move all the ones you think you don't need in there, then if anything goes wrong you just move the folder(s) back.

---

### Post by bodhi.zazen on 2007-08-10
> **jingo811 said:**
> I just deleted my /(root) folder and re-installed my Ubuntu.  When I browse to my /home folder I can see that there are traces of 3rd party programs from before I deleted /(root).
What's the correct way for removing these invisible system folders?

Like I still have what seems to be system files for Automatix
.automatix

Do I just delete the folders I don't want manually if so.  How do I know which .invisible folders I can and cannot touch?

You can either make a new user or delete unwanted .directories, like .automatix for example can be deleted.

---

### Post by Hospadar on 2007-08-10
Also in the future, if you are trying to totally clean your hard drive, you would get the best results by formatting the entire drive during installation.  This will completely remove all data from the drive so you get a fresh install with none of those extras.

---

### Post by jingo811 on 2007-08-10
Is there a list one can compare to just to make sure I'm not deleting something that Ubuntu really needs?  Like these seems important.

.aptitude
.config
.gconf
.update-notifier

---

### Post by reacocard on 2007-08-10
> **jingo811 said:**
> Is there a list one can compare to just to make sure I'm not deleting something that Ubuntu really needs?  Like these seems important.

.aptitude
.config
.gconf
.update-notifier

None of them are absolutely necessary. If you delete something needed, Ubuntu will regenerate it from the defaults. These are only YOUR settings, system settings are stored safely in /etc.

---

### Post by psusi on 2007-08-10
If you did a sudo rm -fr /, then you deleted EVERYTHING that was mounted at the time.  So unless you have a separate /home partition that was not mounted at the time, the files you see there are new.

---

### Post by happysmileman on 2007-08-10
A simple rule, which applies most of the time... If you can delete it without entering your password, it won't harm Ubuntu in any way, though may delete your settings.

If you need a password to delete something think about it first

---

