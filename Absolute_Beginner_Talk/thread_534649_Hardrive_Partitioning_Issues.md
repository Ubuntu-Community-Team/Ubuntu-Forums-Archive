---
title: "Hardrive Partitioning Issues"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Controlpanel on 2007-08-25
I'm not sure whats wrong with my hard drive. I started out with a 60 GB hard drive and partitioned Ubuntu to 20 GB. On Windows now I only have a 20 GB hard drive as well. What happened to the other 20 GB?

---

### Post by Majorix on 2007-08-25
You could have a look around with GParted LiveCD and see for yourself where it is.

---

### Post by Controlpanel on 2007-08-25
> **Majorix said:**
> You could have a look around with GParted LiveCD and see for yourself where it is.

Whats that? Is that on the Ubuntu live CD?

---

### Post by Majorix on 2007-08-25
No its a different CD. Give me a sec I will find the link and edit this post.

EDIT: Ok here is the link:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Controlpanel on 2007-08-25
How do I use it? Do I just burn it and then load it onto Ubuntu and use it?

---

### Post by Majorix on 2007-08-25
Just like you would use Ubuntu LiveCD, you burn it and boot from it. It won't write anything to your hdd or delete if you don't specify it to.

---

### Post by trak87 on 2007-08-25
The gparted program is listed in Synaptic for me. If the OP doesn't want the standalone distribution he can just install and run it from Ubuntu.

---

### Post by Controlpanel on 2007-08-25
> **trak87 said:**
> The gparted program is listed in Synaptic for me. If the OP doesn't want the standalone distribution he can just install and run it from Ubuntu.

I would get it off of Synaptic, but I can't connect to the internet on My Ubuntu boot.

---

### Post by armandh on 2007-08-25
if I were going to guess.........
most likely the missing 20GBs are unassigned

---

### Post by Controlpanel on 2007-08-25
So how would I fix this?

---

### Post by ajgreeny on 2007-08-25
As majorix said, get the gparted live CD, from your windows if needed, or get a friend to dl it for you, burn it as an image to a CD and boot from it.  You can then see exactly what your disk layout is and make the changes you want to.  If you need more detail, come back and ask again.

---

### Post by Controlpanel on 2007-08-25
> **ajgreeny said:**
> As majorix said, get the gparted live CD, from your windows if needed, or get a friend to dl it for you, burn it as an image to a CD and boot from it.  You can then see exactly what your disk layout is and make the changes you want to.  If you need more detail, come back and ask again.

I'm not sure how to use this program?

---

### Post by Controlpanel on 2007-08-25
Can someone tell me how to fix this?

---

### Post by ajgreeny on 2007-08-26
Boot into gparted live CD and look for any unallocated space.  If there is some you can enlarge your windows or ubuntu partition by using the Resize/Move icon in the taskbar.
Send us a screenshot of the gparted screen if you think it would help before you make any changes.

---

