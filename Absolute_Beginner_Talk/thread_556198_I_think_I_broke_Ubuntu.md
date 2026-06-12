---
title: "I think I broke Ubuntu"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Arukas on 2007-09-21
Hello, 

  I am thinking I have broke Ubuntu, is there an easy way to reinstall everything like new?  


-Arukas


P.S.

What does the crtl-alt-backspace button doing, a quick log off?

---

### Post by wolfen69 on 2007-09-21
yes, ctrl-alt-backspace will log you out and reset X. you will have to be more specific about what is broken.

---

### Post by asmoore82 on 2007-09-21
> **Arukas said:**
> What does the crtl-alt-backspace button doing, a quick log off?

it **Kills** the X server; it is of subtle importance to note the difference between **Kills** and **restarts**
but in any event it poses no real threat to the health of X; but it also is a cascading effect
that kills all open graphical applications, you really wouldn't want to do it while
something like a package update or synaptic is running :D.

---

### Post by Arukas on 2007-09-21
I have type in enough random commands from guides on how to install stuff, that I think I may have screwed something up.  I have a game that use to work but now doesn't.  I was thinking about reinstalling everything on Ubuntu and start over.   I really don't know where everything goes, or the effects of the command i type in.  Something isn't right or my programs would work right.


-Arukas

---

### Post by phizikal on 2007-09-21
If you want to refresh your ubuntu, back everthing you want up and  just reinstall using your livecd.

You could also fix your problem by giving us details on what is wrong.

---

### Post by PreviousN on 2007-09-21
In short, no there isn't, from what I understand, a "quick reinstall". And the option in the grub menu (safe mode or something like that) is a safe kernel. 

If you think that a new reinstall will fix it, I suggest backingup your /home/ directory to something like a flash drive and then reinstalling it from the cd/dvd. This usually only takes like 30 minutes plus or minus 10 minutes. 

In the future, what I do, is put /home onto its own partition. So when you set up ubuntu and go to the partition manager go 'partition manually" and make one partition like 10 gigs for "/" and then about double your ram for the swap space, and lastly the rest to a third partition. 

This third partition have mount in /home. This way, if the same thing happens again, youcan just pop in an install cd/dvd and skip partitioning and install direclty (overwrite so to speak) to the partition with "/" on it (I like to make it hda1/sda1).  

This way your important documents on the desktop and etc are saved. This is because your desktop profile is in:

/home/{user}/Desktop/

If i'm wrong about the whole "quick repair" then it would be nice to learn about. But I'm like 60% sure there isn't.  In any case, storing your important docs on a diff partition is a good idea.

---

### Post by Arukas on 2007-09-21
What  is X?  

-Arukas

---

### Post by Arukas on 2007-09-21
Hello-

  I think i have a better way to reword my concern.

  I think i have changed settings that I don't even know about and they are interfering with my games that worked befored.  I have no idea how i might have changed them nor what I changed.  


-Arukas

---

