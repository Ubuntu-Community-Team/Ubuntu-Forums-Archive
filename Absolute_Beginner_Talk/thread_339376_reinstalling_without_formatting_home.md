---
title: "reinstalling without formatting /home"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by limitk7 on 2007-01-15
Hi,

I switched from Windows to Ubuntu 2 months ago and haven't looked back, wohoo!

Anyway, something got messed up, and I'd like to reinstall Ubuntu. I have a separate /home partition where all my documents and data are, and a separate / partition where the / stuff is. Could anyone tell me if it's possible, with the setup I have, to reformat and reinstall Ubuntu to the / partition, and leave the /home partition alone?

Thanks!

yes, i have backed everything up just in case.

---

### Post by aysiu on 2007-01-15
Select **Manually Edit the Partition Table**

This will take you to a visual layout of your partitions. Go to the step after that.

One the left, make sure all the mount points match up (/ and /home and swap). On the right, make sure the box (to reformat the drive) next to the /home partition is *unchecked*.

---

### Post by limitk7 on 2007-01-15
Thanks for the reply!

A couple more questions:

What will happen to all the hidden program/system/whatever folders on the /home partition when I do that (those folders that were created automatically when I first installed Ubuntu)? Will the new install overwrite them, or will they just remain as extra data that I can delete? Is there any possibility for conflicts?

And will the above process work also if I want to reinstall with xubuntu instead of ubuntu?

Thanks again.

---

### Post by aysiu on 2007-01-15
If you follow the instructions I gave you, **nothing** on your /home partition will be modified, deleted, or added to. It will remain exactly as it is now. If you have extraneous folders now, you'll have extraneous folders afterwards.

And, yes, as long as you're using the Desktop CD, the same process will work for Xubuntu, Ubuntu, and Kubuntu.

---

### Post by limitk7 on 2007-01-15
okay. Thanks a lot for your help.

---

