---
title: "Windows 7, is there a good way to migrate all user data to a partion other than C:?"
date: 2012-11-02
forum: Any Other OS
---

### Post by jerome1232 on 2012-11-02
I just got a new 3 TB hard disk drive. Right now I share files with Windows by symlinking individual folders in Ubuntu to equivalent places in my Windows users folders.

This older disk is very, very full and I'd like to migrate everything under the Windows 7 Users folder, to the new disk, similar to moving /home on Ubuntu, and updating the symlinks in Ubuntu.

Is there an elegant way to do this? My goggling has turned up people suggesting to simply move the folders and add the new locations to their libraries.

---

### Post by Gone fishing on 2012-11-02
Its a Windows question but...

Yues you can create an ntfs partition copy all the user information to that drive and the change the location in Windows this looks about right  [http://www.starkeith.net/coredump/2009/05/18/how-to-move-your-windows-user-profile-to-another-drive/](http://www.starkeith.net/coredump/2009/05/18/how-to-move-your-windows-user-profile-to-another-drive/).

Then you can simlink into it from Ubuntu etc

---

### Post by jerome1232 on 2012-11-02
Which is why I posted it in other os/distro talk :D


The junction idea looks good, I didn't realize NTFS had that capability, much like a symlink actually. I'll give that a go, it looks like it's the most "transparent" straight forward method.

---

### Post by jerome1232 on 2012-11-03
Well I tried it and it simply isn't working for me, I'm not sure why. I'm going to have a go at this guide which tells you how to do it during the installation process.

[http://www.sevenforums.com/tutorials/124198-user-profiles-create-move-during-windows-7-installation-3.html#post1159551](http://www.sevenforums.com/tutorials/124198-user-profiles-create-move-during-windows-7-installation-3.html#post1159551)

Here we go again, working with MS-DOS commands was a real crash course on dos commands, I kept typing ls and wondering why it didn't work :D

---

### Post by jerome1232 on 2012-11-03
The last method seems to have worked well, something that's so simple to do in Ubuntu, way complicated to do in Windows. *grumble*

I had issues even getting my users profile to copy due to permissions issues (apparently an admin can be locked out of users folders) I wonder if the first method only failed because my copy of my profile was perhaps not perfectly in tact.

---

### Post by pqwoerituytrueiwoq on 2012-11-03
> **jerome1232 said:**
> The junction idea looks good, I didn't realize NTFS had that capability, much like a symlink actually. I'll give that a go, it looks like it's the most "transparent" straight forward method.
as of vista windows does have symlinks, but i don't think you can link to files

---

