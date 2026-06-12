---
title: "I keep on forgetting how to do this"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by -gabe-noob- on 2008-01-21
How can I install flash player, I know its stupid but I keep on forgetting how to do it when I download a new distro,

---

### Post by jleaker01z on 2008-01-21
Are you using 32 bit Ubuntu or 64 bit?  It makes a difference.

32 bit can be installed via Applications>Add/Remove.  Just search for Flash.  64 bit is another story, it has to be installed via script I believe.  (I use 32 bit so not totally sure)

---

### Post by Het Irv on 2008-01-21
you need the_ Ubuntu restricted extras_ package in add remove programs.
If 64-bit click the link in my sig (Great Backup Program).  It will install 32&64 bit Flash plus alot of other things

---

### Post by -gabe-noob- on 2008-01-21
32 bit, and I've never used that app you put in, dont see why I need to

You guys know I'm talking about the flash player for youtube videos and stuff....right?

---

### Post by PmDematagoda on 2008-01-21
There is not much of a difficulty in installing Flash on Ubuntu 7.10 x64 as it was on Ubuntu 7.04 x64, you can install it simply by executing:-
```
sudo apt-get install flashplugin-nonfree
```

P.S. This applies to Ubuntu 32 bit as well:).

---

### Post by jleaker01z on 2008-01-21
> **-gabe-noob- said:**
> 32 bit, and I've never used that app you put in, dont see why I need to

You guys know I'm talking about the flash player for youtube videos and stuff....right?

Yes...install the Flash plugin via Applications>Add/Remove

---

### Post by Saint Angeles on 2008-01-21
the best way is to go to [www.adobe.com](www.adobe.com) and find the "get flash player" link

save the ad...tar.gz file and extract it to your desktop.

in a terminal, navigate to the folder and type: sh flash[tab]

this has always worked for me

---

### Post by -gabe-noob- on 2008-01-21
you can do it in add/remove?

I've always done it the way the guy above me said to

---

### Post by zabien1970 on 2008-01-21
I just reinstalled and when I went to a site that needed it a yellow bar appeared at top (in firefox) and said additional plugins are required, when I clicked on it it allowed my to install flash

---

### Post by PmDematagoda on 2008-01-21
> you can do it in add/remove?

No, you will have to do it either through apt-get or Synaptic.

---

### Post by jleaker01z on 2008-01-21
> **-gabe-noob- said:**
> you can do it in add/remove?

I've always done it the way the guy above me said to

Yes.  I know most people when you ask for help on here will give you a command to enter into a terminal.  There are several reasons for this, its easier and faster for us, and it will work regardless of what desktop you use or how it is customized.

The Add/Remove option is easier for the user, but if you use KDE or XFCE it may not be located in the same place.  I always give Gnome options as that is the default desktop for Ubuntu.

---

### Post by Het Irv on 2008-01-21
> **-gabe-noob- said:**
> 32 bit, and I've never used that app you put in, dont see why I need to

You guys know I'm talking about the flash player for youtube videos and stuff....right?
I ran across the app when I was looking for a way to back-up my Linux stuff.  It is very good for building a Ubuntu computer.  Not only does it back-up stuff but it also installs many of the common programs and plug-ins

---

### Post by jleaker01z on 2008-01-21
> **PmDematagoda said:**
> No, you will have to do it either through apt-get or Synaptic.

I installed it via Add/Remove, and have instructed several others to do the same who reported it worked fine for them.

---

### Post by -gabe-noob- on 2008-01-21
the sudo apt-get install didn't work i mean it installed, but its not IN firefox yet...
I forget how to navigate to the file :P!

---

### Post by omi291 on 2008-01-21
go to this link:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux)

and download the tar.gz file. Extract it, and using the terminal, change the directory to the location of the new file. Then, just type this in the terminal, and the installation will be complete:

./flashplayer-installer

It worked for me...

---

### Post by -gabe-noob- on 2008-01-21
(I know this is SUPER nubish) but how do I change directories?

---

### Post by zabien1970 on 2008-01-21
> **-gabe-noob- said:**
> (I know this is SUPER nubish) but how do I change directories?

In the terminal its cd

---

