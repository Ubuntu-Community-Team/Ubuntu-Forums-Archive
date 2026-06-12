---
title: "System Crash--Help with Recovering Files/Permissions"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by wkck on 2008-03-31
Hello!  I scoured the forums, and I think this is a new issue.  Probably really easy for you guys to help with!

Background story:  I'm running 7.10.  Today when I restarted my computer I noticed something odd when it was shutting down (namely a number 6 and a couple of those symbols for women--you know the mirror thingy).  Thought that was strange... then my computer wouldn't start up again.  I've never seen the log in screen again.  So if you have a fix for that, great, but I can always install the operating system again.

So I panicked and freaked out--all my files gone?  But then realized I could run the live CD and get to my files.  So I'm running the live CD, searched for my documents and found them.  Under my "cat" home file.  "cat" is my username... and I also know my password... but not what my username and password is on the live CD 

Here is my problem:  I'm trying to copy them over to my external hard drive, but can't because "The folder contents could not be displayed," because I don't have "permission."  When I go into properties, I cannot change the permissions settings either, it says "You are not the owner, so you can't change these permissions."

So, how can I get permission to copy over my files to back them up?

Thanks in advance!  You guys are awesome.  :KS
Cat

---

### Post by kane77 on 2008-03-31
> **wkck said:**
> Hello!  I scoured the forums, and I think this is a new issue.  Probably really easy for you guys to help with!

Background story:  I'm running 7.10.  Today when I restarted my computer I noticed something odd when it was shutting down (namely a number 6 and a couple of those symbols for women--you know the mirror thingy).  Thought that was strange... then my computer wouldn't start up again.  I've never seen the log in screen again.  So if you have a fix for that, great, but I can always install the operating system again.

So I panicked and freaked out--all my files gone?  But then realized I could run the live CD and get to my files.  So I'm running the live CD, searched for my documents and found them.  Under my "cat" home file.  "cat" is my username... and I also know my password... but not what my username and password is on the live CD 

Here is my problem:  I'm trying to copy them over to my external hard drive, but can't because "The folder contents could not be displayed," because I don't have "permission."  When I go into properties, I cannot change the permissions settings either, it says "You are not the owner, so you can't change these permissions."

So, how can I get permission to copy over my files to back them up?

Thanks in advance!  You guys are awesome.  :KS
Cat
from terminal you can run ```
gksu nautilus
``` that should give you enough permissions to copy those files. anyway.. 

however I prefer to run something like 
```
sudo cp -a /path/to/source /path/to/destination
```
that will preserver all the user/group/permission information.. (replace the path/to/source/ and destination with actual paths)

---

