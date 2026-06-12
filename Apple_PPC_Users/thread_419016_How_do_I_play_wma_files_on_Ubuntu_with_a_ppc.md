---
title: "How do I play wma files on Ubuntu with a ppc?"
date: 2007-04-22
forum: Apple PPC Users
---

### Post by mindwalkernine on 2007-04-22
All I want to do is play the wma files using Ubuntu on my ppc.  How do I do this?

---

### Post by stmiller on 2007-04-22
Vlc.

---

### Post by engla on 2007-04-23
If you install enough gstreamer codecs rhythmbox will play wma files. I don't know exactly which packages though.

---

### Post by mindwalkernine on 2007-04-23
> **stmiller said:**
> Vlc.

I opened up terminal and did the install vlc thing.  It's now in my menu.  I opened my wma file.  no audio.  I let it play all the way through.  a couple of parts made a sound, but not enough of a blurb to even know if it part of the song I tried to play.

Is there some sort of update or something I need to do to it?

---

### Post by stmiller on 2007-04-23
Open VLC and go to 
Settings>Preferences>check advanced options>Audio>Output modules>ALSA audio output and click save. See if it works now.

---

### Post by mindwalkernine on 2007-04-24
> **stmiller said:**
> Open VLC and go to 
Settings>Preferences>check advanced options>Audio>Output modules>ALSA audio output and click save. See if it works now.

That doesn't seem to work.  I restarted the app after saving it too, still didn't.

---

### Post by mindwalkernine on 2007-04-24
> **engla said:**
> If you install enough gstreamer codecs rhythmbox will play wma files. I don't know exactly which packages though.

You wouldn't know if there is a terminal command line that would download this codes, would you.  I'd like to try to go try that route too.

---

### Post by mindwalkernine on 2007-04-24
> **stmiller said:**
> Open VLC and go to 
Settings>Preferences>check advanced options>Audio>Output modules>ALSA audio output and click save. See if it works now.

Oh, after looking around, I found out this is a wma2 file.  Does this make things different?

---

### Post by stmiller on 2007-04-24
[http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)

VLC should be able to do it. It plays back any wmv content that I've tried.

---

### Post by ssam on 2007-04-24
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by 3rdalbum on 2007-04-24
[https://shop.fluendo.com/](https://shop.fluendo.com/)

---

### Post by engla on 2007-04-24
I'd install all these:
gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
(from the wiki page) and try again. Install them with your favorite method (sudo aptitude install ... or synaptic)

---

### Post by marklar2u on 2007-04-24
I am new here to.  Just really got started a few weeks ago w/ 6.1 and now 7.04.


I am crossing the same bridges as you.  I had done some commands in following instructions for other software to enable / make aware the "update manager" of the software outside the normal/official packages...  search for multiverse and universe, 

Anyway, that being done, launch the Synaptic Package Manager.  Click on the "search" button.  Type VLC in, and all packages related to VLC show up.  Same thing works well for mPlayer.  When you choose one package, if it requires others to work it will warn/advise you and offer to mark the packages in question.  Further scan the titles and descriptions of other packages and pick relevant to your platform, your Ubu or Kubu, your processor/architecture, and most importantly, desired file types.

This is the blind leading the blind, but hope it works for you too.

---

### Post by mindwalkernine on 2007-04-24
> **engla said:**
> I'd install all these:
gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
(from the wiki page) and try again. Install them with your favorite method (sudo aptitude install ... or synaptic)

I tried, but I got this:

oem@ubuntu:~$ sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll
oem@ubuntu:~$

---

### Post by brunometal on 2007-04-24
the Medibuntu repositories have the ppc-codecs

[http://medibuntu.sos-sts.com/packages.php](http://medibuntu.sos-sts.com/packages.php)

---

### Post by SXR on 2007-04-25
Simple Awnser     Sudo apt-get vlc install  Make sure you habe universal packages enabled in symantic.  Google VLC PLAYER for the site it explains  it all in great detail there for you if you need the complete walk through.

---

### Post by mindwalkernine on 2007-04-25
> **SXR said:**
> Simple Awnser     Sudo apt-get vlc install  Make sure you habe universal packages enabled in symantic.  Google VLC PLAYER for the site it explains  it all in great detail there for you if you need the complete walk through.

Tried.

The first step...

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

I don't have to bang my head against the wall now, the wall is banging my head!

oem@ubuntu:~$ deb [http://mirror3.ubuntulinux.nl/](http://mirror3.ubuntulinux.nl/) dapper-seveas freenx
bash: deb: command not found
oem@ubuntu:~$

---

### Post by AndrewB on 2007-04-25
> **mindwalkernine said:**
> the wall is banging my head!

But how does it feel?


Seriously, through synaptic search for VLC
Choose to **instal**l VLC and the web plugin as well

Choose **apply**, this will include the dependencies

Let synaptic do its thing.....

Download a wmv file to your desktop.. right click on it 
, choose **open with** select VLC.. If VLC isn't there choose **"open with other application" **click **Add** type in **wxvlc** click **open**


Go to your downloaded wmv file and double click it. It should open and run in VLC now:popcorn:

---

### Post by stmiller on 2007-04-25
Anyone else want to make another post and say "vlc?" I think we need four or five more...

---

### Post by AndrewB on 2007-04-25
Seems that folk are still having problems getting set up.

[PHP]    sudo aptitude install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

[/PHP]
This is a command line install that should get most all codecs working.

There is more info here:[Ubuntu UN-OFFICIAL website]("http://medibuntu.sos-sts.com/") and [Here]("http://onlyubuntu.blogspot.com/2007/03/install-mplayer-and-multimedia-codecs.html")

---

### Post by sulobanks on 2007-04-26
If I remember correctly, w32codecs is not installable in ppc linux.  This may be where the missing piece is for mindwalkernine.  I rarely want to see video or flash on my comp (that's why I have the nice stereo and large TV screen), so it's not an issue for me.  But I do remember trying to play a few wmv files awhile back and I'm pretty sure I came to the conclusion that I would not be able to play them because w32codecs isn't available for ppc.  Might want to check me on that.  I'm not absolutely sure, but I'm pretty sure.

---

### Post by ubuntubrian on 2007-04-26
I am running Dapper on my TiBook G4 and can play .wmv and .wma files. I have the following plugins installed:
    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.25
And mPlayer plays the files just fine, audio and all.

    File name: libvlcplugin.so
    VLC multimedia plugin 
This is spotty playback on VLC, choppy sound.

In Firefox I have the mozilla-pluger plugin and get spotty playback in the browser.

---

