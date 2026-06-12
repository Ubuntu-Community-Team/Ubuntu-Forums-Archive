---
title: "home network"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by ubunoobie on 2007-10-26
It seems that home networking is not that highly documented in the Ubuntu How-To's... anyway, the question is: what do I need to do in order to access my ubuntu desktop from another XP machine?

I can see the ubuntu desktop on my home network, but when I try to access it from my XP machine a dialog comes up asking for a username/password. I can also transfer files *from* my ubuntu desktop *to* my XP machine. But not vice versa.

What is this username/password? Where do I set it? And how?

Thank you!

---

### Post by Joeb454 on 2007-10-26
either a FAT partition, usually FAT32, or an NTFS partition.

Failing that do a google search for ext2 or ext3 drivers for windows

*EDIT*

Sorry misread the question, I'm tired :p, I don't know what the username and password it's asking for is. But I'm guessing that the last part would be helpful for copying to your XP machine while using that

---

### Post by woedend on 2007-10-26
you must make a new user for your ubuntu.  add a user, associate a password...may need to configure samba a little...but you've got it very close!

---

### Post by ubunoobie on 2007-10-26
> **woedend said:**
> you must make a new user for your ubuntu.  add a user, associate a password...may need to configure samba a little...but you've got it very close!

Hi, could you provide some instructions of what you're saying here? What do you mean by "make a new user for your ubuntu" ?

Thanks!

---

### Post by ubunoobie on 2007-10-27
bump

Anyone? I can't be the only person that has encountered this situation.

Perhaps this thread is in the wrong place? Maybe a moderator can come by and move it to the networking forum?

---

### Post by blackaardvark on 2007-10-27
Setting up a username in samba is explained here:

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

Hope that helps, it worked for me!

---

