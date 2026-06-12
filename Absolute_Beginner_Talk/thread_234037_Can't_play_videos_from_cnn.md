---
title: "Can't play videos from cnn"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-08-10
I have the latest version of firefox,totem and totem-xine and the totem-xine firfox plugin
When i try to play a video from cnn.com nothing comes up just a blank screen no video and no sound

---

### Post by TheRingmaster on 2006-08-10
don't use totem.

Install the Mplayer Plugin via synaptic.

It works great!

---

### Post by Fass on 2006-08-10
I feel like a prostitute for whoring out mplayerplug-in, but it really is the one I've found to work best with these sites.

It's in the repos and called "mozilla-mplayer." It plays the videos at CNN, and most other places, without problems for me.

---

### Post by lime4x4 on 2006-08-10
looks like it's already installed

john@ubuntu:~$ sudo apt-get install mozilla-mplayer
Password:
Reading package lists... Done
Building dependency tree... Done
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@ubuntu:~$

---

### Post by Fass on 2006-08-10
Uninstall the totem firefox plugin, or start firefox and go into "Edit - Preferences - Downloads - Download Actions - View & Edit Actions" and change the settings of the different video files to have them be handled by mplayerplug-in.

---

### Post by lime4x4 on 2006-08-10
okay did that for some reason there currently set to use windows media player pluggin.. Do u happen to know the exact path for the mozilla-pluggin?

---

### Post by Tehas on 2006-08-10
At first this didn't work.  I had to remove the Totem Firefox plug-in.  Once that was removed, the MPlayer plug-in worked like a charm.  Thanks!

---

### Post by lime4x4 on 2006-08-10
well i seemed to have really screwed something up..I removed a package called mplayer-pluggin now when i run this i get this error

john@ubuntu:~$ sudo apt-get install mozilla-myplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-myplayer
john@ubuntu:~$

---

### Post by junglepeanut on 2006-08-11
myplayer = mplayer

Also install plugin (or extension)

mediaplayerconnectivity

and 

videodownloader...for when above is blocked by bad java/flash saying need higher, need windows, etc pages.

---

### Post by lime4x4 on 2006-08-11
my bad...lol this is what i get now

john@ubuntu:~$ sudo apt-get install mozilla-mplayer
Password:
Reading package lists... Done
Building dependency tree... Done
Package mozilla-mplayer is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-mplayer has no installation candidate
john@ubuntu:~$


i also used synaptic for the following 2 packages but it doesn't find them
mediaplayerconnectivity

and

videodownloader

---

### Post by lime4x4 on 2006-08-11
also here is a copy of my source list

####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

#Dapper Backports (new software versions, provided by the Ubuntu Backports Project)


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse



deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
# deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
# deb [http://claws.sylpheed.org/ubuntu/dapper/](http://claws.sylpheed.org/ubuntu/dapper/) ./

---

### Post by Fass on 2006-08-11
You're missing the multiverse repos for dapper:

```
deb http://archive.ubuntu.com/ubuntu dapper multiverse
```

---

### Post by junglepeanut on 2006-08-12
Sorry forgot to mention they were firefox extension/plugins from the actual website. I.e. goto in firefox

tools->extensions->get more extensions

or 

the firefox website and download them.

I find them very helpful.
80% of the media plays with out needing them for me, but for the other twenty percent they are like magic tools.

---

### Post by pepolez on 2006-08-12
many codecs are not included with ubuntu by default for legal reasons.

automatix is very useful for getting codecs as well as a number of other useful things, see [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by lime4x4 on 2006-08-14
still doesn't play video on cnn i also noticed that when trying to view a wmv file from other sites it will only allow me to save it to my disk then i can play it just fine

---

### Post by arkangel on 2006-08-14
I have installed the mplayer plugin .  and seems to be working ... well not quite 

It shows me the screen  then it load the film ,  i have audio,  but not video
any idea ?

---

### Post by lime4x4 on 2006-08-15
here is a screenshot of what i get when trying to view videos on cnn

[http://lime4x4.pointclark.net:8888/cpg148/displayimage.php?album=random&cat=0&pos=-13](http://lime4x4.pointclark.net:8888/cpg148/displayimage.php?album=random&cat=0&pos=-13)

---

