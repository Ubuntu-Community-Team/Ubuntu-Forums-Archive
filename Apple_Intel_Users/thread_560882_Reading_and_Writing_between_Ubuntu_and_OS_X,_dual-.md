---
title: "Reading and Writing between Ubuntu and OS X, dual-boot setup"
date: 2007-09-26
forum: Apple Intel Users
---

### Post by dmber on 2007-09-26
What's the easiest way to set this up?  I would like to be able to just mount my OS X partition in Ubuntu and use the Pre-set folders that OS X sets up for me.  Mainly because OS X seems to get ornery when I try to use different defaults.  It's just easy to use Documents for all my docs and whatnot.  

My problem is that I can mount my OS X partition in Ubuntu, but I get Read-only, only.  I can't write to the OS X partition.

Does anyone have a Dual-boot setup that works well for them?

Thanks.

---

### Post by cyberdork33 on 2007-09-27
> **dmber said:**
> What's the easiest way to set this up?  I would like to be able to just mount my OS X partition in Ubuntu and use the Pre-set folders that OS X sets up for me.  Mainly because OS X seems to get ornery when I try to use different defaults.  It's just easy to use Documents for all my docs and whatnot.  

My problem is that I can mount my OS X partition in Ubuntu, but I get Read-only, only.  I can't write to the OS X partition.

Does anyone have a Dual-boot setup that works well for them?

You have two issues:
1. the HFS+ filesystem modules can only allow write access if journaling is disabled in OSX. See: [http://julipedia.blogspot.com/2007/04/how-to-disable-journaling-on-hfs-volume.html](http://julipedia.blogspot.com/2007/04/how-to-disable-journaling-on-hfs-volume.html)

2. HFS+ uses permissions management in the same way that linux does. Your linux user and OSX user are considered separate, and you do not have access to other user's files by default. You can either edit the permissions on your folders in OSX to allow access by other users, or you can attempt to edit your uid/gid to be the same in linux as OSX, and thus are considered the same user. See: [http://ubuntuforums.org/showthread.php?t=486483&highlight=shared+home+partition](http://ubuntuforums.org/showthread.php?t=486483&highlight=shared+home+partition)
Note, this is not a recommend solution (at least by myself) as you can create more problems than you are preventing, but it is possible to share a home partition if that is what your goal is.

---

### Post by dmber on 2007-09-27
i tried turning journaling off -- and was successful -- but that didn't work.  possibly because i hadn't done anything about #2.

I have changed all the permissions on the folders in OS Xto Read/Write, but that still hasn't given me write capabilities in Ubuntu.  Do I need to change the "owner"?  I've changed everything else to Read/Write in the bottom of the Get Info window on all the folders I want to access.

With journaling disabled on my OS X partition and each of the folders I want to access set to Read/Write for all choices, I was still unable to write.  

My OS X partition is formatted "Mac OS Extended (Journaled)" (because I turned journaling back on after it didn't work to turn it off.)  Is Mac Os Extended the same as HFS+?

Thanks for the help.

---

### Post by cyberdork33 on 2007-09-27
> **dmber said:**
> i tried turning journaling off -- and was successful -- but that didn't work.  possibly because i hadn't done anything about #2.

I have changed all the permissions on the folders in OS Xto Read/Write, but that still hasn't given me write capabilities in Ubuntu.  Do I need to change the "owner"?  I've changed everything else to Read/Write in the bottom of the Get Info window on all the folders I want to access.

With journaling disabled on my OS X partition and each of the folders I want to access set to Read/Write for all choices, I was still unable to write.  

My OS X partition is formatted "Mac OS Extended (Journaled)" (because I turned journaling back on after it didn't work to turn it off.)  Is Mac Os Extended the same as HFS+?

Thanks for the help.
Sometimes you have to use the command to enable journaling then disable it again otherwise it won't work (although it will say it did.) The way to test if permission are the problem, try copying a file as root. root overrides the privileges set in the folders. If you set the others group to read/write then you shouldn't have a problem.

---

### Post by dmber on 2007-09-27
Would you mind walking me through doing things (such as copying a file) as root?  I hear "as root" pretty frequently and i'm not sure how to do it in the GUI.  I assume sudo is the same as root...correct?

thanks.

---

### Post by cyberdork33 on 2007-09-27
> **dmber said:**
> Would you mind walking me through doing things (such as copying a file) as root?  I hear "as root" pretty frequently and i'm not sure how to do it in the GUI.  I assume sudo is the same as root...correct?yes, Ubuntu is different from most linux distros as you do not setup the root account yourself. Root is THE linux admin. Root can do anything. su means superuser. su, by itself, is the command you use to switch to root, but you do not know the root password. If you want to only be root for one command, you use ```
sudo command
``` (if you have permission to use it, which you do in ubuntu).

so, to do something as root, you simply prefix it with sudo. For example, I have a text file on my desktop that I want to copy to the root home folder (/root). I cannot normally do that, because my user does not have permission to write to the /root folder. So...
```
sudo cp /home/cyberdork33/Desktop/testfile.txt /root/testfile.txt
```There is also a trick you can use to become root user and even set the root password. Try ```
sudo su
``` Then you can use the passwd command to set the password.

---

