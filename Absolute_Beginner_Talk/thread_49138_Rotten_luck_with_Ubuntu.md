---
title: "Rotten luck with Ubuntu"
date: 2005-07-15
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-15
After many hours of installing and adding apps, I finally had a nice sytem going, although it lacked MANY basics. So last night when I shut down, I noticed my PC has restarted into the CLI. And guess what???

I cannot get Xwindows running. My original nemises..... Now I am re-installing the whole darn CD, again. 

Is'nt there a way to re-install just the xwindows bit? I get a few dependecies that goes missing. I have my cd's listed in the sources list, but for some silly reason the files is not extracted from cd. I've done the update as well...

But better still. I think I should go for Debian as a boot as well. I have ten CD's for Debian and there is a lot more files added to my sourdes without going to internet. So far I managed to get most thingies like my printer working from the Debian cd's, but last night I did an automatic update in Synaptic. I think that was why my system went haywire. I've never before did an auto update, and not once did my system fail.

---

### Post by ubuntu_demon on 2005-07-15
to install all packages that are installed by default :

$ sudo apt-get install ubuntu-base ubuntu-desktop

$ sudo dpkg-reconfigure xserver-xorg
is the way to reconfigure your X. (just press enter when you don't know something and choose simple for your monitor configuration)

to get multimedia codecs and find anwsers to most basic questions go to : [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by GrootBrak on 2005-07-15
> sudo apt-get install ubuntu-base ubuntu-desktop

Worked, but there is missing dependencies
gnomemeeting
gstreamer0.8-sdl
rss-glx

And they have other dependencies.
libsdl1.2debian
libsdl1.2debian-nas
libsmpeg0

And I cannot find them all in the indexes. I do not yet have internet because of missing bluetooth.

Is there any way I can get the files back from the CD? It *should* be there cause it was working.


> sudo dpkg-reconfigure xserver-xorg

No xserver-org installed. Eish, I'm net getting anywhere.
As a boogy price, I can get into my desktop when I select "Gnome failsafe", but it won't give me much scope to work with.

---

### Post by ubuntu_demon on 2005-07-17
Make sure the first line in your /etc/apt/sources.list regarding the cd-rom is uncommented (sudo gedit /etc/apt/sources.list)

do :

sudo apt-get install -f
this will (try) to solve missing dependencies and stuff

You might also want to update your sources.list with the one from ubuntuguide to be able to install multimedia codecs

---

### Post by poofyhairguy on 2005-07-17
[QUOTE=GrootBrak]So far I managed to get most thingies like my printer working from the Debian cd's, but last night I did an automatic update in Synaptic. .[/QUOTE]

Debian plain lacks Xorg. SO when you auto-updated with the Debian CDs it stripped away Xorg. Good by display.

That is why you shouldn't use Debian CDs on Ubuntu, they are different.

I hate to be a dick and say I told you so...but....

[http://www.ubuntuforums.org/showpost.php?p=250535&postcount=2](http://www.ubuntuforums.org/showpost.php?p=250535&postcount=2)

Just please know that you are having bad luck with a mutt mix of Debian and Ubuntu....not Ubuntu itself.

My old recommendation still stands.

---

