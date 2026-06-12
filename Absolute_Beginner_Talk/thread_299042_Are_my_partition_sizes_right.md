---
title: "Are my partition sizes right?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-13
For some reason, when I installed Ubuntu (Dapper) I was pretty sure that (being the noobie I am) I accidentally assigned most of my hard drive space to my swap. Well I got GParted downloaded and it's showing me this:


****
/dev/hda1      ext3     Size-17.94 GB    Used-4.93 GB      Unused-13.02 GB

/dev/hda2      extended   Size-705.99 MB   ---                ---

/dev/hda5      linux-swap  Size-705.96 MB


Does that look right to you? I could have sworn that in the beginning I had done something wrong but nothing looks wrong here.

---

### Post by taurus on 2006-11-13
Looks about right to me since you have 705.99MB for extended partition and all of it is assigned to swap...

---

### Post by dwblas on 2006-11-13
I think Ubuntu would have given you an error message if you didn't have enough space to install so you are fine.  If you run out of space at some future time you can always move /home or some other dir to a different partition and change /etc/fstab to mount it, but ~18 gigs should last a long time.

---

