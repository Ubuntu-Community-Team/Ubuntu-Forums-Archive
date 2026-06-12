---
title: "Partitions - Look Good?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by cmaksymchuk on 2007-03-10
I am new to linux and have just installed ubuntu.  Here's how I set up the partitions:

/boot - primary - 100mb
/ - primary 20 gb
swap - logical - twice my ram (1536mb) 
/user - logical - 20 gb
/home - logical 160 gb 

Does this seem like it would be a good setup for partitions?  I chose to make the last three logical vs primary due to the primary restriciton of 4.  Does it really matter if they are primary or logical? Why would you make one primay or logical or vice versa?

Thanks a lot for your help

C

---

### Post by K.Mandla on 2007-03-10
To the best of my knowledge there's no real advantage in logical over primary partitions, or vice-versa, except in situations like yours when you want more than the four allowed. I think primary partitions might mount faster, but I don't know where I heard that, or if the difference would be noticable at all.

You could probably cut back on swap space, but that's a matter of preference. I usually set mine equal my installed memory, but I very rarely run out of memory or start swapping to the hard drive. If you're anticipating a heavier workload, you might need more. 

Any reason you want 20Gb for /usr and root? You might be able to survive with ~2Gb for each. Again, that will differ if you're going to install a horde of applications.

---

### Post by cmaksymchuk on 2007-03-10
Swap space: I read that your swap should be 2Xram, but no biggie, I have a much bigger hd than i'll ever use.  Same reason for the 20gb root and usr.  Just I have a huge hard drive and didnt know what would be sufficient for each, so  figured 20gb... why not?  Question: could I resize them later if I decide I need the space?  How would I go about doing that?

---

### Post by cmaksymchuk on 2007-03-10
Another question, I was installing kubuntu desktop and pushed ctrl c and it klled the install.  WOuld that have partially installed the desktop, or not at all.  I tried apt-get remove kubuntu-desktop but it didnt seem to remove anything. Am I all good or did I mess things up.
Thanks again.

C

---

### Post by K.Mandla on 2007-03-10
I can't say definitively that it should be one or another; I used to use the 2X rule in Windows and it was almost a necessity. After I started using Linux and never touched the swap space, I began wondering how little I could get by with. I've shaved it to as little as 1/2 available memory, and still haven't had problems ... but again, I rarely use so much physical memory that swap comes into play.

I think if you use LVM you can resize drives later. Otherwise you'd probably have to resize them with something like GPartEd, and make sure nothing was damaged in the process. Not a tantalizing prospect to me. ... :shock:

---

### Post by K.Mandla on 2007-03-10
> **cmaksymchuk said:**
> Another question, I was installing kubuntu desktop and pushed ctrl c and it klled the install.  WOuld that have partially installed the desktop, or not at all.  I tried apt-get remove kubuntu-desktop but it didnt seem to remove anything. Am I all good or did I mess things up.
Thanks again.

C
It should be all right. You should be able to resume the installation later if you want.

---

### Post by cmaksymchuk on 2007-03-10
What is LVM? OK, just looked it up... linux volume manager. Not sure if I used it or not.   I partitioned using the ubuntu cd install.  Which ever partition manager that was... thats what I used.  Was it LVM? That ok?  How do I resize?  

Thanks again for your quick (and knowlegable) replies.

C

---

### Post by K.Mandla on 2007-03-11
I think you have to specifically opt for LVM during the installation to use it. I know the default does not use LVM. I'm afraid I can't be more helpful than that; I tried it once about a year ago and didn't think it was anything I would use. Search around. I'm sure there are some tutorials on the subject somewhere around here. ;)

---

### Post by enopepsoo on 2007-03-11
I looks pretty good to me.  separating things is certainly a good idea.

---

