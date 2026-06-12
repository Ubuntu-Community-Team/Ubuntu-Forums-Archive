---
title: "G3 iMac lock up problem"
date: 2005-09-12
forum: Apple PPC Users
---

### Post by RHTopics on 2005-09-12
My slot loading iMac (G3 350mhz) is having an occassional lock up problem with Ubuntu 5.04.  I installed Ubuntu on this computer last week and have downloaded/installed all the security patches for it.  I have not installed any additional software beyond the standard desktop install.

Here is what is happening:

On two occassions it occurred after using Firefox, with it disappearing unexpectantly.  After that no other applications could be started, yet the menus would still work.  Attempts to kill and restart the X window session using "Control", "alt", "delete" keys did not work.  Switching to another screen worked, for example using "Control", "alt", "f2" keys.  At this screen a login prompt is displayed, but entering an user id did nothing other than re-prompt for the login user id.

I could not determine any other way to break out of this situation other than to press the Reset button on the side of the computer.

After pressing the power button to restart the computer, it boots back up with no apparent problems.

Has anyone had this type of experience?

Other than this problem, Ubuntu works well on this computer.

---

### Post by Elijahg on 2005-09-16
Maybe it's overheating? Especially if it's unusually hot there right now... Slot loading iMacs don't have a fan, so they do get quite hot.

---

### Post by RHTopics on 2005-09-17
Elijahg,  thanks for the reply.

Overheating could be a possibility, but after the having problem again yesterday and the room temperature was less than 80'f, I think the problem is software related.

On other posts in this forum and in bugzilla, I have seen people having problems with the daemon "pbbuttonsd".  It is started on boot up with this iMac.  I am wondering if it could be source of the problem and is it required for an iMac or is only needed for Apple notebook type computers?

---

