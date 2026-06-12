---
title: "Two optical drives listed, only one installed"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by kpel on 2007-04-26
I'm sure there's an answer somewhere for this one, but I haven't been able to find it in my searching.


When I installed Ubuntu I had two optical drives; a CD-RW and a DVD-ROM on the PATA port.  My CD-RW drive dropped dead a few days ago so I picked up a combo drive, pulled out the two original drives, and installed the combo drive on an extra SATA port.  Ubuntu and Windows XP both picked up the changes without a problem and the new drive works fine with all types of media in both OSes.  The problem is that Ubuntu is still listing a CD-ROM drive when I go to Places>Computer.  Is there an easy command to get Ubuntu to update the drive listing, or do I have to edit a file somewhere?  I'm not opposed to either, I just don't know how to do it.

---

### Post by wormser on 2007-04-26
I am not 100% sure on this but you might have to edit /etc/fstab.

---

### Post by kpel on 2007-04-26
> I am not 100% sure on this but you might have to edit /etc/fstab.


Thanks, I couldn't remember the name of the file to edit.  That looks like it did the trick.

---

