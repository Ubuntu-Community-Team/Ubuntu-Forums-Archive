---
title: "monitor calibration???"
date: 2005-08-20
forum: Art &amp; Design
---

### Post by factotum218 on 2005-08-20
First to the Mods:
I posted a similar thread in Hoary Desktop, so feel free to delete that one if this forum seems more appropriate!

Im looking for a way to calibrate my monitor. This is the one thing holding me back from doing more work in Ubuntu instead of Windows. I have Photoshop running through wine at the moment, quite well actually.
Problem is that my windows system has been calibrated to match what is printed and also matches up quite well with the Pantone color system. Its dead on from what I can tell.

Anyone have a suggestion for calibrating my monitor? I checked in freshmeat.net for an app. and did try one, but for some reason I could not get it to run. I cant remember the name of it since it was uninstalled quite while ago, but I am looking for any suggestions!

---

### Post by Nigel Lew on 2005-08-20
Hi, great question. Im a linux noob so its all a bit vexing right now. I did however stumble across this  [http://www.pcbypaul.com/linux/monica.html](http://www.pcbypaul.com/linux/monica.html)

I will try to check it out as soon as I can...

hope that helps
Nigel

---

### Post by autocrosser on 2005-08-28
Well-I looked at Monica--only installs as sourcecode--you will need the fltk library & development set installed--do a Synaptic>search>fltk & select/download what you need----then install Monica as---cd in the terminal to /home/user name/Desktop/monica-3.3(I just drop the file on the open term after the cd)>make>sudo make install....It will be installed to your /usr directory. You can type monica in a terminal or use Smeg to add a launcher to the menu.

---

### Post by regeya on 2005-08-29
[QUOTE=Nigel Lew]Hi, great question. Im a linux noob so its all a bit vexing right now. I did however stumble across this  [http://www.pcbypaul.com/linux/monica.html](http://www.pcbypaul.com/linux/monica.html)

I will try to check it out as soon as I can...

hope that helps
Nigel[/QUOTE]

ROCK ON!  Must try this as soon as possible.  As I type this it's a bit late for me so tomorrow it is...

Thanks for posting a link to that.  I hope it works.

---

### Post by autocrosser on 2005-08-29
I used Monica to calibrate my Dual-head set--Using FBMerged with a ATI 9600Pro--Monica treats both monitors as one large screen--so my right monitor is slightly darker than the left--with a little fiddeling I got a fairly close match.

---

### Post by factotum218 on 2005-09-02
thanks for the info, works quite well. Thanks again!!

---

### Post by TroutMaskReplica on 2005-09-05
this only addresses calibration, which is only one component of colour management. the other is *profiling*. in mac os x i use a hardware colorimeter to profile my display to ensure what's on the screen matches what i see on press.

so i guess my question is, does Ubuntu or Linux in general have a way of dealing with ICC Color profiles (the standard for colour management in the graphics industry).

---

### Post by factotum218 on 2005-09-07
I have yet to see a hardware color profiler that works with linux

---

### Post by jasplund on 2005-09-18
At least linux is starting to get better with color management. Fortunately the Gimp will have icc support in the next version (2.4). 

EOG in breezy can handle icc profiles. However you have to apply a icc profile for your monitor. I don't know how to make a icc profile for my monitor. I guess I could do it in winXP but I don't have winXP on this computer. ANyone know about a profiling app that works with wine?

btw, take a look at:
[http://www.burtonini.com/blog/computers/xicc](http://www.burtonini.com/blog/computers/xicc)
[http://www.burtonini.com/computing/x-icc-profiles-spec-0.1.html](http://www.burtonini.com/computing/x-icc-profiles-spec-0.1.html)
[http://applications.linux.com/article.pl?sid=05/02/07/2244242&tid=47&tid=26&tid=7](http://applications.linux.com/article.pl?sid=05/02/07/2244242&tid=47&tid=26&tid=7)

---

### Post by Kiwilad on 2007-09-17
> **autocrosser said:**
> Well-I looked at Monica--only installs as sourcecode--you will need the fltk library & development set installed--do a Synaptic>search>fltk & select/download what you need----then install Monica as---cd in the terminal to /home/user name/Desktop/monica-3.3(I just drop the file on the open term after the cd)>make>sudo make install....It will be installed to your /usr directory. You can type monica in a terminal or use Smeg to add a launcher to the menu.

Ok, bearing in mind that I'm not that great with this stuff, can you please explain how to go through this setup in really basic lingo that I can understand. Step by step instructions would be great if possible

Many thanks

Stu

---

### Post by SreckoMicic on 2007-09-20
> **TroutMaskReplica said:**
> this only addresses calibration, which is only one component of colour management. the other is *profiling*. in mac os x i use a hardware colorimeter to profile my display to ensure what's on the screen matches what i see on press.

so i guess my question is, does Ubuntu or Linux in general have a way of dealing with ICC Color profiles (the standard for colour management in the graphics industry).

Yes I think it is. Look for Lprof in synaptic and see how it is managed!

Or read this: [Linux and Color managment]("http://en.wikipedia.org/wiki/Linux_color_management")

---

### Post by ropers on 2007-11-23
There now is a binary package, which should be much simpler to install for less technical people.

Go to [http://www.pcbypaul.com/software/monica.html](http://www.pcbypaul.com/software/monica.html) , download the binary package and extract the files. You can then immediately run the monica command you extracted, but if you want to install it for all users you can move the extracted monica file to /usr/bin . For this hiowever, you need to have root privileges. 

I hope this helps someone.

---

### Post by jcornuz on 2007-11-25
Hi there!

In order to load a monitor profile to your graphic card LUT table, you can use: xcalib or dispwin (part of ArgyllCMS).

Graphic programs that use a monitor profile in Linux include The Gimp, Cinepaint, Krita, RawStudio (experimental), Ufraw and RawTherapee (not open source).

In order to create the profiles, ArgyllCMS (command line utilities) and Lprof (GUI) support several calibration devices, including Colorvision Spyder (in development).

Check my blog down there for more info, links, detailed howtos....

Take care,

Joel

---

### Post by jespdj on 2007-11-27
GIMP version 2.4 indeed has some support for ICC color profiles. But I looked into the source code of GIMP and I was disappointed to see that support for color management is only very basic and very limited in GIMP 2.4.

Most operations in GIMP are hard-coded for sRGB. If you work with images that are not in sRGB, then GIMP will simply produce wrong results.
See for example [GIMP bug #499794](http://bugzilla.gnome.org/show_bug.cgi?id=499794).

So GIMP 2.4 is not suitable for a serious, color-managed workflow.

---

