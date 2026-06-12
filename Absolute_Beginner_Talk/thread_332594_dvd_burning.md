---
title: "dvd burning"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2007-01-06
ok ive had ubuntu for about a month now and i would like to burn some movies i haved ripped to 700mb divx/xvid clips. when i was a windows user i used VSO Software's ConvertXtoDVD, which converted the divx to whatever it needed to be for dvd and burned it with one click. i was able to burn three divx movies to one dvd-r with a custom background image and custom menu text, also i was able to choose whether i wanted the movies to play sequentially or not or loop playback.  i dont really care about all these options except for making my own menu screen and getting three movies to a dvd-r that plays in standalone dvd players. i have devede now and i juast tryed it and it only allows 1 divx/xvid to a dvd before it says its full but when i got to burn it sayd its only about 1.5gb to the disk. is there a recommended program(s) to do this??? or ami doing something wrong with devede??? thanks in advance!!!!

---

### Post by shanepardue on 2007-01-06
I don't know if this does that, but K9copy is the best I've found for backing up DVD's.

---

### Post by antgul3382 on 2007-01-06
there would be no point to me  of backin them up if i cant put more than one on a disc

---

### Post by shanepardue on 2007-01-06
You can change the target file size of each movie.

---

### Post by antgul3382 on 2007-01-07
k9copy suck its just a copying prog i have about 30 on my hdd that i wanna put to dvd with windows that would take 10 dvds with linux it will take 30   im wondering how i can put more than one to a disc

---

### Post by Artemis3 on 2007-01-07
Use [tovid](http://tovid.wikia.com/). It is not in ubuntu repositories so follow the instructions in their page to install it. I recommend you skip the debian package for tovid itself and pull it from svn (read their forums) to compile.

It does depend on several packages, most available in the repositories, i think i installed a couple from debian testing as they were missing from ubuntu servers.

Yes in short, you feed tovid with, whatever, and it outputs compliant dvd video.

You can use tovidgui as a start but its more fun to tweak the settings using the scripts directly from the command line.

---

### Post by nix4me on 2007-01-07
devede does it.  I made a dvd yesterday with 30 cartoon episodes on it.  They play one after another.

nix4me

---

### Post by halitech on 2007-01-07
ManDVD is a good program if you want to put multiple movies on 1 dvd. It will allow you to create a background, sounds, images for each movie instead of text. or you can try the tutorial here
[http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux")
if you feel up to trying the CLI

---

### Post by antgul3382 on 2007-01-07
how can i   get mandvd??? i searched synaptic git nothingq

---

### Post by halitech on 2007-01-07
they don't seem to have it listed for Edgy but the Dapper version should work. the easiest way would be to go here:

[http://www.getdeb.net/category.php?id=4&release=Dapper]("http://www.getdeb.net/category.php?id=4&release=Dapper")

and go down and get the deb version then just double click on it. If that doesn't, google will find plenty of places to get the source files so you can compile it by hand (but the dapper deb file should work fine)

---

### Post by antgul3382 on 2007-01-11
you usnt have noticed im running the x64 version this wont work is there a 64 bit version?

---

### Post by lamego on 2007-01-21
I have uploade the latest version:
[http://www.getdeb.net/app.php?name=mandvd](http://www.getdeb.net/app.php?name=mandvd)
It can be installed on Dapper or Edgy (32 bits).

---

