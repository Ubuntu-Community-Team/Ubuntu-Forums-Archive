---
title: "Reformatting windows partition"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by josesanders on 2007-05-14
I'm finally ready to delete my Windows partition, so I have a really stupid question.  How do I do this?  I just want to reformat it as a linux partition.

---

### Post by oilchangeguy on 2007-05-14
if you've already installed ubuntu just use gparted from the live cd. or if it's not installed just allow ubuntu to use the entire drive.

---

### Post by laidback on 2007-05-14
Gparted is excellent, a good route to follow.

---

### Post by pikul on 2007-05-14
Your windows installation was on your first partition (hda1), and you want to add that space to your main linux (hda2), thats your case?

---

### Post by josesanders on 2007-05-14
Ok, so I used GParted.  I reformatted the Windows partition, but now it is just gone completely.  How do I mount the new partition?

---

### Post by josesanders on 2007-05-14
Solved by this thread:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Thanks for the gparted suggestion.

---

### Post by timgrin on 2007-10-08
> **pikul said:**
> Your windows installation was on your first partition (hda1), and you want to add that space to your main linux (hda2), thats your case?

This is what I would like to do - will I have a problem with GRUB as my bootloader? etc.

---

### Post by josesanders on 2007-10-09
I didn't have any trouble with GRUB.

---

### Post by tech9 on 2007-10-09
> **josesanders said:**
> I'm finally ready to delete my Windows partition, so I have a really stupid question.  How do I do this?  I just want to reformat it as a linux partition.


Just use liveCD to install ubuntu and then when you get to resizing your partition window,

choose manual and make sure that you check the format checkbox

---

