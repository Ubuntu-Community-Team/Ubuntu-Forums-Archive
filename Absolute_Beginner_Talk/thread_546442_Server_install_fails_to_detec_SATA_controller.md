---
title: "Server install fails to detec SATA controller"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by aaltieri on 2007-09-08
Greetings;

I am trying to re-install my Myth server (migrating to new hard drives).  But I'm having a time with the Sata controller.  Here's what happens:

I can install Dapper, Edgy, or Fiesty LIVE DESKTOP version no worries.  But when I try to install either the server or alternate versions of any of these, the text installer fails, and tells me I need a driver for my hard drive controller.  

It is the Asus P5LP Lakeport logic board.  Edgy is running fine (migrating to larger drives) so I can pull the drivers off that install, and push them into the Feisty install, or the edgy server install for that matter.  What I need help with is finding the files I need to copy.

The device manager in GDM lists it as "82801 GB/GR/GH (ICH7)

Now, why we have different drivers on the CD's is beyond me.  That really seems silly.  The last time I installed, I installed Edgy desktop, and then spent HOURS removing just about every blessed thing to get it to where I could use it as a MythTV back/front end without all the bloat.  And I'm REALLY trying to avoid doing that again.

Any help is appreciated!  Thanks!


Peace!

---

### Post by aaltieri on 2007-09-12
I have found part of my problems...kinda.

On the Lakeport motherboard, you have two modes for the hard drive controller:

Combined mode 
Enhanced mode

I can boot into the full live CD's of Dapper or Edgy if I set the board to enhanced mode.  This gives me  all my drives.  Then I spend an hour or two removing all the bloat.

The alternative and server installs of Edgy and Dapper will boot in Combined mode only.  The problem with this is that the IDE interface takes precedence so I loose my other two SATA drives.  

Feisty just plain won't boot on this system at all.  I tried booting from install CD's and loading Edgy, then upgrading.  After the upgrade, it can no longer boot.

So my question is this:  _IS_ there a way to make Feisty work?  Or should I give up and try another Linux Distro or use an outmoded version of Ubuntu?  Knoppix loads no problems.  I haven't tried FC7 yet to see.

---

