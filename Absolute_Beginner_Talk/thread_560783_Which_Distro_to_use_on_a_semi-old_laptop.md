---
title: "Which Distro to use on a semi-old laptop?"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by new2*buntu on 2007-09-26
First off, I would like to say hello to everyone, as this is my first post. 

Here is the problem: On my 1.6 GHz dual-core processor with 512 MB Ram, Ubuntu runs great.
But my little sister has seen my use Ubuntu (with Beryl) and she says she wants it too. But her computer is a 700 MHz Pentium III with 256 MB RAM. I have tried to install Ubuntu, but it was too sluggish. I am not sure what to try next. I have found that XFCE may work well on this setup but I am no expert on this, since I just switched to Ubuntu myself for about 3 weeks. :)
Any Suggestions?

P.S. Ubuntu Rocks!!!

---

### Post by bodhi.zazen on 2007-09-26
Wolvix + Beryl

You will have to do some config to get Beryl up ...

[http://wiki.wolvix.org/Beryl](http://wiki.wolvix.org/Beryl)

What video card by the way ?

---

### Post by new2*buntu on 2007-09-26
DXDIAG says that I have an S3 Savage IV.
And it says it has approx. 8 MB of total memory, but I am not sure if that is right.
A quick Google Search gave me this:
[http://en.wikipedia.org/wiki/S3_Savage#Savage4]("http://en.wikipedia.org/wiki/S3_Savage#Savage4")
Also, when I went to Wolvix.org it asked if I wanted "Cub" or "Hunter."
I am not sure.

---

### Post by exile on 2007-09-26
I can't answer for laptops but on older hardware I've found Slackware to be pretty snappy - it takes more effort to set up, but its not terribly hard imo. Maybe look at SLAX : [http://www.slax.org/]("http://www.slax.org/").

Often though I don't think the distro plays as much into it as the windows manager and the services/software that is installed. Changing to XFCE, Fluxbox, OpenBox etc will sit nicely on lower specced machines - however, once again the setup effort is increased and it can be a bit too much of a shift for new people that are used to the Windows way of desktops.

Good luck & let us know how you go with it.

---

### Post by viergeame on 2007-09-26
I am stuck on a 700MHz and I run Fiesty with Compiz-Fusion nicely.  I don't know how well that works on XFCE though.  I know that I could never get Beryl to run correctly on XFCE.  With a good enough video card she should be able to try out Beryl, though probably not with some of the more intense effects.

---

### Post by tdrusk on 2007-09-26
Xubuntu if she can stand it being a little slow.

Puppy Linux if she wants her computer to be faster than yours.

---

### Post by new2*buntu on 2007-09-26
I have showed her Puppy Linux (I put it onto my Flash Drive) and she doesn't like it. Xubuntu sounds good, I will try it out.

---

### Post by tdrusk on 2007-09-26
> **new2*buntu said:**
> I have showed her Puppy Linux (I put it onto my Flash Drive) and she doesn't like it. Xubuntu sounds good, I will try it out.

I would suggest Xubuntu anyway. I really love puppy, but if you learn a lot about Ubuntu, Xubuntu will be easy to work with.

Install Ubuntu on her laptop and open a terminal. Run
```

sudo aptitude install xubuntu-desktop
```
Then if you want to remove Gnome
```
sudo aptitude remove ubuntu-desktop
```

That way is  a whole lot easier than downloading the iso.

---

### Post by new2*buntu on 2007-09-26
OK, I just tried SLAX (the live CD) and it couldn't connect to the internet wirelessly. My sister's computer uses an Asante Aerolan AL5410-G card. Any way to get the drivers to work?

Ok, I will put Ubuntu onto her computer and then install xubuntu-desktop. I will keep Windows there though.

---

### Post by tdrusk on 2007-09-26
> **new2*buntu said:**
> OK, I just tried SLAX (the live CD) and it couldn't connect to the internet wirelessly. My sister's computer uses an Asante Aerolan AL5410-G card. Any way to get the drivers to work?

Ok, I will put Ubuntu onto her computer and then install xubuntu-desktop. I will keep Windows there though.

Once you get Ubuntu installed and you are ready to mess with wireless (if it doesn't work out of the box), open a terminal and put
```
lspci
```

then copy and paste the output here.

---

### Post by new2*buntu on 2007-09-26
I'll try to get Ubuntu installed. But I may have to do it tomorrow since I have school and can't go to sleep too late.

---

### Post by mrcanard on 2007-09-26
See if you can install another 256 Mb of ram.
I have a 766Mhz w/390 ram that does a fair job of running Ubuntu 7.04. It won't run Compiz.
Xubuntu seems to be missing a lots of features that I use in Ubuntu.

---

### Post by new2*buntu on 2007-09-26
That is a good idea. I'll ask my dad to get some RAM to make her computer more useable.

---

### Post by diction on 2007-09-27
> **mrcanard said:**
> See if you can install another 256 Mb of ram.
I have a 766Mhz w/390 ram that does a fair job of running Ubuntu 7.04. It won't run Compiz.
Xubuntu seems to be missing a lots of features that I use in Ubuntu.


I agree. On 512mb ram, things should go a lot smoother.

---

