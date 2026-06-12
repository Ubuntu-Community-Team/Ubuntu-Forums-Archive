---
title: "USB Drive slow"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by loupy on 2005-11-14
I have a USB 2.0 drive and doing copies from my USB drive to my notebook it goes at a rate between 20MB to 25MB per sec.  Copying from my notebook to the USB drive it only goes between .5MB to 1.5MB.  I know the notebook HD is only a 4200rpm as opposed to the 7200rpm of my USB drive, but should it be that slow?

I think I have the hdparm.conf configured properly to have DMA on and I am using LVM on my notebook.  Any help is appreciated!

---

### Post by loupy on 2005-11-15
Shameless bump.

Am I the only one having this issue???

---

### Post by Jussi Kukkonen on 2005-11-15
It's probably not a drive issue, but USB one...

25MB per sec sounds like it's in the right ballpark for USB 2.0 hard drives, but it should be about the same in both directions -- at least that's what I'm seeing with my LaCie...

---

### Post by loupy on 2005-11-15
Update:  I just did a reinstall and used regular partitions on my HD and not LVM and now I get 25MB both ways.  So I'll assume LVM was the culprit.

Thanks for the reply!

---

### Post by jdong on 2005-11-15
That's really weird. I'll play around a bit with LVM tonight and see if I can reproduce this... LVM is highly used in the high-performance enterprise environments, so it should be tested well enough that it won't cause problems like this... (then again, when has a 1TB network storage device ever needed the blessing of a USB drive? ;) )

---

### Post by loupy on 2005-11-15
Let me know how your testing goes.  I'd really like to go back to LVM, but since I'm on a notebook USB drives are more important to me.

---

### Post by jdong on 2005-11-15
Any reason why you want LVM so bad?

---

### Post by loupy on 2005-11-16
I like to test a bunch of different distro's and it's easier if I have LVM to create/resize partitions as needed instead of making numerous logical drives that are not as easily resized.

---

