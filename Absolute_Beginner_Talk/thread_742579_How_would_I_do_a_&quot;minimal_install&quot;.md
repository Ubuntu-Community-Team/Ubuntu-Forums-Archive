---
title: "How would I do a &quot;minimal install&quot;"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-04-01
If i wanted to do a "minimal install"  of Ubuntu, how would I do it and what advantages would it give me?

---

### Post by DGortze380 on 2008-04-01
do you mean a command line system? you'd use the alternate install cd. advantages? no gui. will run on older systems fast, with no issues (for the most part).

---

### Post by -gabe-noob- on 2008-04-01
I'm not sure if I completely understand.


I've seen people talking about doing a "minimal install" of ubuntu then putting KDE or XFCE ontop of it, instead of using Kubunut or Xubuntu, is this the same thing you're talking about?

---

### Post by mick8985 on 2008-04-01
No real advantage if you are running a desktop system, you could install without a graphical environment if you wanted to run a server or something. If you want a more lightweight desktop you could use xubuntu, using the xfce window manager, which is very gnome like.

---

### Post by NightwishFan on 2008-04-01
Here is a guide.
[http://www.psychocats.net/ubuntu/minimal]("http://www.psychocats.net/ubuntu/minimal")
Using a minimal install you can set up a lightweight wm like fluxbox without having to have used gnome/kde/xfce first.

---

### Post by -gabe-noob- on 2008-04-01
So if I did a min- install of ubuntu but then used KDE instead of icewm  as seen in your guide i'd get no preformance boost right?

---

### Post by NightwishFan on 2008-04-01
Actually I assume you would if you used kde-core, and not kde4 or kubuntu desktop. :)

---

### Post by mick8985 on 2008-04-01
Thats correct, the best way to tweak performance is to stop daemons like tracker running. I havent used kde in a long while so I cant really remember/not up to date with, how you go about stopping thigs like that in kde.

---

### Post by -gabe-noob- on 2008-04-01
@ nightwish fan 

so in your little guide i'd replace the lines that say "IceWM" with kde-core?

edit: after I do this "bare-bones installation" I'll have a Bare kde desktop with nothing installed correct?

double edit: If i do this while doing my math homework, from a distance I'll actully look smart :P just like when I was using the terminal today and convinced a few 5th graders I was hacking the School. It just so happens the internet went down in the school later that day, so they fell for it hook line and sinker :D

---

### Post by NightwishFan on 2008-04-01
Well it is Aysiu's guide, but yeah I assume that would work well. =D
Yes if you follow the guide you should have a desktop and firefox and synaptic and/or adept if you so choose

Kde-core will have a few apps though. Just to tell you a kde-core on 64bit took up onlylike 118mb ram for me. =D
Sorry to edit a bunch.. It might be a bit different on Gutsy, but it was intuitive (i did it)

---

### Post by -gabe-noob- on 2008-04-01
it'll be setup in the same fashion as a Kde 3.5 kubuntu install I assume?

---

### Post by -gabe-noob- on 2008-04-01
and how did you get you're kde-core install?

---

### Post by NightwishFan on 2008-04-01
kde-core is a package for kde3 that doesnt contain any extra applications I believe. I set mine up a similar way. Installing the xserver and kde-core and kdm, as well as adept.

---

### Post by -gabe-noob- on 2008-04-01
cool, so whats the difference between using a kde-core mini install and say using somthing like Arch with kde (you know besides the fact that one is Ubuntu basesd)

anyways I'm backing up my files and going through with it :D

---

### Post by NightwishFan on 2008-04-01
I haven't ever used arch, I just hear it is very customizable. I prefer Debian/Ubuntu though.

---

### Post by -gabe-noob- on 2008-04-01
running into a problem. 

Using the mini cd it keeps telling me that the mirror archive does not work, also it cannot get into my network, can I use the alternate install cd instead of the minimal cd and do it that way?

---

### Post by NightwishFan on 2008-04-01
I am not really an expert as I only did it once. I am not sure how the alternate cd would work for you. Worth a try though :(

---

### Post by ugm6hr on 2008-04-01
> **-gabe-noob- said:**
> Using the mini cd it keeps telling me that the mirror archive does not work, also it cannot get into my network, can I use the alternate install cd instead of the minimal cd and do it that way?

I suspect the Kubuntu Alternate CD has all the necessary files.

However, I don't know how to use apt-get from a CD repo.

It couldn't be as easy as installing a CLI interface (from AlternateCD), and then using the apt-get commands, could it?

The Xubuntu 7.10 AlternateCD automatically includes the CD in the repo list (in etc/apt/sources.list), so presumably Kubuntu does too:
```
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

---

### Post by -gabe-noob- on 2008-04-01
according to that guide it is, I'm off to the magical CLI land, see yah later peeps

---

### Post by NightwishFan on 2008-04-01
Good luck! May the strength of the pink ponies go with you. :KS:popcorn::KS

---

