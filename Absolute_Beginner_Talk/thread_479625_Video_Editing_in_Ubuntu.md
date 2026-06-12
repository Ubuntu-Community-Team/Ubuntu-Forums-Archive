---
title: "Video Editing in Ubuntu"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by bagrol1 on 2007-06-20
During my transition to Ubuntu from XP, I plan to use Sony Vegas for video editing. I believe the only way of doing it is by mouting XP with virtual progs like VMware or Virtual Box.

Questions:

1. Will these progs allow Vegas to see firewire port to capture DV?  I know USB ports work in virtual environment, but don't know about firewire.

2. I tried reverse, i.e., Ubuntu in virtual machine in XP and it was painfully slow on my old comp. My new setup is: E6420 C2D overclocked to 3.5GHz, 2GB RAM, NVIDIA 7900GS, Seagate 320GB HD.  Will this setup allow for a responsive video editing in a virtual machine???

3. Which program is faster VMware or Virtual Box, or maybe KVM?

Thanx.

---

### Post by empthollow on 2007-06-20
i have never used vmware or virtual box to run windows progs under linux.  Wine is becomming quite a nice tool for running windows progs.  it emulates windows api's instead of the entire desktop so it acts much more like a native application.  if that doesn't work you could try xcrossover - this however is about $30.  wine is available in the repositories.  you can visit [www.winehq.org](www.winehq.org) and click on appDB on the left side. search for you program and you may find some tips or tricks if it doesn't work right away.  good luck.

---

### Post by Daisybobs on 2007-06-20
Don't use VMware, it will be too slow. I doubt Virtual Box will allow you to capture from Firewire too.

empthollow is right, try wine. It may take a bit of tweaking but you'll get a better result. The  results for wine with Adobe Premiere are pretty weak so don't expect perfection.

Have you tried [Cinelera]("http://heroinewarrior.com/cinelerra.php3") yet?  This repository for feisty might help:

[http://www.kiberpipa.org/~gandalf/blog/?p=77](http://www.kiberpipa.org/~gandalf/blog/?p=77)

---

### Post by iPirates on 2007-06-20
try looking around for a how-to on installing vegas with wine, if you choose to go that way.  see if somebody else has got it running in wine, because sometimes installing and running applications with wine can get a little complicated.  wine is getting better, but i mean we're essentially talking about tricking your system into thinking the windows program is a linux program.  there's bound to be little issues to crop up here and there, so check to see how other people have got it installed, and try following their steps.

---

### Post by bagrol1 on 2007-06-20
Wine application database indicates that Vegas does not work at all and actually none of video editor such as Premiere, Pinnacle or Ulead Studio works. Thus the only option is full XP virtualization, but I am concerned about speed and usablity.

---

### Post by doobit on 2007-06-20
That is correct. Vegas requires DirectX, DirectShow, and QuickTime. Your best bet is to use a dual boot box.

---

### Post by djorzgul on 2007-06-21
also vegas requires Microsoft .NET Framework 2.0

---

### Post by tregeagle on 2007-07-02
I used to use Video Vegas (which I think is pre-taken-over version of Sony Vegas). Great program. I have just started using Cinelerra on Ubuntu Feisty, it installed easily and runs OK on my 3yr old P4 laptop. It is not as cut and polished as Vegas but seems to have a lot of features under the bonnet. 

I've decided to go wih it for now, along with a few other tools (e.g Kino) I reckon it'll be worth learning...

---

