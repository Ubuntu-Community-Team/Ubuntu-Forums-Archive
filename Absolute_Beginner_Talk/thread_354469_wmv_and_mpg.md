---
title: "wmv and mpg"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-02-06
The default video player does not play mpg or wmv files. I get a message sating I may need plugins. How do I get the plug-ins? Would I be better off getting a different player?

---

### Post by aysiu on 2007-02-06
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by riven0 on 2007-02-06
Okay, first go to System >> Administration >> Synaptic package manager >> Settings >> Repositories. Now make sure everything under Internet is checked off. Then click OK and Reload. Now close Synaptic, open the terminal and run this command:

> sudo apt-get install mpg123 mpg123-alsa gstreamer0.10-alsa gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.8-dvd gstreamer0.8-mpeg2dec libdvdread3 && sudo /usr/share/doc/libdvdread3/./install-css.sh

---

### Post by aysiu on 2007-02-06
By the way *run this command* is another way of saying *copy and paste this command into the terminal to save yourself the trouble of retyping it and possibly messing up*.

---

### Post by paydaydaddy on 2007-02-06
> **riven0 said:**
> Okay, first go to System >> Administration >> Synaptic package manager >> Settings >> Repositories. Now make sure everything under Internet is checked off. Then click OK and Reload. Now close Synaptic, open the terminal and run this command:

Ran this command and got this message:
Reading package lists... Done
Building dependency tree... Done
Note, selecting mpg321 instead of mpg123
E: Couldn't find package mpg123-alsa

I'll check out some files and see if they play.

---

### Post by paydaydaddy on 2007-02-06
get the same message for both mpg and wmv:

You do not have a decoder installed to handle this file. You might need to install the necessary plugins.

---

### Post by Rui Pais on 2007-02-06
hi,
maybe giving [automatix]("http://www.getautomatix.com/index.html") a try would be the easiest way...

---

### Post by paydaydaddy on 2007-02-06
I'm getting closer. I can now play mpgs but the mwv acts like it is playing but only gives a black screen. I read something about windows codecs and there seemed to be a link but it would not open.

---

### Post by Scarlett on 2007-02-06
I'd be interested to know if there's a fix for this too.

WMVs used to work when I was using Dapper with 32bit Firefox but now I've got Edgy with 64bit FF and they don't work anymore.  I've installed every codec I could find and probably a lot that don't  even have anything to do with Mplayer, RealPlayer, Win32 or video in general.  I have a feeling it has something to do with that 64bit thing.  I really had to shoe-horn it in to get it to work.

---

### Post by dr_d on 2007-02-06
use vlc... it plays almost everything

---

### Post by Rui Pais on 2007-02-06
> **Scarlett said:**
> I'd be interested to know if there's a fix for this too.

WMVs used to work when I was using Dapper with 32bit Firefox but now I've got Edgy with 64bit FF and they don't work anymore.  I've installed every codec I could find and probably a lot that don't  even have anything to do with Mplayer, RealPlayer, Win32 or video in general.  I have a feeling it has something to do with that 64bit thing.  I really had to shoe-horn it in to get it to work.

window codecs are 32bits and will only work on 64bit with a 32bit multimedia frontend. They fail on totem or kaffeine or firefox for 64bit. 
Try to add to your sources:
> deb [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) edgy misc multimedia
and apt-get they mplayer. It should play everything on 64bit.

---

### Post by atihimself on 2007-02-06
Why don't you get vlc or mplayer 
sudo apt-get update && sudo apt-get install mplayer
and you need win32 codecs also, it worked for me

---

### Post by Scarlett on 2007-02-06
Even embedded media?  

If so, how do I set it to default?  I had to get rid of Totem because it wanted to be the default originally and it wouldn't play anything.  Mplayer at least plays *almost* everything I need.

---

### Post by Scarlett on 2007-02-06
> **Rui Pais said:**
> window codecs are 32bits and will only work on 64bit with a 32bit multimedia frontend. They fail on totem or kaffeine or firefox for 64bit. 
Try to add to your sources:

and apt-get they mplayer. It should play everything on 64bit.

You are my hero!  Thank you!!!

---

