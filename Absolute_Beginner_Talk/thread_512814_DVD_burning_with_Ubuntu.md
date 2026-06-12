---
title: "DVD burning with Ubuntu"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by yogo on 2007-07-29
I am new to Ubuntu like many of you and have been reading over the threads on getting things going.

Seems video playback and burning are causing some major headaches and a rush to the drugstore for more Tylenol.  With Windows I had a system for backing up DVD's which used three programs, two of which I got going under Wine, DVDFAB HD decrypter worked flawlessly the first time, however DVD Shrink failed on the last second with an error.

To make a long story short, I decided to use 100% new programs used under Ubuntu. K9copy was a bit difficult to get going. 

*Select your DVD drive for the output source and click on the folder and it will then give you all your titles. Then just click on the DVD icon and it should copy*, mine did not, I got a signal 11 sigsegv error and kept getting this error. The problem somehow fixed itself, maybe from restarting the app, I am not sure but finally it went. and did what it was suppose to do. I then used K3B which I love out of the box, worked great and I did not make a coaster although I was expecting one after such a troublesome day getting burning going. One of the things I noticed is that many programs are set to look for a certain browser, I think they should look for the default browser and use that no matter what the end user has chosen. Such was the case with K3B.

I normally used IMGburn with Windows but really liked K3B on my first run.

I am confused as to why K9copy is 85mb when DVD Shrink is so small? Maybe all the codecs...?

I like the default delete .iso that Imgburn has, not sure there is one in K3B but probably it is there as it seems to be a more complete burner.


My reason for starting this thread is to hopefully have one area where we can discuss multiple apps regarding DVD burning.

---

### Post by ron999 on 2007-07-29
These are the ones I use:-
AcidRip to rip a DVD into an avi or mpg file.
K9copy to rip a DVD onto a 4.7GB DVD+-R.
DeVeDe to create a DVD from an avi or mpg file.
K3b to burn CDs and DVDs.
:cool:

---

### Post by MrKlean on 2007-07-29
I agree...but...I'm having trouble with devede since I switched to 7.04  : (  I get a movie made, but the sound is scratchy !!

Any thots would be appreciated !
thanks ; )

---

### Post by ron999 on 2007-07-29
> **MrKlean said:**
> I agree...but...I'm having trouble with devede since I switched to 7.04  : (  I get a movie made, but the sound is scratchy !!

Any thots would be appreciated !
thanks ; )

You can use tovid from the command line (CLI) instead of DeVeDe.
This is the link:- [http://tovid.wikia.com/wiki/Main_Page]("http://tovid.wikia.com/wiki/Main_Page")

It's long-winded, but you do it in stages.
Like this:-
1) Use tovid to convert the file(s) to MPEG2, DVD compliant format.
2) Use makemenu to make a menu, if required.
3) Use makexml to make an xml file.
4) Use makedvd to author the DVD (Creates a VIDEO_TS folder containing IFO, BUP and VOB files).
5) Use K3B to create an ISO image file.
6) Use VLC to test view the ISO.
7) Use K3B to burn the ISO.
:cool:

---

### Post by alienexplorers on 2007-07-29
T copy or make new DVD's I use K3B.  Has never failed me yet.

---

### Post by meho_r on 2007-07-29
Yeah, I've tried Gnome Baker and Brasero, but K3b is No.1, definitely. It'll be nice to have similar app for Gnome, maybe G3b or something:D

---

### Post by zerobinary on 2007-07-29
how about burning ogm

---

### Post by yogo on 2007-07-29
I foolishly googled T copy, because I had not heard of that program but then when it did not return anything, I realized Alien E meant (To copy)

I agree that K3B is a great program and I look forward to working with it.

I am going to try the Acidrip, would that be good for video from a video camera? my son is two, almost three so I have lots of video to edit although I am not good at the editing!

---

### Post by Mawy on 2007-07-29
> **MrKlean said:**
> I agree...but...I'm having trouble with devede since I switched to 7.04  : (  I get a movie made, but the sound is scratchy !!

Any thots would be appreciated !
thanks ; )

I had the same problem, and found this site, got it working perfectly :)

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

> **ron999 said:**
> These are the ones I use:-
AcidRip to rip a DVD into an avi or mpg file.
K9copy to rip a DVD onto a 4.7GB DVD+-R.
DeVeDe to create a DVD from an avi or mpg file.
K3b to burn CDs and DVDs.
:cool:

Same here, spent a day or so trying all the different programs out there, these were the winners.

Cheers,
Mawy

---

### Post by stinger30au on 2007-07-30
i have beenhaving all sorts of dramas with native linux apps. i gave up and rip dvds using wine and the freeware dvdfab hd decrypter.

i wish there was a newbies or dummies guide to ripping dvds on ubuntu somewhere

---

### Post by zerobinary on 2007-07-30
is there any app in buring ogm and mkv 
it seems linux don't have whose app with the gui one

---

### Post by yogo on 2007-07-30
> **stinger30au said:**
> i have beenhaving all sorts of dramas with native linux apps. i gave up and rip dvds using wine and the freeware dvdfab hd decrypter.

i wish there was a newbies or dummies guide to ripping dvds on ubuntu somewhere

Stinger, 

I felt the same way. I did find that dvdfab hd decrypter worked flawlessly the first time I ran it with Wine.  My method may not be the right way as I too am new but it worked. What I did was locate dvdfab in program files on my Windows HD and I right clicked the .exe and it gave me a choice to open with Wine and it worked to successfully make a back up copy. The problem I had was with DVD Shrink failing with one second remaining.

So I used K9copy and it worked after some fiddling around with it, see my post about how to use it, first post in this thread. I really likeK3B for burning, it is sweet.

Let us know what troubles you are having and we can work from there.

---

### Post by andrew.46 on 2007-07-30
Hi,

You have come across one of the problems that drove me from Feisty to Dapper:

> **MrKlean said:**
> I agree...but...I'm having trouble with devede since I switched to 7.04  : (  I get a movie made, but the sound is scratchy !!

Any thots would be appreciated !
thanks ; )

 The sound issue is well known bug with the Feisty Mplayer/Mencoder that has not been fixed. See the note for Feisty users:

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)

               Andrew

---

