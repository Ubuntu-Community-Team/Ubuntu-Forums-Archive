---
title: "Dual Booting MacOSX and Ubuntu, Sharing file partition"
date: 2009-05-14
forum: Apple Hardware Users
---

### Post by arsnic265 on 2009-05-14
Ok, so before installing Ubuntu on my macbook pro i ran it under vmware fusion to get used to the new OS first. So I messed with it learning the basics and finally made the switch not long after 9.04 was released. I have for about a couple of weeks been running both, happily.

When installing I partitioned my 200gig drive to three parts, first hfsplus(Journalled) for the Mac OSX partition, then the second partion now housing my Ubuntu OS. Each of these were 40 gigs, to allow room for programs and such. But for the rest of the 120gigs i wanted a partition to hold my music, picture, downloads, and such. I formatted it hfsplus(No Journalling). I figured that would make it easy for the Mac OS partition, knowing of course that Ubuntu would be able to read and write to the partition without problem.

This is where i need help. The partition has been set up for weeks and ran fine but now when i boot up linux for previously running mac my partition will allow me to use it then will suddenly switch to readonly. I've tried forcing the partion to unmount and remount to rw but when looking under the media the folder permissions for "My Files", my partition sharing the data, shows drwxrwxrwx, so i don't understand the problem. A friend of mine looked at it, he has used ubuntu for many years, and if we look at a files permissions the was made in OS X the file is marked for groups 501 dialout. dialout is 20. I need a way to sync up the accounts across OS's so that my group 1000 1000, which is me under ubuntu, matches the account permissions on Mac OS which seems to be for  some reason 501 20.

Any help would render me very greatful. Thanks in advance.

---

### Post by bruce_g on 2009-07-03
The easiest way to read files into Ubuntu from your HFS+ partition is to do so as root.  You will bypass the permissions issues.

The next easiest way is to create a new user with UID=501 (the default Mac user) and use that to copy files.

If you're still hungry for punishment, try the following threads:

These two go together and they're really the grandddaddies of a lot more:
[http://ubuntuforums.org/showthread.php?t=486646](http://ubuntuforums.org/showthread.php?t=486646)
[http://ubuntuforums.org/showthread.php?p=1922676](http://ubuntuforums.org/showthread.php?p=1922676)

After that, try searching the forums for "OSX" and "UID".  You might want to add "hfs" to the search, too.

Enjoy!  Look for my next post sometime around 2011.

---

