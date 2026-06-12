---
title: "[SOLVED] Media Players Closes When Playing Media Files"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by kolisikepu on 2008-04-01
When ever I open up a media file, whether it MP3 or any videos, any player will open (as if it will play it) and then it will close.  It's frustrating me!!  I don't get a bit of the song or movie it will just close.

Any idea's community?

I did see one post that was resolved, but it didn't give any hints as to how it was fixed.  It fixed itself.

---

### Post by taavikko on 2008-04-01
Start the player in command line 
till e.x ```
kaffeine
```
And paste the error message, if any.

---

### Post by kolisikepu on 2008-04-01
> **taavikko said:**
> Start the player in command line 
till e.x ```
kaffeine
```
And paste the error message, if any.

I can open the players with no issues.  As soon as I open a media file, whether I open it straight from the directory or open from within the players, it closes.

Is it possible to capture what it is doing when I open an app in the terminal and then open a file within the terminal?

---

### Post by aeiah on 2008-04-01
you should be able to just type kaffiene song.mp3 in the terminal and it'll start playing it (or not as the case may be) and give you error messages.

i know that mplayer will do this pretty easily anyway. gmplayer /path/to/video.avi will launch the normal mplayer movie player and play the video (mplayer will play the command line version of mplayer. it shouldnt make a difference for tracking the error though)

if it comes up with nothing you could use a flag for the verbosity level:

mplayer -verbose=4 /path/to/video.avi

---

### Post by taavikko on 2008-04-01
> **kolisikepu said:**
> I can open the players with no issues.  As soon as I open a media file, whether I open it straight from the directory or open from within the players, it closes.

Is it possible to capture what it is doing when I open an app in the terminal and then open a file within the terminal?

The idea when opening application in terminal, that it outputs everything it does, so when opening mp3 in application started in terminal, you should be able to see errors.

And youre able to start playing mp3 like typing
```
kaffeine /media/music/britney-spears.mp3
```

BTW, have you installed codecs for playing mp3?

---

### Post by kolisikepu on 2008-04-01
OK... here's the output I get when I try and play with mplayer.

```
kolisikepu@matrix-linuxacer:~/Desktop$ gmplayer /Michael Buble - Everything.mp3
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU          540  @ 1.86GHz (Family: 6, Model: 22, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /Michael.
File not found: '/Michael'
Failed to open /Michael.


Playing /home/kolisikepu/Desktop/Buble.
File not found: '/home/kolisikepu/Desktop/Buble'
Failed to open /home/kolisikepu/Desktop/Buble.


Playing /home/kolisikepu/Desktop/-.
File not found: '/home/kolisikepu/Desktop/-'
Failed to open /home/kolisikepu/Desktop/-.


Playing /home/kolisikepu/Desktop/Everything.mp3.
File not found: '/home/kolisikepu/Desktop/Everything.mp3'
Failed to open /home/kolisikepu/Desktop/Everything.mp3.


Exiting... (Quit)

```

I hope this helps.

---

### Post by taavikko on 2008-04-01
> gmplayer /Michael Buble - Everything.mp3
.
.
.
Playing /Michael.
File not found: '/Michael'
Failed to open /Michael.


It's incorrect file path...

Use tab to autofill the path ex. kaffe<tab> /Mich<tab>
and see what happens.

---

### Post by kolisikepu on 2008-04-01
> **taavikko said:**
> It's incorrect file path...

Use tab to autofill the path ex. kaffe<tab> /Mich<tab>
and see what happens.

It's there, but I don't think it likes the spaces in between the name of the file.  Do I use $ sign for space?

How can I get it to play in Movie Player?

---

### Post by taavikko on 2008-04-01
> **kolisikepu said:**
> It's there, but I don't think it likes the spaces in between the name of the file.  Do I use $ sign for space?

How can I get it to play in Movie Player?
No you use backslash \
example, directory called "My Movies" and file "space balls.avi"
```
totem My\ Movies/space\ balls.avi
```

But it's better to use the <tab> button to autocomplete It'll get it right.
It's located just up of caps lock, the button with two arrows to left and right

---

### Post by forrestcupp on 2008-04-01
Or you could just navigate to it in your file browser and double click the file.

But the backslash is what you need for spaces.

---

### Post by msak007 on 2008-04-01
> **forrestcupp said:**
> Or you could just navigate to it in your file browser and double click the file.

But the backslash is what you need for spaces.
That's how the OP was originally doing it, but is trying to troubleshoot why the media players close. The suggestion to open the file using the terminal was so that he can catch any error messages prompting the media players to close abruptly without playing the file.

---

### Post by kolisikepu on 2008-04-01
> **taavikko said:**
> No you use backslash \
example, directory called "My Movies" and file "space balls.avi"
```
totem My\ Movies/space\ balls.avi
```

But it's better to use the <tab> button to autocomplete It'll get it right.
It's located just up of caps lock, the button with two arrows to left and right

Awesome bro!  That time my MP3 worked... beautiful TAB key aye.  It didn't work with my AVI file.  Here's the output.

```
kolisikepu@matrix-linuxacer:~/Desktop$ gmplayer Junior\ -\ Message\ to\ Kris.AVI 
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU          540  @ 1.86GHz (Family: 6, Model: 22, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/kolisikepu/Desktop/Junior - Message to Kris.AVI.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  320x240  24bpp  30.000 fps  2732.0 kbps (333.5 kbyte/s)
Clip info:
 Digitization Time: Tue Feb 29 12:58:46 2008

 Software: SONY DSC MJPEG 0100
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [alaw] aLaw/uLaw audio decoder
AUDIO: 11025 Hz, 1 ch, s16le, 88.2 kbit/50.00% (ratio: 11025->22050)
Selected audio codec: [ulaw] afm: alaw (uLaw)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x8925250]SwScaler: BICUBIC scaler, from yuv422p to yuv420p using MMX2
[swscaler @ 0x8925250]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x8925250]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x8925250]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x8925250]SwScaler: 320x240 -> 320x240
VO: [xv] 320x240 => 320x240 Planar YV12 
[ws] Error in display.
[ws]  Error code: 11 ( BadAlloc (insufficient resources for operation) )
[ws]  Request code: 140
[ws]  Minor code: 19
[ws]  Modules: flip_page

```

Any suggestions??

Thanks heaps for the first suggestion!

---

### Post by taavikko on 2008-04-01
> **forrestcupp said:**
> Or you could just navigate to it in your file browser and double click the file.

The downside of that is, no error report comes without hassle...

---

### Post by taavikko on 2008-04-01
> **kolisikepu said:**
> Awesome bro!  That time my MP3 worked... beautiful TAB key aye.  It didn't work with my AVI file.  Here's the output.

Any suggestions??

Thanks heaps for the first suggestion!

Try changing the video output module.
```
gmplayer
```
right click, preferences, Video tab, try different ones to find the one that works :)

---

### Post by kolisikepu on 2008-04-01
OK... MP3 is good, it plays via gmplayer and Kaffeine.

My video files are not so good.  Here are different outputs from different players.

Kaffeine plays the file, but I get no picture.
```
kbuildsycoca running...
Reusing existing ksycoca
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found

```

gmplayer crashes when I open it and here's my output.
```
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Celeron(R) CPU          540  @ 1.86GHz (Family: 6, Model: 22, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/kolisikepu/Desktop/Junior - Message to Kris.AVI.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  320x240  24bpp  30.000 fps  2732.0 kbps (333.5 kbyte/s)
Clip info:
 Digitization Time: Tue Feb 29 12:58:46 2008

 Software: SONY DSC MJPEG 0100
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [alaw] aLaw/uLaw audio decoder
AUDIO: 11025 Hz, 1 ch, s16le, 88.2 kbit/50.00% (ratio: 11025->22050)
Selected audio codec: [ulaw] afm: alaw (uLaw)
==========================================================================
AO: [alsa] 48000Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8
[swscaler @ 0x8925250]SwScaler: BICUBIC scaler, from yuv422p to yuv420p using MMX2
[swscaler @ 0x8925250]SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
[swscaler @ 0x8925250]SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
[swscaler @ 0x8925250]SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
[swscaler @ 0x8925250]SwScaler: 320x240 -> 320x240
VO: [xv] 320x240 => 320x240 Planar YV12 
[ws] Error in display.
[ws]  Error code: 11 ( BadAlloc (insufficient resources for operation) )
[ws]  Request code: 140
[ws]  Minor code: 19
[ws]  Modules: flip_page

```

Just to let you all know, everything worked in my first installation of Gutsy.  I then thought I'd be a hero and install the beta for Hardy cause that was to fix some other issues I was having and as it was suggested for someone from this forum to do.

I removed Hardy and came back to Gutsy and now things aren't working like they did.

---

### Post by kolisikepu on 2008-04-01
I've also installed VLC and this is what I get in my output.

```
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85

```

---

### Post by kolisikepu on 2008-04-01
I may have a solution for my problem.  How do I enable or use X11 for my environment?

---

### Post by parmdeep on 2008-04-01
i know the error you are getting, i had the same problem, its because you have compiz fusion enabled, turn it off and ur media files will work perfectly, HOWever if you want both features to work you need to change the output method of your video, there is a list somewhere if you search these forums its different for each individual/ before you change these settings try as i said turn compiz off and tell me if you encounter the same problem,

---

### Post by kolisikepu on 2008-04-02
> **parmdeep said:**
> i know the error you are getting, i had the same problem, its because you have compiz fusion enabled, turn it off and ur media files will work perfectly, HOWever if you want both features to work you need to change the output method of your video, there is a list somewhere if you search these forums its different for each individual/ before you change these settings try as i said turn compiz off and tell me if you encounter the same problem,

You're exactly right... I did notice that lastnight when I did turn off visual effects.  All my media works includng my webcam.  I installed smplayer & I was able change video output on that to.... I can't remember what video output I chose but when I figured that out, I created another thread titled (something along lines of....) "how to activate X11 or use it as default driver".

How did you fix it?  What list are you referring to?

---

### Post by taavikko on 2008-04-02
> **kolisikepu said:**
> You're exactly right... I did notice that lastnight when I did turn off visual effects.  All my media works includng my webcam.  I installed smplayer & I was able change video output on that to.... I can't remember what video output I chose but when I figured that out, I created another thread titled (something along lines of....) "how to activate X11 or use it as default driver".

How did you fix it?  What list are you referring to?

Just open the preferred mediaplayer, and under it's settings try different video drivers, until you find the one that works.

---

### Post by forrestcupp on 2008-04-02
If you use vlc, [here](http://ubuntuforums.org/showpost.php?p=4532372&postcount=10) is how you set it to use the X11 video output.

---

### Post by kolisikepu on 2008-04-02
> **taavikko said:**
> Just open the preferred mediaplayer, and under it's settings try different video drivers, until you find the one that works.

OK.... I've just tried Totem Movie Player, but it doesn't give me the option of Output.  This is just a work around, but it doesn't help with my webcam as well as it doesn't want to play as well unless I turn Compiz off.

---

### Post by taavikko on 2008-04-02
> **kolisikepu said:**
> OK.... I've just tried Totem Movie Player, but it doesn't give me the option of Output.  This is just a work around, but it doesn't help with my webcam as well as it doesn't want to play as well unless I turn Compiz off.

Use something else... smplayer is very good;)
and you can easily change it to be default app for videos.

---

### Post by kolisikepu on 2008-04-02
> **forrestcupp said:**
> If you use vlc, [here](http://ubuntuforums.org/showpost.php?p=4532372&postcount=10) is how you set it to use the X11 video output.

As mentioned before, I created a thread requesting how to use X11 Video output as default for everything... even Screensavers.  I know it is Compiz that's causing the problem where I can't play media (MP3's and Movies) and Webcam not working either.  But I did notice that when I choose X11 through media players such as VLC, smplayer, etc. my media works.  But that doesn't help with the fact that when anything with video or sound/mp3 the applications just shut down.

Thanks for the suggestion, but the problem is within the environment and not just the players.  So the question again is, is X11 a driver where I need to select as default driver for my video or XGL or what ever it was to render video and music??  Any assistance to teach will be awesome too.... as I'm learning.

---

### Post by taavikko on 2008-04-02
> **kolisikepu said:**
> As mentioned before, I created a thread requesting how to use X11 Video output as default for everything... even Screensavers.  I know it is Compiz that's causing the problem where I can't play media (MP3's and Movies) and Webcam not working either.  But I did notice that when I choose X11 through media players such as VLC, smplayer, etc. my media works.  But that doesn't help with the fact that when anything with video or sound/mp3 the applications just shut down.

Thanks for the suggestion, but the problem is within the environment and not just the players.  So the question again is, is X11 a driver where I need to select as default driver for my video or XGL or what ever it was to render video and music??  Any assistance to teach will be awesome too.... as I'm learning.

Paste input of the following commands
```
cat /etc/X11/xorg.conf |grep Driver
```
```
apt-cache policy ubuntu-restricted-extras linux-ubuntu-modules-`uname -r`
```

---

### Post by kolisikepu on 2008-04-02
cat /etc/X11/xorg.conf |grep Driver

```
Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "intel"
```

apt-cache policy ubuntu-restricted-extras linux-ubuntu-modules-`uname -r`

```
ubuntu-restricted-extras:
  Installed: (none)
  Candidate: 10
  Version table:
     10 0
        500 http://ftp.iinet.net.au gutsy/multiverse Packages
linux-ubuntu-modules-2.6.22-14-generic:
  Installed: 2.6.22-14.38
  Candidate: 2.6.22-14.38
  Version table:
 *** 2.6.22-14.38 0
        500 http://ftp.iinet.net.au gutsy-proposed/main Packages
        100 /var/lib/dpkg/status
     2.6.22-14.37 0
        500 http://ftp.iinet.net.au gutsy/main Packages

```

I hope this helps.

---

### Post by taavikko on 2008-04-02
Seems you have integrated Intel graphic card on your PC, that posess trouble using compiz.
You'd be better off not using compiz.
paste output here
**lspci -v |grep VGA** and or
** lspci -v |grep Intel**


That should clear few of your issues ;)
```
sudo apt-get install ubuntu-restricted-extras
```
This will prompt for accepting javas EULA just accept by arrow button and enter

Why does your profile says hardy development user, when you use gutsy;)

---

### Post by kolisikepu on 2008-04-02
> **taavikko said:**
> That should clear few of your issues ;)
```
sudo apt-get install ubuntu-restricted-extras
```
This will prompt for accepting javas EULA just accept by arrow button and enter

Why does your profile says hardy development user, when you use gutsy;)

:lolflag:  I was using Hardy, but "1" little thing annoyed me and no one could help with it.  Guess what it was??  My 'Delete' button on my keyboard would not work.  I only realised then how much I use this button, so I came back to Gutsy and I'm in the situation I'm in now with my media files ... :lolflag:

---

### Post by kolisikepu on 2008-04-02
> **taavikko said:**
> Seems you have integrated Intel graphic card on your PC, that posess trouble using compiz.
You'd be better off not using compiz.
paste output here
**lspci -v |grep VGA** and or
** lspci -v |grep Intel**


That should clear few of your issues ;)
```
sudo apt-get install ubuntu-restricted-extras
```
This will prompt for accepting javas EULA just accept by arrow button and enter

Why does your profile says hardy development user, when you use gutsy;)

OK... I've just executed that cmd you asked me to do, can you now remote to my computer with that last cmd I executed and as suggested?? :lolflag:

Was that suppose to help, because it didn't.

---

### Post by taavikko on 2008-04-02
> OK... I've just executed that cmd you asked me to do, can you now remote to my computer with the last thing I just as suggested??

No, i can't remote connect to your comp, lspci command shows info on hardware on pci 

apt-get install ubuntu-restricted-extras installs few packages that should make your files work.

You need to install ssh-server to somebody to remote connect to you, and that wouldn't be wise to let somebody access yous computer!

---

### Post by kolisikepu on 2008-04-02
This is "EXACTLY" what I was after.  I wanted to know how to run XGL or X11... and I've found the cmd that fixed all my problems.... aaaaaaahhhhh.

```
sudo aptitude install xserver-xgl compizconfig-settings-manager
```

Thank you all for helping.  This is now solved!

---

### Post by forrestcupp on 2008-04-02
Well, let me just ask the obvious.  Have you installed the restricted extras package?
```
sudo apt-get install ubuntu-restricted-extras
```
Or change the ubuntu to kubuntu if that's what you have.

---

