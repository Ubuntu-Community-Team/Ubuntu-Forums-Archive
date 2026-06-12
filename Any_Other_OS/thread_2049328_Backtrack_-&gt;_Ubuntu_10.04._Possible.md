---
title: "Backtrack -&gt; Ubuntu 10.04. Possible?"
date: 2012-08-28
forum: Any Other OS
---

### Post by anashlali on 2012-08-28
Hi guys

I'm using backtrack 5 r3, I would like to upgrade to 10.04.1, is that possible? I don't want to do fresh install cause I don't want to loss the backtrack packges, is there any way to do this?

---

### Post by coffeecat on 2012-08-28
@anashlali, I've moved your post from where it was hijacking a Testimonial thread to its own thread and given it a suitable title. Please start your own threads.

---

### Post by MG&amp;TL on 2012-08-28
> **anashlali said:**
> Hi guys

I'm using backtrack 5 r3, I would like to upgrade to 10.04.1, is that possible? I don't want to do fresh install cause I don't want to loss the backtrack packges, is there any way to do this?

Probably...but if you need and use the utilities backtrack provides, could you not just install them on 10.04?

Simply changing your /etc/apt/sources.lst to reference ubuntu should be okay. Although back up your stuff first.

---

### Post by Trapper on 2012-08-28
This is what I found in the FAQ's at the Backtrack site:

> ** Why cant I just add the Backtrack repositories to my Ubuntu install or the Ubuntu repositories to my Backtrack install ?**

 We highly recommend against this action because Backtrack tools are  built with many custom features, libraries and kernel. We have no way of  knowing how they will perform on a non Backtrack distribution, plus you  will very quickly break your install.  
Also if you chose to add the ubuntu repositories to your  Backtrack install, you will most certainly break your entire Backtrack  install very quickly. 
We do a lot of testing to ensure that all packages in our repo will work together without causing problems. 
If you decide on this course of action you do so entirely at your  own risk and the backtrack team will not offer any support in any way. 


---

### Post by MG&amp;TL on 2012-08-28
> **Trapper said:**
> This is what I found in the FAQ's at the Backtrack site:

My bad then, apologies.

BackTrack is a very specialist distribution, what are you trying to achieve by moving to Ubuntu, OP?

---

