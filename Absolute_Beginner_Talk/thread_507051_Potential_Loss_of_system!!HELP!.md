---
title: "Potential Loss of system!!HELP!"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by iamiso on 2007-07-22
Hi There, 

Been using ubunntu for a while with no bother. Then today somethuing really weird happened. 

It paused loading up (at orange bar) and then went into text mode. It then said the following: 

/dev/ hda contains a file system with errors. Check forced. 

Check occurs and then other error messages come up. Such as: 

Duplicate or bad block in use

Multiple clamied blocks node 7

Then other stuff. Then it says FSCK should be performed in maintenance mode. Asks for Root password which is the given and it thens claims "apt-get install" isn't installed. And that a manual FSCK should be run by pressing enter or something. This then fails........at this point I am UTTERLY lost!! What can I do? I'm using a live CD to post this......

Any help much appreciated.

---

### Post by meatpan on 2007-07-22
After fsck fails are you at a command line?  If so, can you try 'sudo fsck' and see if the problem persists?

I'm not surprised apt-get insall was not in the root path.  Keeping the root path to a minimum helps for damage prevention if a system is compromised, and more importantly, can keep the root user from accidentally running something disastrous.  This doesn't really answer your question, but hopefully helps you understand why you encountered a 'program not found' error when attempting to run as root.

---

### Post by iamiso on 2007-07-22
Thanks for the response. I think I'm at a command line! I'll have to try it again. 

Is there anything I can do from the Live CD that might correct this problem?

---

### Post by iamiso on 2007-07-22
just a quick bump in case anyone has any ideas!

---

### Post by iamiso on 2007-07-23
And again! Am I right in perhaps thinking this is going to have to be a complete reinstall? Darn!

---

### Post by xstevex on 2007-07-23
ive had this problem about 3 times. running FSCK in the command line interface, then saying Y to all of the questions will fix it.

---

### Post by iamiso on 2007-07-23
I'll try that again because as I remember (from a while back) there were an awful lots of Y's to answer - I mean hundreds! Is this right? 

Anyone know hat causes the problem?

---

### Post by autocrosser on 2007-07-23
How new is your hardware? Errors are the first sign of a incoming failure....

---

