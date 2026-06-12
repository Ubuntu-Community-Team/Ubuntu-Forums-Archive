---
title: "Removing Programs"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Hexx on 2006-07-11
When I try to remove some programs (like Ekiga and Evolution) via the Add/Remove menu, I get error messages like this:

> One or more applications depend on 'ekiga'. To remove 'ekiga' and the dependent applications, please switch to the advanced software manager.

Does this mean I need to uninstall them via Synaptic, or the command line?

---

### Post by ironfistchamp on 2006-07-11
To my knowledge that means use Synaptic. I have never used Add/Remove programs at all. I always use Synaptic and mess around as root. I think I may be to careless.

Try it through Synaptic and see.

Ironfistchamp

---

### Post by Hexx on 2006-07-11
> **ironfistchamp said:**
> To my knowledge that means use Synaptic. I have never used Add/Remove programs at all. I always use Synaptic and mess around as root. I think I may be to careless.

Try it through Synaptic and see.

Ironfistchamp

You might be the man to ask this question then: When I attempt to uninstall certain programs via Synaptic, it asks if I want to uninstall ubuntu-desktop as well. Is this safe???

---

### Post by Brunellus on 2006-07-11
yes, you can safely uninstall ubuntu-desktop.

---

### Post by ironfistchamp on 2006-07-11
Hehe that sounds kind of odd. Do you get left with just the bottom of the desk? :p 

Seriously though what does it actually uninstall?

---

### Post by Hexx on 2006-07-11
> **ironfistchamp said:**
> Hehe that sounds kind of odd. Do you get left with just the bottom of the desk? :p 

Seriously though what does it actually uninstall?

This is all completely new to me, but I uninstalled Ekiga and Evolution via Terminal, and it uninstalled "ubuntu-desktop" along with both of them, and everything's fine. I'm assuming the "ubuntu-desktop" that's getting uninstalled along with these apps is somehow related to the programs themselves, and not directly related to Nautilus...?

---

### Post by ironfistchamp on 2006-07-11
I think I uninstalled it a while back thinking "what the hell I still have windows" (I was a Windows user back then). Didn't seem to do anything though.

---

### Post by Freiburg05 on 2006-11-08
I have upgraded Dapper to Edgy just now, and found the same problem. Anyway, ubuntu-desktop package does anything, seems to have only references to other packages. Looking in installed files, it only has a copyright and a changelog file. The only thing it does seems to be create those annoying dependecy messages. 


    Cheers.

---

### Post by TheRingmaster on 2006-11-08
ubuntu-desktop is just a dummy package. no real packages are actually taken out with it.

---

