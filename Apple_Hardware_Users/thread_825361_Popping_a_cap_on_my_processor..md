---
title: "Popping a cap on my processor."
date: 2008-06-10
forum: Apple Hardware Users
---

### Post by Alex&amp;Linux on 2008-06-10
Hey guys!
One of the few things that I hate about Ubuntu on my Macbook is that the battery lasts about 1 hour.

Looking at it from the point of view of thermodynamics, it looks like the thing consuming most of my battery's charge is the processor (other things seem negligible in comparison, except perhaps the HDD, but I don't know if there's a way to stop that from goin' 'round).

My 13" book had an Intel duo core running at 1.83 Ghz (if memory serves), and I only use the thing for light browsing and reading ebooks, so how about telling the processors to slow down to a few hundred megahertz, in a way that would allow me to reverse this in case of the use of more demanding applications.

Halp!

---

### Post by Bubba64 on 2008-06-10
> **Alex&Linux said:**
> Hey guys!
One of the few things that I hate about Ubuntu on my Macbook is that the battery lasts about 1 hour.

Looking at it from the point of view of thermodynamics, it looks like the thing consuming most of my battery's charge is the processor (other things seem negligible in comparison, except perhaps the HDD, but I don't know if there's a way to stop that from goin' 'round).

My 13" book had an Intel duo core running at 1.83 Ghz (if memory serves), and I only use the thing for light browsing and reading ebooks, so how about telling the processors to slow down to a few hundred megahertz, in a way that would allow me to reverse this in case of the use of more demanding applications.

Halp!

I am not sure why you would get such a short amount of battery time, but I have seen posts that suggest that the Ubuntu program may take a while to show correct battery usage although I haven't experienced this myself. How old is the battery, mine goes around 3-4 hrs. You can also change the power usage I do this with the 3rd party Ubuntu Tweak which has a bunch of easy access change possibilities.

---

### Post by Alex&amp;Linux on 2008-06-11
> **Bubba64 said:**
> I am not sure why you would get such a short amount of battery time, but I have seen posts that suggest that the Ubuntu program may take a while to show correct battery usage although I haven't experienced this myself. How old is the battery, mine goes around 3-4 hrs. You can also change the power usage I do this with the 3rd party Ubuntu Tweak which has a bunch of easy access change possibilities.
New battery 1 month ago, and with OS X, I get 3.5 hours of normal usage as of last week.

I've tried Ubuntu Tweak, and at most it affoarded me an extra 20 minutes.

My record of battery life under ubuntu is 2 hours, but I had to be very careful with what I was doing.

The governing powersaving feature of OS X which allowed such an above average life of battery charge was its dynamic processor scaling, so I should be able to do the same things here, or at the least impose a hard limit on the available frequency.

I really enjoy some things that Ubuntu brings to the table, but on mobile technology, the problems that are created exactly cancel the disadvantages created by closed OS's like OS X and Windows.  Ubuntu needs to catch up on this hardware business.

---

### Post by Bubba64 on 2008-06-11
> **Alex&Linux said:**
> New battery 1 month ago, and with OS X, I get 3.5 hours of normal usage as of last week.

I've tried Ubuntu Tweak, and at most it affoarded me an extra 20 minutes.

My record of battery life under ubuntu is 2 hours, but I had to be very careful with what I was doing.

The governing powersaving feature of OS X which allowed such an above average life of battery charge was its dynamic processor scaling, so I should be able to do the same things here, or at the least impose a hard limit on the available frequency.

I really enjoy some things that Ubuntu brings to the table, but on mobile technology, the problems that are created exactly cancel the disadvantages created by closed OS's like OS X and Windows.  Ubuntu needs to catch up on this hardware business.

It is bummer that your having this experience, I wonder though if the Ubuntu program isn't somehow miss reading the charged value. Since it is a brand new battery, have you tried letting the Ubuntu program run to a almost used state then running the other program to see if this might be the problem. I of course am assuming that your dual booting.

---

### Post by Alex&amp;Linux on 2008-06-11
I am not requesting help with the problem in general;  I specifically want to know how to cap my processors, because it IS the problem.

The power estimation by Ubuntu has absolutely nothing to do with this, because it doesn't matter what it says;  what matters is that Ubuntu eats up the battery in around an hour and a half, while OS X (performing the same tasks) will last 3 times longer --due to the way it's kernel handles processor scaling.

To emphasize:  THE PROBLEM CAN ONLY BE RESOLVED BY CHANGING THE WAY THAT UBUNTU USES
               PROCESSING, AND THE BEST WAY TO DO THIS IS TO CREATE A CAP;  SOME SORT
               OF RESTRICTION.

---

### Post by cyberdork33 on 2008-06-11
Your processor is just a normal Intel Core CPU, and processor scaling is supported by the kernel. This is not a Mac specific issue. CPU governance should be the same for you as any other PC using a Core CPU.

As for your Power Issues... There are quite a number of threads that have discussed power saving on the Mactel hardware. You might want to look into those. I am linking to a quite extensive one here:

[http://ubuntuforums.org/showthread.php?t=590867](http://ubuntuforums.org/showthread.php?t=590867)

---

### Post by Alex&amp;Linux on 2008-06-11
I'll give them a try, however, I am seeing several reports of these measures failing.
OS X still performs better on the Mac it seems.

Could you show me how to cap the processors please?

---

### Post by cyberdork33 on 2008-06-12
> **Alex&Linux said:**
> OS X still performs better on the Mac it seems.and it probably always will. That is the benefit of having full access to the hardware specs.

I have no idea how to cap the processor speed.
[http://www.google.com/search?q=Ubuntu+CPU+scaling](http://www.google.com/search?q=Ubuntu+CPU+scaling)

---

