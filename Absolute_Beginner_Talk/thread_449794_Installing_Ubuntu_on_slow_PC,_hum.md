---
title: "Installing Ubuntu on slow PC, hum"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by fruitsofherwomb on 2007-05-20
Well, my friend had Windows ME on his PC and I told him it was crap since it was, So suggested that he try ubuntu (or Kubuntu) but the installer takes FOREVER, first Ubuntu doesn't boot the installer, Kubutnu does but is slllllllllllllllllllooooooow, The power went out at 15 percent installing, and it didn't install the whole thing and now doesn't boot from cd to finish, annoying. 

I was going to prob try to burn a new disk and try it... What do you guys suggest for a not so great pc? 










fanx.

---

### Post by Bachstelze on 2007-05-20
What are the specs of the PC, exactly ?

---

### Post by fruitsofherwomb on 2007-05-20
Yeah thats the problem I don't know the specs, If I had to guess i'd say around 128mb of ram, Pent III1.5 ghx?

---

### Post by drowner on 2007-05-20
Use the Alternate CD. It works better on slower systems

---

### Post by overdrank on 2007-05-20
> **fruitsofherwomb said:**
> Well, my friend had Windows ME on his PC and I told him it was crap since it was, So suggested that he try ubuntu (or Kubuntu) but the installer takes FOREVER, first Ubuntu doesn't boot the installer, Kubutnu does but is slllllllllllllllllllooooooow, The power went out at 15 percent installing, and it didn't install the whole thing and now doesn't boot from cd to finish, annoying. 

I was going to prob try to burn a new disk and try it... What do you guys suggest for a not so great pc? 










fanx.

Hi and I might suggest that you check bios and make sure it is still set to boot to cd with a power outage, the bios could have reset to default.

---

### Post by bobplano on 2007-05-20
you might also want to try xubuntu. after xubuntu's customized it can look pretty good.

---

### Post by AndyCooll on 2007-05-20
Slower pc's (i.e. those with less than 256mb of RAM) often have problems using the main Ubuntu install disk. There are however alternatives and you may need to use one of the methods. These include doing an install using the alternative cd version,  or beginning by using a server install cd, or even using the mini install cd.

There are some good notes here: [ Modest Spec or Barebones Installation of Ubuntu]("http://www.psychocats.net/ubuntu/minimal#barebones")

:cool:

---

### Post by nerdman978 on 2007-05-20
Try using Xubuntu on a slower PC. I used it on a 1Ghz 256MB RAM computer and it worked fine. I just don't like XFCE so I switched to OpenSUSE

---

### Post by ugm6hr on 2007-05-20
Agree with nerdman978 - Xubuntu is probably best hope for an official Ubuntu variant.  And likely only from the alternate install CD (although the Live CD will probably run but not install).  All the forum / community docs are reasonably easily translated into Xubuntu, which is it's main benefit.  And XFCE is an acquired taste - I think it's great when you get to know how to customise it.

If you're looking for alternatives, my choice is Puppy Linux for old hardware (but predominantly because it installs easily from a Live CD wizard on almost anything, and only takes about 20 minutes (depending on hardware).  It's just had 2.16 released (which I haven't tried - but the beta looked good).

---

### Post by zorog on 2007-05-20
Hi all I spent all weekend trying to get Feisty Fawn (7.04) standard CD up and running on my thinkpad r30 laptop with 256mb of ram, the install was so very slow, after much playing around, burning new CDs, swapping out HDD's ect...

I almost gave up..

until I tried one last time  this time I found a post about enabling a swap file on the hard drive for the live CD to use ([http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html](http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html))
and bingo the install was snappy and quick! so here's a quick run down of what I did...

Firstly I let the live CD boot up

then using **Ctrl+Alt+F1** I brought up a  console and entered to following commands:

I used fdisk to delete my old windows XP partition and created a new empty partition I'm lazy so I just used the whole disk  for my new partition as the Install was going to overwrite it anyway
**sudo fdisk /dev/hda**

then I used my new blank partition for a swap
**sudo mkswap /dev/hda1**  
**sudo swapon /dev/hda1 **

the re entered  graphical mode by pressing **Ctrl + Alt +F7**
and then used the install icon on the desktop and all was and still is sweet

I hope this helps
Have Fun,
Simon

---

### Post by prince_alfie on 2007-05-21
> **zorog said:**
> Hi all I spent all weekend trying to get Feisty Fawn (7.04) standard CD up and running on my thinkpad r30 laptop with 256mb of ram, the install was so very slow, after much playing around, burning new CDs, swapping out HDD's ect...

I almost gave up..

until I tried one last time  this time I found a post about enabling a swap file on the hard drive for the live CD to use ([http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html](http://linuxondesktop.blogspot.com/2007/02/installing-ubuntu-6.html))
and bingo the install was snappy and quick! so here's a quick run down of what I did...

Firstly I let the live CD boot up

then using **Ctrl+Alt+F1** I brought up a  console and entered to following commands:

I used fdisk to delete my old windows XP partition and created a new empty partition I'm lazy so I just used the whole disk  for my new partition as the Install was going to overwrite it anyway
**sudo fdisk /dev/hda**

then I used my new blank partition for a swap
**sudo mkswap /dev/hda1**  
**sudo swapon /dev/hda1 **

the re entered  graphical mode by pressing **Ctrl + Alt +F7**
and then used the install icon on the desktop and all was and still is sweet

I hope this helps
Have Fun,
Simon

Thanks for the help... looks like i will check this out! :D

---

