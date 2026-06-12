---
title: "[SOLVED] Creating a shared folder with Windows XP"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-08-05
My wife and I have two computers connected in a network.  She uses XP, and I've just migrated to Feisty Fawn.  

When we were both using XP I created a couple of shared folders so that she could get access to some stuff on my computer and vice versa for me.  Now I would like to do the same thing between my Feisty and her XP, if you understand my drift.  I've used Samba (I think) to create a "shared folder" in my home directory.  Unfortunately the help texts are too abbreviated for me understand what I need to do next.

I figure that next I have to:

1) give her permission to access the folder, and 

2) tell XP how to find the folder on my computer under Feisty.

But I can't quite figure out how to do that.

For what it's worth, by the way, I can access the shared folders we have installed in XP via Feisty (I have a dual-boot).  However, when I oppen the folders they are devoid of content, with the exception of two files: Desktop.ini, and target.lnk.

Can anyone out there give us a hand with this?

---

### Post by aysiu on 2007-08-05
Watch this video:
[How-to: File sharing with Ubuntu using Samba](http://www.youtube.com/watch?v=Ad17kma8rNM)

---

### Post by Mr. Svinlesha on 2007-08-05
Thank you, aysiu!

---

### Post by Mr. Svinlesha on 2007-08-05
**aysiu**:

Just a quick shout-out to let you know that I did it, and it worked just fine!

Once again, thanks muchly!

---

### Post by aysiu on 2007-08-05
That's great!

---

### Post by cetheriel on 2007-08-12
i tried doing the same.
but when (following video tutorial) i come to check whether i can see the XP´s shared folders on the network, my network doesn't show up (only mshome does, yet it doesn't display anything in it).
what might be wrong?
also, my pcs (ubuntu and XP) are connected through an ethernet cable (no router/hub inbetween).

---

### Post by xpod on 2007-08-12
> i tried doing the same.
but when (following video tutorial) i come to check whether i can see the XP´s shared folders on the network, my network doesn't show up (only mshome does, yet it doesn't display anything in it).
what might be wrong?
also, my pcs (ubuntu and XP) are connected through an ethernet cable (no router/hub inbetween).

I think you possibly need a crossover cable for connecting pc`s like so rather than just a straight ethernet one.Thats what i have to use without a router anyway.....

---

### Post by Mr. Svinlesha on 2007-08-12
Sorry, **ceth**: it worked for me, but I completely new at all of this and doubt I can be of much help.  

I will mention one glitch I ran into, though.  During one step of this process you are required to to go into a file with gedit and "uncomment" a couple of lines.  You also have to change the word after the "=" sign from "no" to "yes."  During my first attempt at this I missed that step, so that after uncommenting the line "browseable=no" I forgot to switch to yes.  So I still couldn't browse the folder from my windows computer after having completed all the steps.  Luckily I figured out the problem after going back over everything a second time, step by step.

Still, doesn't sound much like your problem.  Sorry I can't be more helpful.  The only thing I can recommend is starting over from scratch and making sure you haven't missed a step in the process.

Good luck.

---

