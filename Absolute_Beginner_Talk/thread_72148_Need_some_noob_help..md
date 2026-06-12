---
title: "Need some noob help."
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by PisShivers on 2005-10-05
I need some help here.
I've used Ubuntu for a little while now and I really like it, the other day my HD crashed and GRUB along with it, I can't get into XP anymore.
I reckon I have to reinstall Ubuntu to get this sorted again.

Here's my question, I have a 250 Gig HD and a 80 Gig HD the 80 Gig HD contains windows.
I want to partitionate the 2.nd HD to a 50 Gig HD with Ubuntu and a 200Gig HD with other stuff in it.

When i choose partitionate in the Ubuntu install menu, which one of the partitions does Ubuntu come in? the first or 2.nd?

Thank you.

---

### Post by snowjunkie on 2005-10-05
Would you edit out the bad language please?

---

### Post by PisShivers on 2005-10-05
:Edited:

PS: Kinda Urgent

---

### Post by canadianwriterman on 2005-10-05
Bad language? I hope you are referring to "Windows XP" as the bad language and only in jest, as I see no bad language!

---

### Post by drgreborn on 2005-10-05
you can choose which partition goes into. When you go into the partitionor, set the 50gig as mounted "/" and the other as mount for your stuff. E.g "/media/Data" as I did on my PC. So when you boot into Ubuntu you'll have two hdd icons, One file system which is 50 gig and one Data which is the 200 gig. Hope this helps.

---

### Post by Muhammad on 2005-10-05
^He editted it.

...


The one you mount as "/", possibly the second one or "hd2". 

Use this command in the terminal:

```
sudo fdisk -l
```

EDIT: drgreborn beat me to it. XP

---

### Post by Goober on 2005-10-05
If you are partitioning in Ubuntu, then just use GParted.  That worked for me.  Not sure if it comes with Hoary, or if you need to get it using apt-get.

Or Synaptic, but I personally prefer the Command Line.

---

