---
title: "First look at Kubuntu, some teething isues"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by Brinstar on 2005-09-02
Okay, today i had my first look at the Kubuntu live cd(hoary), and also my first look at linux in over 5 years. Its come a long way for sure, but still has a few issues that hold me back from deleting the WinXP partition just yet.

I have a lot of questions on my mind but to begin with:

1. hey, no games?

2. my Wifi card (Centrino-based) seems to have been detected and installed, but why did my access point show up and not connect?

3. why couldn't i access my WinXP partition from Konqueror?

4. why didn't the OpenGL screen savers work even though OpenGl was detected on my card, and the appropriate Mesa driver was installed (i think)?

5. what difference would it make using 'normal' or Gnome Ubuntu?
okay, thats enough to get us started.

anyway, despite the problems, i was impressed with how far Linux has come in 5 years, and i look forward to the imminent release of Ubuntu 5.10 with great interest.

---

### Post by KingBahamut on 2005-09-02
1. apt-get install bzflag freeciv glob2 gnotacan vegastrike tuxracer tuxkart 
  -- now you have some games. =) 
2. Probably need to edit your config in /etc to reflect your wirless router settings.
3. need to edit your fstab to reflect this line --
  /dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
where hda1 is a variable that is the partition your trying to mount. 
4. Which card do you have? 
5. Gnome Ubuntu runs Gnome as default Desktop, Kubuntu runs KDE as def desktop. 

Helping thus far?

---

### Post by Brinstar on 2005-09-02
KingBahamut, thanks for your quick response, i really appreciate it :)


in reply to what graphics card i have, its an Intel Graphics 855GM jobby, pretty fast for an onboard card in WinXP, runs games like KOTOR and Homeworld 2 (my current time-sponge) just fine. As for the Gnome/KDE, what i actually had in mind was something along the lines of, 'Gnome would probably be easier to use for a beginner, KDE looks better', since I really don't know how much either environment has changed, as I have not kept up with the advances of both, so basically a recommendation is what I need ;)

---

### Post by KingBahamut on 2005-09-02
Brin, Ive never had much success getting 3d accel to run on an intel based card. Im not wholely sure you can.....Someone will surely correct me on this, but thats my impression.

---

### Post by Hobbsee on 2005-09-02
[QUOTE=Brinstar]
4. why didn't the OpenGL screen savers work even though OpenGl was detected on my card, and the appropriate Mesa driver was installed (i think)?
[/QUOTE]

For some reason, the openGL ones dont auto install...

try "sudo apt-get install rss-glx" - you may also need the other screensaver packages, but try that one first.

For some silly reason, that is the only screensaver file that doesnt have "screensaver" in the title.

That should solve the problem - took me ages to figure out the solution again when i reinstalled kubuntu yesterday :D

That tuxkart looks awesome!  Just downloaded it!

---

### Post by sophtpaw on 2005-09-02
[QUOTE=KingBahamut]1. apt-get install bzflag freeciv glob2 gnotacan vegastrike tuxracer tuxkart 
  -- now you have some games. =) 


Helping thus far?[/QUOTE]


Lond live the King!

I don't have the package gnotacan. Is this a game i can run in Gnome? 

thx,

--
sophtpaw

---

### Post by xmastree on 2005-09-02
[QUOTE=Brinstar]1. hey, no games?[/QUOTE]Fire up synaptic, click "sections" scroll down to "games and amusement" and take your pick.

---

### Post by Hobbsee on 2005-09-03
[QUOTE=xmastree]Fire up synaptic, click "sections" scroll down to "games and amusement" and take your pick.[/QUOTE]
 also check the games under kde desktop environment section as well...

---

