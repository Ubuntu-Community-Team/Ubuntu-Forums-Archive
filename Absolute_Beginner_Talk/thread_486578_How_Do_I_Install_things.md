---
title: "How Do I Install things :?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by TehCJ on 2007-06-28
Hi guys I need help atlatste 2 more times!



1: How do i install thing 

2: What Things do i need to get Beryl and games working




                                           ** PLEASE HELP** :popcorn:

---

### Post by vlees91 on 2007-06-28
1. add/remove software or synaptic
2. [http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)

games with cedega...

---

### Post by RomeReactor on 2007-06-28
Hi. To install programs, use the **Add/Remove** application (go to "Applications-->Add/Remove"); regarding Beryl, it depends what graphics card you have and if your system has enough ram and a relatively modern processor. Take a look at this [link]("http://ubuntuforums.org/showthread.php?t=349732").

---

### Post by nekoyokoshima on 2007-06-28
I find [Ubuntu:Feisty wiki]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") to be helpful for beginners. You should take a look.

---

### Post by pyros on 2007-06-28
> **TehCJ said:**
> Hi guys I need help atlatste 2 more times!



1: How do i install thing 

2: What Things do i need to get Beryl and games working




                                           ** PLEASE HELP** :popcorn:
The easiest way to install software is through "Add/Remove..." in the applications menu. For a quick how-to on other ways of installing software in ubuntu, have a look at:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

The first step toward getting Beryl and games working would be to determine what type of video card you have, then have a look here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)
to see about installing a 3d driver for your card (assuming that it is not already installed)

There is also a sticky post at the top of the beginners subform about installing beryl and compiz that you may want to read before you start.
---
(edit: outshot twice, have to start typing faster...)

---

### Post by TehCJ on 2007-06-28
> **pyros said:**
> The easiest way to install software is through "Add/Remove..." in the applications menu. For a quick how-to on other ways of installing software in ubuntu, have a look at:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

The first step toward getting Beryl and games working would be to determine what type of video card you have, then have a look here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Graphics_Card)
to see about installing a 3d driver for your card (assuming that it is not already installed)

There is also a sticky post at the top of the beginners subform about installing beryl and compiz that you may want to read before you start.
---
(edit: outshot twice, have to start typing faster...)

Yes I have a Good Graphics card: Nvidia6800


                            ram: 1 Gig

---

### Post by Inxsible on 2007-06-28
You can install in 1 of 4 ways:
 
1) Applications --> Add/Remove. Search and install
 
2) System --> Administration --> Synaptic Package Manager. Search and install
 
3) ```
sudo aptitude install packagename
```
 
4) ```
sudo apt-get install packagename
```
 
I kinda like method 3 the best because aptitude keeps track of dependencies too.
 
to install beryl
```
sudo aptitude install beryl beryl-manager
```

---

### Post by Calash on 2007-06-28
I run City of Heroes on a 6800 with no problem.  Framerate is good and the game plays smooth.


Cedega is not free, so before investing check out there database and make sure the games you want to play are listed there.

Wine is also a good way to play some games.  They have there own database of supported apps, so check it out as well.  Being free it is easier to justify the install :)

Definetly check out the Wiki posted earlier. It helped me out a lot. 

For installing the methods listed are the easiest ways, but not the only ways.  Howeverr it is a good idea to stick to the basics until you get more confortable with the OS.  Then you can play around with the package manager, external repositores, .deb files, and compiling the apps yourself ;)

---

### Post by TehCJ on 2007-06-28
> **TehCJ said:**
> Hi guys I need help atlatste 2 more times!



1: How do i install thing 

2: What Things do i need to get Beryl and games working




                                           ** PLEASE HELP** :popcorn:



How do I Install MSI Files?? Please Help me On that! :D :tongue::-({|=

---

### Post by pyros on 2007-06-28
For that you will need a way to install and run windows programs. there are three options that I know of, cedega, crossover office, and wine. cedega and crossover office are basically extended versions of wine. cedega is geared more towards games. But, personally, I have to agree with Calash

---

