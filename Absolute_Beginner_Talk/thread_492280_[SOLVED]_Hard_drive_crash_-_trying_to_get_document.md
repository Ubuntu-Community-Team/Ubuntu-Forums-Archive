---
title: "[SOLVED] Hard drive crash - trying to get documents back"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by mactece on 2007-07-04
The fan cooling my chip gave up and in the resulting overheat my hard drive got muddled. The good news is that if I boot up with the Ubuntu live cd I can see the drives. Most of my data is backed up but I'd still like to get back the last week or so. 

The problem: how do I use the live distro to get to the data? everything is coming up as read only. I need to get data off the linux partition and the windows partition and my backup drive is NTFS (I back up to an external hard drive). 

Many thanks

David

---

### Post by nitro_n2o on 2007-07-04
did you try to log in as root? or use sudo <command> while copying or accessing files?

---

### Post by mactece on 2007-07-04
That's part of the problem - 've only been using Ubuntu for a few weeks so I need some help with the commands.

I tried logging in as root but couldn't. I don't know if this is even possible from the live cd.

I used sudo su in a terminal and it showed me as a root user but then I don't know the commands to do what I want to.

So I'm hoping someone can talk me through it.

---

### Post by forestpixie on 2007-07-04
try gksudo nautilus - might give you enough access - don't panic about the error message you might get in terminal - it's a bug apparently

---

### Post by mactece on 2007-07-09
Thanks for your help. I tried what I could but just didn't have the experience. PClinux seems to be a better proposition for this kind of thing but that wouldn't work either (blast). In the end I installed Ubuntu on a spare hard drive and transferred the files that way. Now that I owned the installation it would let me mount the drive and copy. Previously I had been trying to copy to the same drive and it wouldn't let me sot out the permissions. 

Now I've hit a problem with Ubuntu - seems there is a bug recognising PS2 keyboards and its affecting me - so I've resued my data but now I can't get to it! So I think the simplest solution is a keyboard update.

Best regards

David

---

### Post by mactece on 2007-10-10
This thread ends here.

To find out more about the keyboard problem, follow this link

[URL="http://ubuntuforums.org/showthread.php?t=496676"]

---

