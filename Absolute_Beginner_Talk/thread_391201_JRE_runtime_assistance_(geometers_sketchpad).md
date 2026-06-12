---
title: "JRE runtime assistance (geometers sketchpad)"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by godd4242 on 2007-03-22
Alright everyone.
I messed up.

You see, I need a certain program, the [Geometers sketchpad.]("http://www.dynamicgeometry.com/javasketchpad/download_center.php")
For school.
Now when I switched over to Ubuntu, I never even thought about saving this thing to my lil USB drive that I used to transfer all the *really important stuff*, for example my music.

Now the above link, looks like the best replacement possible
If anyone knows of FOSS replacements, (which I haven't been able to find) I'll gladly take one of those.
The .exe is untested in WINE, and qkSEM or some weird emulator with a name like that that runs windows xp is said to only be available on Feisty.
Gee how handy.

So two ideas for this thread.
Open source geometers sketchpad replacements, 
or[here]("http://java.com/en/download/help/5000010500.xml#selfextracting")
ways I can get that above link to work on my Ubuntu Edgy lappie.

Thanks in advance all.

EDIT: 
Alright first things first I need JRE installed, which at the moment I can't figure out how to do
The instructions on the website turn out to command not found in Ubuntu
link [Is here]("http://java.com/en/download/help/5000010500.xml#selfextracting")
So tips or advice on that would be nice also...

---

### Post by dhtseany on 2007-03-23
Ok I'm not familiar with the first part but I can at least help you install Java:

Go into terminal and type:

```
$ sudo apt-get install sun-java6-jdk
```

Let me know if that install its. If not I have a different method you can try.

Sean

---

### Post by godd4242 on 2007-03-23
> **dhtseany said:**
> Ok I'm not familiar with the first part but I can at least help you install Java:

Go into terminal and type:

```
$ sudo apt-get install sun-java6-jdk
```

Let me know if that install its. If not I have a different method you can try.

Sean

```

E: Couldn't find package sun-java6-jdk
```

The install guide says distros support:
Redhat 
SuSE
and one more but that one isn't debian.

So I'm really stumped here.

The WINE solution looks tempting however.

---

### Post by camz on 2007-03-23
Dude you can install Java Runtime Environment from the Add/Remove Menu in Applications. It's ver. 5.0. I don't really get the problem so I could be completely off the point but I hope I did manage to help.

---

### Post by dhtseany on 2007-03-23
Trust me, there is Java on Ubuntu :)

I'm having a hard time remembering if these had to be added to get java but it won't hurt to add them:



```

$ su root
*Password:*
$ gedit /etc/apt/sources.list 
```

Add the following lines:

```

deb ftp://ftp.videolan.org/pub/videolan/ubuntu dapper universe
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse

```

Save, and exit. Then you need to update the list:

```
$ sudo apt-get update
```

Then:

```
$ sudo apt-get install sun-java5-jdk 
```

From there you should be good to go. Let me know if all is well!:)

Sean

---

### Post by godd4242 on 2007-03-23
> **camz said:**
> Dude you can install Java Runtime Environment from the Add/Remove Menu in Applications. It's ver. 5.0. I don't really get the problem so I could be completely off the point but I hope I did manage to help.

Haha.
I guess that teaches me a lesson about looking through the easiest answers first huh?
Thanks that worked for JRE, testing now as to whether or not I can get GSP working now or not.

Thanks again :3

---

### Post by godd4242 on 2007-03-23
> **dhtseany said:**
> Trust me, there is Java on Ubuntu :)

I'm having a hard time remembering if these had to be added to get java but it won't hurt to add them:



```

$ su root
*Password:*
$ gedit /etc/apt/sources.list 
```

Add the following lines:

```

deb ftp://ftp.videolan.org/pub/videolan/ubuntu dapper universe
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse

```

```
$ sudo apt-get install sun-java5-jdk 
```

From there you should be good to go. Let me know if all is well!:)

Sean

For some reason my sources.list only opens as read only, even though I'm logged in as root.

Secondly, why do I need the Videolan.org repo, unless they do something other than VLC which i don't know about.
And finally, why the dapper main restricted? I'm running edgy at the moment ;_;

EDIT:
It looks like the program I found is only a webapplet creator for displaying GSP creations.
I'm almost positive infact.

So thread hijack.

FOSS solutions to GSP 
and / or
Getting GSP.exe to work off of an install CD in WINE

Any help, would be greatly appreciated.
Thanks all.
If you want any Beryl help I think I could pay you back in that :3

---

### Post by theproc64 on 2008-01-13
Geo sketchpad works great in wine except that it is a little slow.  Just install wine (sudo apt-get install wine) and pop in the cd.  Then go to the sketchpad folder in the cd and click on the .exe file.  It runs fine for me.

---

### Post by theproc64 on 2008-02-12
Does anyone have ideas for geosketchpad replacements?  I've tried Kig and it doesn't have enough features to fit my needs (hiding points, transformations are confusing).  I don't really like running it in wine because it runs slowly.  Any ideas?

---

### Post by darkdud on 2008-03-03
I just sent this out to our Math teachers this morning.  Figured I would share the wealth here as well:

--------------------
GEOGEBRA
--------------------
You have probably heard me promote the FREE java based Geogebra.ORG software, there are many reasons to migrate your use from the equally excellent Geometer's Sketchpad to a Free alternative.  
  *  [http://www.geogebra.org](http://www.geogebra.org)

One, reduce the Cost to our district to purchase a large amount of licenses.  But MOST IMPORTANTLY is that the students can use THE SAME software at home or at school.

There are many resources available as well for Middle School:
  *  [http://www.geogebra.org/en/wiki/index.php/English#Math:_Middle_School](http://www.geogebra.org/en/wiki/index.php/English#Math:_Middle_School)
  *  [http://teachers.henrico.k12.va.us/math/GeoGebra_Site/](http://teachers.henrico.k12.va.us/math/GeoGebra_Site/)

Just visit the website and click on the "Java webstart" to start the program.  I'm still looking for a way to convert Geometer's Sketchpad files to Geogebra .GGB files.

--------------------
CPMP TOOLS
--------------------
Another similar (and FREE) Geometry resource is CPMP tools.  This runs with Java as well, so you can just click on the download link and quickly start the program.
  *  [http://www.wmich.edu/cpmp/CPMP-Tools/](http://www.wmich.edu/cpmp/CPMP-Tools/)

There are many useful aspect to this tool, but of particular interest is exploring the 4 triangle congruence theorems (SSS, SAS, AAS, ASA) under:
     Geometry -> Triangle Congruence

--------------------
Geometry Constructions
--------------------
Okay, now that you have some software, what else can you do with it.  Take a tip from the master (Euclid) and see if your students can reconstruct the basic constructions from "The Elements"

Propositions 1, 9-12, 15, 23  (3 and especially 2 are REALLY tough to understand, for beginners, so just skip these)
  *  [http://aleph0.clarku.edu/~djoyce/java/elements/bookI/bookI.html#props](http://aleph0.clarku.edu/~djoyce/java/elements/bookI/bookI.html#props)

Another more pictorial version of the above with links to these both versions of the constructions
  *  [http://www.sunsite.ubc.ca/DigitalMathArchive/Euclid/bookI/bookI.html](http://www.sunsite.ubc.ca/DigitalMathArchive/Euclid/bookI/bookI.html)

-----------------------------------------------
3 GREAT tools, all FREE and all available to engage student learning

---

