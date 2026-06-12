---
title: "Drive Partitioning question for Ubuntu Install (/home?)"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by dmorand on 2007-07-16
I already installed Ubuntu, but ran into some issues, so I'm reinstalling now.  I have a couple of probably dumb questions, but I'm very new to Ubuntu so please bear with me.  

I partitioned my drive out the following:

hda1 90gig - Windows Partition (NTFS)
hda2 5gig - /
hda3 40 gig /home
hda4 1 gig linux swap

The thing I noticed is that I was installing apps in Ubuntu, and the root drive kept getting smaller.  What exactly is the home folder used for?  I thought that the apps would install in that folder, not in my root.  Like I said this is probably a dumb question.  I'm just trying to get a good understanding of all of this so I know what the hell I'm doing.

---

### Post by davidjmayo on 2007-07-16
> **dmorand said:**
> I already installed Ubuntu, but ran into some issues, so I'm reinstalling now.  I have a couple of probably dumb questions, but I'm very new to Ubuntu so please bear with me.  

I partitioned my drive out the following:

hda1 90gig - Windows Partition (NTFS)
hda2 5gig - /
hda3 40 gig /home
hda4 1 gig linux swap

The thing I noticed is that I was installing apps in Ubuntu, and the root drive kept getting smaller.  What exactly is the home folder used for?  I thought that the apps would install in that folder, not in my root.  Like I said this is probably a dumb question.  I'm just trying to get a good understanding of all of this so I know what the hell I'm doing.

There are no dumb questions - if you don't know ask for advice and people will try to help you.
Apps installed in Ubuntu go in root so they are available to other users, depending on the permissions. Most people recommend 10GB for root ( / ). If you think you are going to add a lot of apps maybe 15GB but 10 should be enough. 

/Home stores user settings (e.g. bookmarks, email, app settings you choose, desktop etc.). It can also be used to save your data if you want.

Swap is usually 2 X RAM. If you have 1GB of RAM 1GB is Ok for swap unless you plan to do intensive stuff like multimedia

HTH

---

### Post by dmorand on 2007-07-16
Is 15 gig enough even if I install some games?

I don't see how I'd need so much more space in my /home folder if it just stores the files you mentioned above.

---

### Post by davidjmayo on 2007-07-16
Sorry don't know I'm not a gamer so don't know what kind of space they use.

To help others assist you can you say what games or what kind of games you're looking at playing

---

### Post by dmorand on 2007-07-16
What's a good space allocation for /home?  I was thinking 30 gig.

---

### Post by Daveth on 2007-07-16
given that all your documents, digital pictures, music, pdfs and, if you are using wine, all your game files (5gb under Steam for Half life 2 on mine) end up in /home, the bigger the better. You could always steal some from that windows partition, of course!

---

### Post by davidjmayo on 2007-07-16
> **Daveth said:**
> given that all your documents, digital pictures, music, pdfs and, if you are using wine, all your game files (5gb under Steam for Half life 2 on mine) end up in /home, the bigger the better. You could always steal some from that windows partition, of course!

good point

Also you can change the partition sizes later if you needed to with GParted or GParted Live cd (I prefer the GParted Live Cd)

Note if you resize that win partition defrag it a few times BEFORE you resize and back it up . there is always a  risk with re-partitioning causing corruption.

---

### Post by dmorand on 2007-07-16
Yeah I think I'll start with 30, then resize if necessary.  I'll make a cd of the Gparted Live CD.

---

### Post by davidjmayo on 2007-07-16
see my edit if you missed it

---

### Post by dmorand on 2007-07-16
Good point.  I was actually thinking about doing a defrag.  Thanks for the tip!!

---

### Post by dptxp on 2007-07-16
Give 10 GB to /, 2 GB to SWAP, rest to /home. Data by default is stored in /home/<username>.

You can always make more data partitions in the NTFS section.

---

