---
title: "Any internet radio that works??!!"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by swimm3r137@gmail.com on 2008-04-18
Hi,

I have a problem.  When I try to listen to online radio stations such as:
1) 1 fm
2) pandora
3) aol radio
4) yahoo radio

They don't work.  I know it's vague, but they worked in windows, but everytime I try to run them on these web sites, theres a error that comes up. (different depending on site obviously)

Any quick fix or solution?

---

### Post by spiderbatdad on 2008-04-18
I use streamtuner
Available in synbaptic package manager.

---

### Post by starcannon on 2008-04-18
> **spiderbatdad said:**
> I use streamtuner
Available in synbaptic package manager.

I use Streamtuner as well, its the best of the lot, stick with Shoutcast tab for best results.

---

### Post by swimm3r137@gmail.com on 2008-04-18
I attempted to use shoutcast, and I get the same error(s) over and over again:
"Unable to tune in

Failed to execute child process "xmms" (no such file or directory)."

OR

Uunable to tune it-Stream is empty


WTF?

---

### Post by starcannon on 2008-04-18
Open up synaptic package manager, search for xmms:

Install xmms (not xmms2)
install xmms live-ice
install lame (mp3 encoder/decoder)
look through the xmms stuff grab any thing else there you think you'd like.

note xmms is pretty much winamp for linux

cheers,
Starcannon

---

### Post by robalcorn on 2008-04-18
I found that MoviePlayer works great

---

### Post by spiderbatdad on 2008-04-18
Edit>>preferences
make sure applications is highlighted on the left...
scroll through and where you see xmms %q...double click the line. Delete xmms and put in totem...if that is your music player...see screenshot below.

If you want to use streamripper to record streamtuner...sudo apt-get install streamripper and add
-d /mnt.Data01/Ripped -r -q to the end of the record a stream line...screenshot 2.

---

### Post by LeoSolaris on 2008-04-18
I like BPMx myself. I haven't had any real issues with it, but I am not a music guy, so I do not really stretch its limits.

Leo

---

### Post by swimm3r137@gmail.com on 2008-04-18
> **starcannon said:**
> Open up synaptic package manager, search for xmms:

Install xmms (not xmms2)
install xmms live-ice
install lame (mp3 encoder/decoder)
look through the xmms stuff grab any thing else there you think you'd like.

note xmms is pretty much winamp for linux

cheers,
Starcannon

When I search for xmms, theres LOTS of files/packages that comes up.  Which 1 do I choose?  PLease not, I'm using the 8.04beta incase that makes any difference.  THeres alot of xmms2 packages, so I dunno.  I know you said install the xmms one (NOT xmms2), but I'm not surewhich 1 to install cuz theres lots.  Thanks

---

### Post by starcannon on 2008-04-18
You can either search for xmms-liveice or open a terminal and type:
```
sudo apt-get install xmms-liveice
```

either way you do the install, it will grab xmms and any other dependencies for you, be sure to go through all the xmms packages later, lots of really cool stuff (i'm a goom fan fun to watch and space on while listening to music, theres also a handy dandy wma codec in the xmms stuff as well as a bunch of other really neat stuff :) ) let us know how you make out.

Cheers,
Starcannon

ps if you haven't done so be sure to:
```
sudo apt-get install lame
```
as well.

---

### Post by Whiffle on 2008-04-19
For pandora you need to have flash installed.

---

### Post by swimm3r137@gmail.com on 2008-04-19
> **Whiffle said:**
> For pandora you need to have flash installed.

speaking of flash....  When I go to the adobe site- [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

It seems to automatically know I'm using linux OS (which is good!).  BUT, under "version," which one should I download?  The options are:
1) .tar.gz for linux
2) .rpm for linux
3) YUM for linux

ps- sorry im such a newb

---

### Post by starcannon on 2008-04-19
I believe the flash plugin s in the restricted extras package already:
```
sudo apt-get install ubuntu-restricted-extras
```

It also includes several other packages that are good to have, java, some fonts, lame encoder, etc...

Oh, did you get Streamtuner working?

---

### Post by swimm3r137@gmail.com on 2008-04-19
Oh, did you get Streamtuner working?[/QUOTE]

Unfortunately, no.  This is what happened when I did sudo apt-get install xmms-liveice in the terminal.  Do you think it has something to do with the fact that I have 8.04 beta vs 7.10?  I have no idea lol.  I kinda just gave up, considering I can't even get past this point unless you can help me :)

alex@ubuntu:~$ sudo apt-get install xmms-liveice
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xmms-liveice
alex@ubuntu:~$

---

### Post by starcannon on 2008-04-19
search for xmms-liveice in synaptic, I'm not using 8.04 yet, its still beta.

---

### Post by swimm3r137@gmail.com on 2008-04-19
no package is found.....

---

### Post by kenny1948 on 2008-04-30
> **starcannon said:**
> Open up synaptic package manager, search for xmms:

Install xmms (not xmms2)
install xmms live-ice
install lame (mp3 encoder/decoder)
look through the xmms stuff grab any thing else there you think you'd like.

note xmms is pretty much winamp for linux

cheers,
Starcannon

Tried finding these, but they're not there. Only xmms2

I just updated to 8.04 and now cannot listen to internet radio. Have tried Helix Player ( cannot install ) MPlayer and nothing works. I am frustrated. 
With Gutsy they all worked no problem. 
This is with an external player--that is what will not work.:confused:
screenshot attached

---

### Post by DirtDawg on 2008-04-30
For whatever reason, XMMS has been removed from the 8.04 repos.

But [here are links to XMMS Hardy Debs.]("http://ubuntuforums.org/showthread.php?t=774461")

EDIT: I could not find xmms-liveice in the link I provided. Hopefully, you can find it elsewhere. Good luck.

---

### Post by bilal.17 on 2008-04-30
streamtuner works great

---

