---
title: "Is there a way to view Win. Media Player content?"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by drakebarimore on 2007-06-06
I am an absolute beginner to Linux.  I recently installed Ubuntu 7.04 fiesty fawn, but I have noticed that I run into a lot of problems whenever I try to view certain content on the web.  A few moments ago, I tried to watch the presidential debates which are posted on CNN.com.  Whenever I clicked on the link to play the video, it told me that the video was made to play in windows media player 9 (or something like that).  It gave me the option to upgrade or go ahead and try to play the content anyway, so I wasn't sure about upgrading and chose just to watch it anyway.  But the content could not be viewed.

I have had this problem on most of the streaming or video clip content that I have attempted to watch across most different web sites, like yahoo and youtube, to mention a few.

Does anyone know if I can make these different video sources (or even just one source like the CNN.com content) play correctly on Ubuntu?

---

### Post by zach12 on 2007-06-06
you could use vmware

---

### Post by drakebarimore on 2007-06-06
What is that?  How do I get it?

---

### Post by Papi-KB7VGW on 2007-06-06
Read this sticky How To.  It will help

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by drakebarimore on 2007-06-06
I read that and don't understand it.

---

### Post by diatribe on 2007-06-06
...It tells you exactly what to do...

---

### Post by drakebarimore on 2007-06-06
It may tell someone who is familiar with Ubuntu/Linux exactly what to do, but I do not know what a terminal or a text editor for example is.  So, it assumes that I know something that I don't as I have just started with Ubuntu.  : )

---

### Post by Papi-KB7VGW on 2007-06-06
ok, so try this.  Use >System>Admin>Synaptic Package Manager and search for win32 codecs.  I got all the Gstreamer and Mplayer installed that way.

---

### Post by steeleyuk on 2007-06-06
> **drakebarimore said:**
> It may tell someone who is familiar with Ubuntu/Linux exactly what to do, but I do not know what a terminal or a text editor for example is.  So, it assumes that I know something that I don't as I have just started with Ubuntu.  : )

Maybe you should try to stand up before you walk so to speak...

Have a play with the OS first, find out where things are and what you can do with them. Read the [Restricted Formats]("https://wiki.ubuntu.com/RestrictedFormats") page and other pages on the wiki. Have a search around the forum for other similar posts.

---

### Post by drakebarimore on 2007-06-06
Ok, I found that!

Here are some of the descriptions of some of the things that the search pulled up:

avifile-win32 plugin.
Win32 audio/video plugin for libavifile
This package provides a plugin for the avifile library to compress
and decompress audio video streams with the help of Win32 (i386)
DLL libraries (codecs). Default location for them is /usr/lib/win32.

NOTICE:
  Win32 codecs are NOT part of this package and have to be downloaded
  separately! See documentation or WWW pages for more details.

Homepage: [http://avifile.sourceforge.net](http://avifile.sourceforge.net)


heres another one:
Mplayer.

The Ultimate Movie Player For Linux
It plays most mpeg, avi and asf files, supported by many native and win32
DLL codecs. You can watch VCD, DVD and even DivX movies too. The other
big feature of mplayer is the wide range of supported output drivers. It
works with X11, Xv, DGA, OpenGL, SVGAlib, fbdev, but you can use SDL (and
this way all drivers of SDL) and some lowlevel card-specific drivers (for
Matrox/3dfx/SiS) too! Most of them supports software or hardware scaling,
so you can enjoy movies in fullscreen.

This version includes the Gtk GUI

Will either of these work ok?  Or does anyone suggest another from the list of search results when typing in "win32 codecs"?

---

### Post by fastpakr on 2007-06-06
Start with installing the multimedia codecs that were mentioned above.  I've paraphrased the info from the link you had trouble understanding:
_______________

Click 'Applications'
Click 'Add/Remove'
Under 'Search:' type 'gstreamer', then click 'Sound & Video' in the list on the left.
Mark the following for installation in the results list.
    * "GStreamer ffmpeg video plugin"
    * "GStreamer extra plugins"
    * "GStreamer plugins for aac, xvid, mpeg2, faad"
    * "GStreamer plugins for mms, wavpack, quicktime, musepack"
Click 'Other' in the list on the left, then scroll down to 'Ubuntu restricted extras' and mark it for installation.  Scroll up to 'Macromedia Flash plugin' and mark it as well.

Click 'Apply' and go through the steps to install the new applications.


Close Add/Remove and click 'Applications', then 'Accessories', then 'Terminal'.
At the command prompt, type 'gksudo gedit /etc/apt/sources.list'.
Paste the following into the file:
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 

Save and close the file.  Back at the command prompt, run this command:
'wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -'
Then run:
'sudo apt-get update'

Finally, run:
'sudo apt-get install libdvdcss2 w32codecs'

Type 'exit', hit Enter, and you're done.

---

### Post by zek725 on 2007-06-06
Get [Automatix.]("http://www.getautomatix.com") It is the best installer suited for beginners. It will simplify the above tasks.

---

### Post by drakebarimore on 2007-06-06
I was able to follow your instructions, but I did not get any of the following resluts:

* "GStreamer ffmpeg video plugin"
* "GStreamer extra plugins"
* "GStreamer plugins for aac, xvid, mpeg2, faad"
* "GStreamer plugins for mms, wavpack, quicktime, musepack"

The first three on the right hand side of the screen when, I search for "gstreamer" and select "sound and video," are as follows...

"Movie Player"
"CD Player"
"Recording Level Monitor"  followed by 5 more choices none of which start off "GStreamer."

---

### Post by Zzl1xndd on 2007-06-06
> **zek725 said:**
> Get [Automatix.]("http://www.getautomatix.com") It is the best installer suited for beginners. It will simplify the above tasks.

I hate to always say this but Using Automatix does make things simple for a new user at times but it often breaks the machine later on.

---

### Post by drakebarimore on 2007-06-06
Zek725

They seem to offer Automatix and Automatix2  Do you know which one would be best?  Automatix2 says that it allows you to run some windows programs.  Do you think this would be a good idea?

Thanks

---

### Post by zek725 on 2007-06-06
> **tweakedenigma said:**
> I hate to always say this but Using Automatix does make things simple for a new user at times but it often breaks the machine later on.

Oh I see. I just use it to install all I need to play videos and sounds and other browser plugins. :D

---

### Post by gentlemanmasher on 2007-06-06
I'm going to second the automatix even though many will steer you away from it.  It can cause errors and has for me in the past, but I would have not even gotten past the first week without some of the drivers supplied by automatix.  I was very confused moving from windows to ubuntu.  You expect everything to work like windows.


I no longer use automatix  but did when I was starting, now if you are wanting to learn how to use ubuntu and you don't need everything right away the forums are great, I have learned so much from everyone on here.

read the tutorials and ask specific questions, like where is the command line, what to do with the commands, most all the commands given from the command line are copy from the tutorial and paste into your command line.  You will learn to love it, I can't live without it anymore.

---

### Post by drakebarimore on 2007-06-06
tweakedenigma,  you think it would be best just to try and install the codecs?

---

### Post by drakebarimore on 2007-06-06
BTW, everything I try to click on (like installation) on the Automatix site says the follwoing:

Automatix Wiki has a problem

---

### Post by Zzl1xndd on 2007-06-06
> **drakebarimore said:**
> tweakedenigma,  you think it would be best just to try and install the codecs?

I do, not only is it not gonna break that system at some point you will learn more from it. But the others are right it can be a big help at first, just wanted to make sure you knew both sides.

---

### Post by drakebarimore on 2007-06-06
fastpakr

I was able to figgure out the instructions from fatpakr (I selected "all open source" from the right side menu.

I installed 3 of the ones that listed and now the video seems to play really well, but now I'm having a problem with no sound.

About the no sound problem I don't have sound across the board and it doesn't have anything to do with the video codecs.  I can't even get sound when ubuntu loads.  

My MB manufacturer (MSI) told me to try and update my bios by going to their website, but I didn't want to try that before asking if someone thought it would be alright.  I have been told that loading drivers with linux won't work that I simply have to set up all my hardware and boot ubuntu and it would just recognize everything and would work.

So, does anyone know of any reason that I shouldn't update my bios and will it work?

Thanks

---

### Post by fastpakr on 2007-06-06
> **drakebarimore said:**
> I was able to follow your instructions, but I did not get any of the following resluts:

* "GStreamer ffmpeg video plugin"
* "GStreamer extra plugins"
* "GStreamer plugins for aac, xvid, mpeg2, faad"
* "GStreamer plugins for mms, wavpack, quicktime, musepack"

The first three on the right hand side of the screen when, I search for "gstreamer" and select "sound and video," are as follows...

"Movie Player"
"CD Player"
"Recording Level Monitor"  followed by 5 more choices none of which start off "GStreamer."

Sorry - to the right of 'Search', click the option by 'Show' and select 'All available applications'.  That'll fix you right up.

You do NOT need automatix to do this, it's really just a couple of minutes worth of work to do it the 'proper' way.

---

### Post by zek725 on 2007-06-06
> **drakebarimore said:**
> BTW, everything I try to click on (like installation) on the Automatix site says the follwoing:

Automatix Wiki has a problem

Well, then Automatix has a problem. :D

Try this: [http://easylinux.info/wiki/Ubuntu:Feisty#Automatix2](http://easylinux.info/wiki/Ubuntu:Feisty#Automatix2) or [http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html](http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html)

---

### Post by gentlemanmasher on 2007-06-06
It does appear the automatix site is down.  Just download the .deb for edgy when the site's back up, but like I said it can be more fun hitting the forums and learning the best way to get things installed.

---

### Post by drakebarimore on 2007-06-06
The video plays now thanks to fastpakr.

Now I have a problem with no sound.

I think it may be resolved with a bios update, but I'm sorta scared to try it.  Does anyone know of any reason that I shouldn't try to update the bios while using linux?  Something that someone once told me about loading drivers with linux made me think that I couldn't update the mobo bios.

Thanks

---

### Post by gentlemanmasher on 2007-06-06
I would first see if your sound card is being detected.

---

