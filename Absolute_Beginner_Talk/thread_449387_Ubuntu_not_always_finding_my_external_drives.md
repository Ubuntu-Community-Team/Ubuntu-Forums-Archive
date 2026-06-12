---
title: "Ubuntu not always finding my external drives"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by carusoswi on 2007-05-20
Why is it that I could mount/unmount a specific firewire drive by simply right clicking on its icon and selecting to mount or unmount it for a week.  Today, I am told that I do not have permission to unmount it.  I can use sudo pumount to unmount it if I know its proper designation (sdb1).

When I plug in another firewire drive, it is not recognized by Ubuntu.  Again, if I know what it is called, I can pmount it.  Where I cannot guess the proper name of the drive, my only option is to boot into XP and find it there - that defeats what I am trying to do.

Suggestions would be welcome.

Caruso

---

### Post by overdrank on 2007-05-20
> **carusoswi said:**
> Why is it that I could mount/unmount a specific firewire drive by simply right clicking on its icon and selecting to mount or unmount it for a week.  Today, I am told that I do not have permission to unmount it.  I can use sudo pumount to unmount it if I know its proper designation (sdb1).

When I plug in another firewire drive, it is not recognized by Ubuntu.  Again, if I know what it is called, I can pmount it.  Where I cannot guess the proper name of the drive, my only option is to boot into XP and find it there - that defeats what I am trying to do.

Suggestions would be welcome.

Caruso

Hi you can use the command *sudo fdisk -l*.:KS

---

### Post by carusoswi on 2007-05-20
Thanks, that command lists all my drives - I cannot mount sda1 for some reason.
It will mount in XP, not Ubuntu.  I don't get it.
caruso

---

### Post by overdrank on 2007-05-20
> **carusoswi said:**
> Thanks, that command lists all my drives - I cannot mount sda1 for some reason.
It will mount in XP, not Ubuntu.  I don't get it.
caruso

Maybe this link will help
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Good luck!:popcorn:

---

