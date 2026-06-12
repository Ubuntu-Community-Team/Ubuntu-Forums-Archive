---
title: "copy ubuntu installation"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2006-07-31
Hi,

The partitioning of my drives is poor to say the least is there anyway i could "clone" my install of ubuntu with all programs etc intact? 
I don't wont to lose any of the stuff I have right now but I would like to re-partition my drive to be a little more tidy

Thanks

---

### Post by s_h_a_d_o_w_s on 2006-07-31
I strarted a similar post yesterday: [here]("http://www.ubuntuforums.org/showthread.php?t=226140")

---

### Post by jd65pl on 2006-07-31
I don't necessaraly need to write it to a cd i would be able to copy everything to an external hard drive I have 300gb i dont use.

edit:
Could I copy everything from / upwards to my external hard drive then copy it back to my internal drive and have everything there?

---

### Post by aysiu on 2006-07-31
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by jd65pl on 2006-07-31
Thanks aysiu thats great :D

---

### Post by Frank Golden on 2006-07-31
> **jd65pl said:**
> Thanks aysiu thats great :D
Hi jd65pl, 
 Question do you have only Ubuntu on your machine?

---

### Post by jd65pl on 2006-08-01
I only have ubuntu now as my windows stopped working I want to delete its partition and increase my ubuntu partition but it is hda3 windows was on hda1 and hda2.

---

### Post by Frank Golden on 2006-08-01
> **jd65pl said:**
> I only have ubuntu now as my windows stopped working I want to delete its partition and increase my ubuntu partition but it is hda3 windows was on hda1 and hda2.
Just be careful with partimage if your original setup had
Ubuntu on hda3 then when you restore your image it needs to 
be on a partition hda3 in order for GRUB to find it. Or change GRUB.  What I had
to do with mine is use the install disc to reinstall Ubuntu
making sure it got installed to a partition hda3 then restore my image over that. I am sure there is a more elegant way to do it
or a way to point GRUB at the right partition. I just haven't
figured it out yet. The image will have GRUB info pointing to hda3.

---

