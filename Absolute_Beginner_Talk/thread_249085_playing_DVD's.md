---
title: "playing DVD's"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-02
I want to play DVD's on my computer using xine but it keeps saying I have no MRL's ?   If I try it with Kaffeine or totem it says I don't have a plugin for dvd.

I have installed the AUD DVD codecs with Autmatix.  

Russty

---

### Post by jorn on 2006-09-02
You should really use VLC media-player. It playes most sorts of dvd's.
By the way, what are MRL's?

---

### Post by jorn on 2006-09-02
And you have installed the restricted codecs? Mrl seems to have something to do with xvid.

---

### Post by Russty of Oz on 2006-09-02
> **jorn said:**
> You should really use VLC media-player. It playes most sorts of dvd's.
By the way, what are MRL's?

VLC won't play DVD's either.  I have tried them all.

Restricted codecs??  Hmmm, I will have to see if I can find them.

---

### Post by RageAgainstThis on 2006-09-02
VLC should play dvds

apt-get install vlc

that should install all the needed files for video playback unless you have some sort of dvd i have not encountered.

---

### Post by Russty of Oz on 2006-09-02
> **RageAgainstThis said:**
> VLC should play dvds

apt-get install vlc

that should install all the needed files for video playback unless you have some sort of dvd i have not encountered.

I tried that and it said it was already installed, which it is.

Still won't play videos!

---

### Post by deadgobby on 2006-09-02
I use Ogle myself. It should be in the Synaptic. After install. Open up the Terminal and type in Ogle. The mouse is used to click on the menue screen. So like play the dvd, just click on the DVD screen play. Here is the info from Synaptic. I did as you did and could not get the DVD to play in Movie player or others. It work just fine in Ogle. Can't complain. 

Ogle is a DVD player with DVD menu support and some other useful
features like bookmarks, time skipping, multichannel audio,
and crop & zoom video and also:
    * Reads encrypted and unencrypted DVDs using libdvdread/libdvdcss.
    * Audio and subpicture selection.
    * Handles advanced subpicture commands such as fade/scroll and wipe.
    * Detects and uses correct aspect for movie and menus.
    * Fullscreen mode.
    * Screenshots with and without subpicture overlay.
    * Title/chapter search.
    * Supports different audio formats: AC-3, MPEG, LPCM (DTS
       only via SP/DIF).

It is yet under development and has some limitations. The
following are not yet implemented: reverse play,
angle selection during playback, karaoke mode and closed caption
support.

This is the vanilla version, with no special CPU support.  If you have
a recent i386 or powerpc, you will want to install the optimized package,
ogle-mmx or ogle-altivec respectively.

Homepage: [http://www.dtek.chalmers.se/groups/dvd/index.shtml](http://www.dtek.chalmers.se/groups/dvd/index.shtml)

---

### Post by bullgr on 2006-09-02
did you try to play commercial dvd's (movies)?
if yes, you must install libdvdread
go to synaptic search for libdvdread and install it...

---

### Post by jorn on 2006-09-02
>  
$ sudo apt-get install gstreamer0.8-plugins
$ sudo apt-get install w32codecs

If you havn't already installed them through Automatix.

Try starting vlc-mediaplayer or your prefered player in terminal to see the output. Example VLC:
> wxvlc

---

### Post by Russty of Oz on 2006-09-02
> **bullgr said:**
> did you try to play commercial dvd's (movies)?
if yes, you must install libdvdread
go to synaptic search for libdvdread and install it...

According to synaptic it is installed.

---

### Post by Russty of Oz on 2006-09-02
All my players, xine, vlc, totem etc will play other files, such as mpg and wmv but nothing will play DVD's, commercial or ones I have made myself from tv.

The gstreamer codecs and w32codecs are installed.  

There just seems to be something to do with DVD's that is missing.

Russty.

---

### Post by Russty of Oz on 2006-09-02
> **jorn said:**
> If you havn't already installed them through Automatix.

Try starting vlc-mediaplayer or your prefered player in terminal to see the output. Example VLC:

I did that and it says there is nothing to play!???  It works on windows on the same computer.

---

### Post by deadgobby on 2006-09-02
Have you tried Ogle Yet?

---

### Post by Russty of Oz on 2006-09-02
> **deadgobby said:**
> Have you tried Ogle Yet?

Oh, I forgot, I will try it now.

---

### Post by Russty of Oz on 2006-09-02
Nope!  Ogle won't play anything!  When I click Open Disc the whole thing closes.

There must be something I have not installed (or perhaps something I HAVE installed) which is causing the problem.  

Russty

---

### Post by bullgr on 2006-09-02
it's strange, with libdvdread installed you must able to play dvd's even in totem...

anyway... go there
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and follow the instructions, wathever need to install, alernate player's etc...

---

### Post by Russty of Oz on 2006-09-02
> **bullgr said:**
> it's strange, with libdvdread installed you must able to play dvd's even in totem...

anyway... go there
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and follow the instructions, wathever need to install, alernate player's etc...

AH!!!  That did it!  :D 

It was to do with the repository things.:redface:   I had to go through and enable all those multiverse thingies etc.  I didn't quite know what I was doing, but I enabled all of them and PRESTO! I can now play DVD's on all the players!

What a relief!!

Thank you to everone who replied.  =D> 

Russty  :)

---

### Post by bullgr on 2006-09-02
when you find the solution makes you happy, if you help someone to find the solution makes you more happy... :biggrin:

---

