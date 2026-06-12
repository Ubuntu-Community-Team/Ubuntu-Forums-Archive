---
title: "cant burn to cd"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by maitresse on 2007-06-17
I am a total noob!!!  I know nothing about what I am doing half the time!

Here is my problem.  No matter which burning thing i use, either nautilus, or gnomebaker, it keeps asking me to insert a blank cd.  I have been through a whole pack wondering what is wrong with them!  Also, it won't let me use mp3 files.  They have to be ogg.  This is making no sense to me!  Anyone know what I am on about?!!!

---

### Post by machoo02 on 2007-06-17
> **maitresse said:**
> I am a total noob!!!  I know nothing about what I am doing half the time!

Here is my problem.  No matter which burning thing i use, either nautilus, or gnomebaker, it keeps asking me to insert a blank cd.  I have been through a whole pack wondering what is wrong with them!  Also, it won't let me use mp3 files.  They have to be ogg.  This is making no sense to me!  Anyone know what I am on about?!!!

Well, for starters you might want to install something like [K3B]("http://k3b.plainblack.com/") as it is *the* most full featured cd/dvd burning application for Linux.  

As for your .mp3 problem..have you installed the codecs required for .mp3 files?

---

### Post by maitresse on 2007-06-17
i have tried to download k3b. it is on my archive manager, but now i have no idea what do to with it!  HELP!!!

---

### Post by forestpixie on 2007-06-17
I you do install K3B and you're likely to burn an audio cd from mp3 you'll need the libk3b2-mp3 package as well.

:)

---

### Post by forestpixie on 2007-06-17
Have you downloaded/installed it?

---

### Post by maitresse on 2007-06-17
and where do i get this from? someone help me out here.......please! lol

---

### Post by dptxp on 2007-06-17
How do I encode WAV to mp3 ? I use Wavepad in Windows, legally free, I think it uses LAME encoder.

---

### Post by maitresse on 2007-06-17
i have downloaded k3b, but i dont have any idea what to do to install it!

---

### Post by forestpixie on 2007-06-17
ok did you get from synaptic?

---

### Post by dptxp on 2007-06-17
Use Add/Remove to install.
It will download and install.

---

### Post by maitresse on 2007-06-17
no. i didnt get it from synaptic.  when i tried that, i got this

k3b:
 Depends: k3blibs but it is not going to be installed
 Depends: kdelibs4c2 but it is not going to be installed
 Depends: libdbus-1-1 but it is not going to be installed
 Depends: libdbus-qt-1-1c2 but it is not going to be installed
 Depends: libmusicbrainz4c2 but it is not going to be installed
 Depends: kdebase-bin but it is not going to be installed
 Depends: kcontrol but it is not going to be installed



i downloaded if from sourceforge

---

### Post by forestpixie on 2007-06-17
easier in synaptic you can the other package at the same time.

---

### Post by maitresse on 2007-06-17
> **dptxp said:**
> Use Add/Remove to install.
It will download and install.

dont even mention that!  i cant use my add/remove.  i get this message when i try to use that!


Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

---

### Post by forestpixie on 2007-06-17
system>admin>synaptic 

search for K3B

mark for installation and away it'll go!

and do the libk3b2-mp3 package

---

### Post by maitresse on 2007-06-17
it wont let me download it from synaptic.

---

### Post by dptxp on 2007-06-17
Select the best server in preferences at bottom left in add/remove.

---

### Post by forestpixie on 2007-06-17
yes got that - you gonna need to get that sorted first then I'd say. 

You're gonna need to get you /etc/apt/sources sorted first.

---

### Post by maitresse on 2007-06-17
I am getting all sorts of messages, but i definately cant download it from synaptic!

---

### Post by maitresse on 2007-06-17
> **forestpixie said:**
> yes got that - you gonna need to get that sorted first then I'd say. 

You're gonna need to get you /etc/apt/sources sorted first.

any idea how? :(

---

### Post by forestpixie on 2007-06-17
Not completely sure but if you can post it here it might help

I'm assuming your in Ubuntu

in a terminal do 

```

gedit /etc/apt/sources.list
```

then copy that into a post

---

### Post by maitresse on 2007-06-17
> **forestpixie said:**
> Not completely sure but if you can post it here it might help

in a terminal
assume your in Ubuntu

in a terminal do 
```

gedit /etc/apt/sources.list
```

then copy that into a post

thanks forestpixie.  I will try that!  look out for what everyone says!

---

### Post by forestpixie on 2007-06-17
Further - got this from a thread - all help herein from taurus!

Close Add/Remove first. Then, post the output of these two commands from a terminal.

Applications -> Accessories -> Terminal


```
sudo apt-get update
sudo apt-get upgrade
```

this is the thread 

[http://ubuntuforums.org/showthread.php?t=471226](http://ubuntuforums.org/showthread.php?t=471226)

It appears that there is something awry with your sources.list

Once that's sorted the K3B thing will be easy!

:D

---

### Post by maitresse on 2007-06-17
i thought it was all sorted, but it aint!!

I now have gnomebaker, k3b and every one of the cd burners you could think of, and not one of them is working!  They all keep asking me to insert a blank disc, and when i do, they keep asking!!!!!

HELP!!!

---

### Post by dptxp on 2007-06-18
> **maitresse said:**
> i thought it was all sorted, but it aint!!

I now have gnomebaker, k3b and every one of the cd burners you could think of, and not one of them is working!  They all keep asking me to insert a blank disc, and when i do, they keep asking!!!!!

HELP!!!

Have you opened 'preferences' in add/remove' and selected 'custom server' to choose the best server ?
Your add/remove may work after that.

---

