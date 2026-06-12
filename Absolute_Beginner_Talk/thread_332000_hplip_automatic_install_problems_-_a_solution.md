---
title: "hplip automatic install problems - a solution?"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by dips on 2007-01-05
Hi there,

I have just been through a painful 12 hours or so trying to get my Ubuntu 6.06 to talk to an HP Photosmart 2710 all in one machine made slightly worse as it connects via a wireless card.

I tried the usual places and found and downloaded the hplip-1.6.12 installer, ran it and selected automatic for ubuntu 6.06 and watched it do it's stuff right up to the point where it tried to download the missing requirements where it just sat. :-? Onto the forums and then back to enabled Universe and Multiverse, back to the installer but nothing doing. Tried to do it via the tarball with more success only the excellent instructions I found via another forum link wanted me to make and make install but my system reported that make didn't exist. More googling, more forums more attempts and more frustration.](*,)  Eventually I realised that I was going about this all wrong - probably due to my inexperience with linux in general. 

So, I made a note of all the missing dependencies and used Synaptic to find each one in turn and install them.Okay purist may have said use a terminal but hey, it worked.
When the Postfix dialouge popped up I selected the don't configure option.

I then ran the installer again and, despite the error message reporting that HPLIP wasMalready installed on my system it actually worked! It ran Make and Make Install and the dialouge box popped up allowing me to select the wireless connection option.:D 

So if anyone out there is in a similar situation take heart. I know that I probably make things worse for myself but if you keep going and think it through logically (not my strong point) with some help from the community and a little luck it will work.

---

### Post by 11hjpphty76lkjj on 2007-01-12
Sorry for your experience with the automatic installer.  I'm working on a solution.  The problem is that when the installer is installing lsb it also pulls in postfix which requires some configuration and the installer stops at that point.

I'm hoping to have this fixed in the next release.  Or at least a work around.

Aaron

---

