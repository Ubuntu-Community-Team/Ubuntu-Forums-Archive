---
title: "Changing partition name"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-02-24
Is there a way to change the default names of partitions to something more user friendly? hda1, hdc2 and the like are not particularly easy to  associate with a particular partition. I made a cheat sheet but would rather not have to use it. Can this be changed so the displayed name is easier to deal with? 

What about editing fstab from this: 
```
/dev/hda1 /media/hda1
```to something like this:```
/dev/hda1 /media/Calamity
```Would this work?

---

### Post by dbbolton on 2007-02-24
you would have to do 'sudo mkdir /media/Calamity' first

---

### Post by Patrick K on 2007-02-24
Man, that was quick!

But the idea is doable, right? Provided the new directory was created.

---

### Post by taurus on 2007-02-25
It's perfectly fine.

---

### Post by Patrick K on 2007-02-25
Cool, I'm going to do that. Thanks!!

---

### Post by Patrick K on 2007-02-25
I noticed, looking at the properties sheet of a partition in Nautilus, that the "name" field can be edited. What does this change? Any problems using this to change the display name of a partition?

---

### Post by dbbolton on 2007-02-25
i generally don't trust nautilus, for what it's worth.

---

### Post by Patrick K on 2007-02-25
Why is that? Are there any file browers you do trust? 

I've been poking around looking for a replacement. I used a file browser called PowerDesk as a replacement for Windows Explorer. A really big improvement. I wouldn't mind find one for Nautilus. I have XFE. I like the layout but it's kind of flaky.

---

