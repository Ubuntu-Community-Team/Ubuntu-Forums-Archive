---
title: "please someone take a look at this and help if you can !!!!"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by jjasonj on 2007-09-04
hi there.my gf has been using ubuntu now for quite a while,and has no problems up until now..she has feisty fawn running,unlike me...ok the main problem she is having which i cant seem to find the answer,i solved it before,but cant find again,on the forum...on booting up after the thirty times..thing,it fails and what is on her screen is a load of stuff,including  /dev/hdal1..unexpected inconsistncy,
run fsck manually (i.e without a or p options)
fsck died with exit status 4...
and at the bottom it tells her that apt-get is not installed..to install type apt-get install apt!!! this does nothing whatsoever..all it says is bash:apt-get is not found !!! 
restarting pc gets all this yet again...she has had enough and after i persuaded her to try ubuntu,i need your help to solve this and what we can do to stop this happening everytime the check is forced..regards jason

---

### Post by mlentink on 2007-09-04
Maybe you can join forces with the OP of [this thread]("http://http://ubuntuforums.org/showthread.php?t=542679")?

---

### Post by skyjacker on 2007-09-04
try typing (in terminal) "sudo  apt-get install apt"

---

### Post by ukripper on 2007-09-04
> **jjasonj said:**
> hi there.my gf has been using ubuntu now for quite a while,and has no problems up until now..she has feisty fawn running,unlike me...ok the main problem she is having which i cant seem to find the answer,i solved it before,but cant find again,on the forum...on booting up after the thirty times..thing,it fails and what is on her screen is a load of stuff,including  /dev/hdal1..unexpected inconsistncy,
run fsck manually (i.e without a or p options)
fsck died with exit status 4...
and at the bottom it tells her that apt-get is not installed..to install type apt-get install apt!!! this does nothing whatsoever..all it says is bash:apt-get is not found !!! 
restarting pc gets all this yet again...she has had enough and after i persuaded her to try ubuntu,i need your help to solve this and what we can do to stop this happening everytime the check is forced..regards jason

you  should run fsck using live cd.

Boot from Live cd and then run fsck

---

### Post by jjasonj on 2007-09-04
thanks for your replies,the link on top suggestion is dead,and we have tried the second one...nothing....jason is meddling with it..so while i am here(the one with the broke pc,lol) let me know asap any more suggestiions

---

### Post by jjasonj on 2007-09-04
whatever was the problem....we have ran fsck without cd,and it came up with a blocked inode ...???terminal asked if we would like to delete it,and we pressed yes,rebooted system and this seens to have worked..anyone can tell us why this happens..and to prevent it keep happening everytime lisa has to do this 30 times check thing...!!! but atleast she has it for another 30 times before we stuck again,lol thanks for your replies guys..

---

### Post by ukripper on 2007-09-04
> **jjasonj said:**
> whatever was the problem....we have ran fsck without cd,and it came up with a blocked inode ...???terminal asked if we would like to delete it,and we pressed yes,rebooted system and this seens to have worked..anyone can tell us why this happens..and to prevent it keep happening everytime lisa has to do this 30 times check thing...!!! but atleast she has it for another 30 times before we stuck again,lol thanks for your replies guys..

Just a lil suggestion, you should never run fsck against filesystem it should be run from the LIVE CD. It can corrupt your filesystem for good if run on loaded filesystem and then only solution would be fresh install.

---

### Post by tact on 2007-09-04
the "30 times thing" is just running fsck like you did from the terminal.  So if you found and fixed something and the file system is all back in good order, then (provided no further file system damage happens between now and then) - your next "30 times thing" should go through without a hitch.

If you are getting repeated incidents of fsck finding file system problems at the 30 times check you need to find out why...  are you not shutting down properly every time?  It is VERY important to do controlled shutdowns with advanced file systems as used in linux.

Also...  you can manually run fsck yourself at any time before the 30 times thing...  and that resets the counter as well.  as ukripper mentions - do it while booted from another disk, like live CD

---

### Post by jjasonj on 2007-09-04
thanks for the advice..lisa just shuts everything down,back to desktop,and clicks on the door and selects shutdown..this right?

---

### Post by rmockler on 2007-09-04
Shutdown procedure looks perfect, at least it works for me !!
~Dick

---

### Post by bhold on 2007-09-05
Not sure if this is relevant to your problem, but I just worked through some similar boot problems a few days ago. .At the boot error message I was in a shell - I just typed exit and boot process continued successfully. My problem was caused by a bad uuid entry in /etc/fstab - not sure how that happened but after I corrected fstab the boot problems were fixed and have not returned. There was no need for me to run fsck even though I got a message to run it - I ignored the message. The message to use apt to install apt is bogus, I ignored it also.

---

### Post by tact on 2007-09-08
Yep it looks like you are shutting down properly.  That gets the basics out of the way  :)

Suggest you do as mentioned and boot from a boot CD and do the fsck checks on all partitions (allowing it to fix any problems.).   Repeat to be sure that problems were fixed.  Then just do your normal thing (proper shutdowns every time) and wait for the 30 reboots thing to roll around.  Let us know if you still got problem.

---

