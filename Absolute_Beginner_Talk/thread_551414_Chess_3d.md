---
title: "Chess 3d"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Nikitas350 on 2007-09-15
I have a problem with the chess which is preinstalled in ubuntu 7.04. When i am trying to enable the 3d view i get an error message saying: "[SIZE="2"]Unable to enable 3D mode[/SIZE] Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.
You are still able to play chess in 2D without these packages."  What packages should i install in order to have the 3d mode enabled?? (and if it is possible to install them with one command; p.e. sudo apt-get install blablabla...) Thanks in advance.....

---

### Post by AlexenderReez on 2007-09-15
> **Nikitas350 said:**
> I have a problem with the chess which is preinstalled in ubuntu 7.04. When i am trying to enable the 3d view i get an error message saying: "[SIZE="2"]Unable to enable 3D mode[/SIZE] Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the **OpenGL Python bindings** and the** GtkGLExt Python** bindings.
*_You are still able to play chess in 2D without these packages_*."  What packages should i install in order to have the 3d mode enabled?? (and if it is possible to install them with one command; p.e. sudo apt-get install blablabla...) Thanks in advance.....

search for it in synaptic..and install ...if still failed ....

[SIZE="4"][COLOR="DarkSlateBlue"]==[/COLOR][/SIZE]

*_**[COLOR="RoyalBlue"]You are still able to play chess in 2D[/COLOR]**_*:lolflag::lolflag:

---

### Post by KIAaze on 2007-09-15
Install:
python-opengl
python-gtkglext1
libgtkglext1

Or by command-line:
```
sudo apt-get install python-opengl python-gtkglext1 libgtkglext1
```

I just tested it and it works for me.

---

### Post by Nikitas350 on 2007-09-15
It worked and for meeeeeeeeee. Thanksssss :popcorn:

---

### Post by orange2k on 2007-09-15
It does work when you install these things, but it does not look as cool as expected...
I still prefer the old 2D look - kind of why I like the Simpsons movie (now in 2D) more than any 3D animated movie...

---

### Post by Nikitas350 on 2007-09-15
> **orange2k said:**
> It does work when you install these things, but it does not look as cool as expected...
I still prefer the old 2D look - kind of why I like the Simpsons movie (now in 2D) more than any 3D animated movie...

Yeah, i think that vista's chess has a better appearence. But ubuntu's one is far more better (it is playing better and faster). Nothing is perfect... :)

---

### Post by Lord Illidan on 2007-09-15
Yes, the 3D chess really looks ugly, imho.

---

### Post by KIAaze on 2007-09-15
I just tried a few other chess games (all available in the repositories). Here's a quick review ;) :

1) 3dchess:
-launch with command "3Dc"
-actually not a 3D display, but rather a 3D-gameplay with three 2D chessboards

2) brutalchess:
good:
-3D looks good (has reflection)
-AI is fast
-displays trace of last move
-rotation possible with right-click
bad:
-3D is a bit slow (on my PC at least)
-has no menu apparently

3) dreamchess:
good:
-3D looks ok and is fast
-AI speed is good
-nice GUI
-very configurable with different pieces, boards, etc
-healthbars to display "health"~nb of pieces left
-8 difficulty levels
bad:
-rotation doesn't seem to be possible

4) pouetChess:
good:
-3D looks good and is fast
-rotation possible with right-click
bad:
-normal AI takes about 30 seconds, but by changing the difficulty level, you can change it from 2 to 90 seconds

---

### Post by neji on 2007-09-15
hey thanks, that's really helpful. Maybe you can start a blog or something where you review ubuntu games

---

### Post by KIAaze on 2007-09-15
[edit]
[B]Before I forget: There's a FOSS gaming tournament being prepared: [see here]("http://nuxified.org/article/nuxified_and_cluenet_prepare_a_gaming_tourney_you_are_invited").
If you want to play chess there too, sign up! :D[/B]
I haven't checked the multiplayer capabilities of the different chess games, but I'm quite sure it's possible to play them over the net.
[/edit]

Was that sarcastic or not? ^^

I have no blog, but there are already a lot of good linux gaming sites on the web, altough I agree one similar to gamespot with complete reviews for every game would be good.
If you know such a site, please tell me. ;)

This one appears to be ok and it's a wiki so it's editable :) :
[http://linux.strangegamer.com.nyud.net:8090/index.php?title=Main_Page](http://linux.strangegamer.com.nyud.net:8090/index.php?title=Main_Page)

Here are the ones I check often:
[http://freegamer.blogspot.com/](http://freegamer.blogspot.com/)
[http://gaming.gwos.org/doku.php/](http://gaming.gwos.org/doku.php/) (the wiki with the native games list seems to be down now unfortunately :( )
[http://happypenguin.org/](http://happypenguin.org/)

But they are more for news than reviews.

And wikipedia is helpful as always for these kinds of things:
[http://en.wikipedia.org/wiki/Category:Linux_games](http://en.wikipedia.org/wiki/Category:Linux_games)

The difference with commercial games is also that reviews can change during the development of the game...

---

### Post by vanadium on 2007-09-15
Does not work for me:

[code]
$ sudo apt-get install python-opengl python-gtkglext1 libgtkglext1
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-gtkglext1
[/code

That is on Ubuntu Feisty.

---

### Post by KIAaze on 2007-09-15
Oops, my fault. I use Gutsy so I didn't notice that python-gtkglext1 is not available for Feisty.

You could try downloading and installing the .deb for Gutsy. It might work if it doesn't require to many recent dependencies.
It's available here (at the end of the page):
[http://packages.ubuntu.com/gutsy/python/python-gtkglext1](http://packages.ubuntu.com/gutsy/python/python-gtkglext1)

edit:
There appears to be a .deb for Feisty here:
[http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437](http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437)

---

