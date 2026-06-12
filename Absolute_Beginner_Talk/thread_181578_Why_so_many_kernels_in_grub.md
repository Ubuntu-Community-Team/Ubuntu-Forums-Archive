---
title: "Why so many kernels in grub?"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by learning on 2006-05-24
I have my systems set up well enough to the point I am probably just being whiney now, but...

When I boot up, grub shows my options as three different linux kernels, and at the bottom, windows. 

The top one is the latest kernel I use.  Why are the two old ones still there?  Can I get rid of them?  Doesn't really matter much, but just wondering if in time, I'll have 20 different kernels to click through.

---

### Post by aysiu on 2006-05-24
You can uninstall them using Synaptic, Adept, or apt-get.

Search for the phrase *linux-image*.

---

### Post by Omnios on 2006-05-24
From my experience when you install a new kernal it does not uninstall the older kernal probably to stop you from getting locked out if something goes wrong. I had this before and just uninstalled the older kernal and parts in synaptic and everything worked fine.

 Edit: somone beet me to it again lol.

---

### Post by chadk on 2006-05-24
aysiu strikes again!

-- Thanks, this question helped me as well. Just removed 3 old kernels.

---

### Post by learning on 2006-05-24
That got it!

Thank you!

---

