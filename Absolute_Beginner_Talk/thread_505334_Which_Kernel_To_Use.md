---
title: "Which Kernel To Use?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by bme on 2007-07-20
I have upgraded my ubuntu to the latest kernel.I still can boot to the original kernel(2.6.20-15-generic).....I would like to know the ff:

1. which should I boot to as a default?what is the advantage?
2. what about device drivers,are they udgraded to the new kernel by default?

---

### Post by misfitpierce on 2007-07-20
New kernel if you have compiled it and everything still works a-ok. The new kernel was just released with more wireless support and better memory management so it sounds to be better.

---

### Post by bme on 2007-07-20
No I did not compile it. I just was upgraded by applying the available update thru synaptic...

---

### Post by AlexenderReez on 2007-07-20
of course the latest is better...and i suggest you to remove old kernel if new kernel running great:)

---

### Post by Seisen on 2007-07-20
Use the new kernel but keep at least one old kernel in case you have problems.

---

### Post by AlexenderReez on 2007-07-20
> **Seisen said:**
> Use the new kernel but keep at least one old kernel in case you have problems.

there is always backup kernel in /boot/ folder,so it is better just remove it.......kernel takes a quite a lot of space ...you can use it for other thing like software....

:)

---

### Post by eentonig on 2007-07-20
That only becomes an issue when you're short on diskspace. As long as I have plenty of space available, I tend to keep at least two, possibly three 'historical' kernels.

I don't use my all my apps regularly. And this way, if I ever found out that one of my rarely used apps doesn't work anymore, I can quickly check if it's kernel related.

Plus, it gives me an easy fix if I ever come to run out of diskspace.

---

### Post by Allycat on 2007-07-20
I have the same option during boot... I can boot in the current or the former kernel. I would like to delete the older version of the kernel, but how do I do that? Is there a smart way or is it just a matter of going to the boot folder and find the specific file(s)? And is it even possible for a complete Linux-novice like me to identify the kernel files?

Kind regards

---

### Post by AlexenderReez on 2007-07-20
> **eentonig said:**
> That only becomes an issue when you're short on diskspace. As long as I have plenty of space available, I tend to keep at least two, possibly three 'historical' kernels.

I don't use my all my apps regularly. And this way, if I ever found out that one of my rarely used apps doesn't work anymore, I can quickly check if it's kernel related.

Plus, it gives me an easy fix if I ever come to run out of diskspace.

> **Allycat said:**
> I have the same option during boot... I can boot in the current or the former kernel. I would like to delete the older version of the kernel, but how do I do that? Is there a smart way or is it just a matter of going to the boot folder and find the specific file(s)? And is it even possible for a complete Linux-novice like me to identify the kernel files?

Kind regards

i prefer to have clean grub ..which contain 3 bootable line -->ubuntu.recovery mode ,and vista....my space is not really big for average user..but 300g for me it is already enough ..even i have quite big space..it doesn't mean i need to waste it...like music,i prefer ogg instead of mp3...and i prefer to convert mp3 to ogg....

to remove old kernel,boot in latest kernel just search in synaptic 'kernel image '..then see
the version..remove older version

:)

---

### Post by Seisen on 2007-07-20
You also have to remember that a some of the people are newbs so we recommend that they keep it on their so it makes it easier for them when they have problems.

---

