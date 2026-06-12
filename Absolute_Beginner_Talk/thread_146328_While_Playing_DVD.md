---
title: "While Playing DVD"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by d-x on 2006-03-18
I've posted this issue several times but this is what happens. 

When I go to play a DVD in no matter what Player under ubuntu it seems to a. freeze certain players b. start playing the first 3 seconds of a DVD (doesnt show warning screens at all just a black screen).

Is it because I'm in Region 4? Or doesn't this affect players under ubuntu? Is there a solution to my problem ? I've used Automatix to download a lot of players and codecs. Is there corruption now? Whats the go? Please help!

---

### Post by Pragmatist on 2006-03-18
Install xine.  Go into synaptic type this in a terminal:
```
sudo synaptic
```
then search for these packages and install them:
**libxine1c2**
**xine-ui**

Once they are installed, run this in a terminal:
```
xine-check
```

Post the output of that here.

---

### Post by d-x on 2006-03-19
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.12-10-386)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...

[OUCH!!] no xine-config on this machine.
         This means that xine-lib is either not installed
         or it is installed in a very unusual place.
         So you should probably install xine-lib before running xine-check...
         press <enter> to continue...

[ hint ] unable to determine plugin directory
         I could not determine your plugin directory. That would be much easier
         if you had xine-config installed (see message above)...
         Note that I could not check your xine plugins.
         press <enter> to continue...

[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 UYVY YV12 I420


Where is Xine-Lib?

---

### Post by d-x on 2006-03-19
I did a reinstall OF everything to do with xine and the tests work perfectly.

Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.12-10-386)
[ good ] intel compatible processor, checking MTRR support
[ good ] you have MTRR support and there are some ranges set.
[ good ] found the player at /usr/bin/xine
[ hint ] multiple xine executables found in your PATH
         I have found more than one occurance of 'xine' in your PATH:
         /usr/bin/X11/xine
         /usr/bin/xine
         You have probably installed xine-ui more than once, or the directory
         where you have installed xine occurs more than once in your PATH.
         Technically, this is not really a problem, but it's probably
         somewhat confusing, as it's not obvious, which xine you're using.
         You should probably uninstall the copies that you don't use...
         Further tests assume, you're using /usr/bin/X11/xine
         press <enter> to continue...

[ hint ] several instances of xine-config found in your PATH
         xine-config executables have been found in these places:
         /usr/bin/X11/xine-config
         /usr/bin/xine-config
         This probably means you have several versions of xine-lib installed.
         It's probably best to uninstall all unused xine-libs.
         Further tests will use /usr/bin/X11/xine-config.
         press <enter> to continue...

[ good ] plugin directory /usr/lib/xine/plugins/1.0.1 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/hdc
[ good ] /dev/dvd points to /dev/hdc
[ good ] DMA is enabled for your DVD drive
[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 UYVY YV12 I420

\\:D/ 

Yet it does the same thing as it did before doesn't play DVDS properly.. Plays the first 3 seconds then stops.

---

### Post by d-x on 2006-03-19
xine knows there is a DVD there, then it plays it for 1 second and goes back to the default xine screen.

Okay Anything that isnt encrypted works but anything that is encrpted isnt working. What do you use under linux  to solve this problem?

---

### Post by d-x on 2006-03-19
[QUOTE=d-x]xine knows there is a DVD there, then it plays it for 1 second and goes back to the default xine screen.

Okay Anything that isnt encrypted works but anything that is encrpted isnt working. What do you use under linux  to solve this problem?[/QUOTE]
Fixed it myself :D

---

### Post by Pragmatist on 2006-03-19
Good job!! :)  Incidentally, I use xine all the time.  Some of my favorite key-combinations are:

**g** brings up the controls
**space bar** pause
**enter** play
**up arrow** faster
**down arrow** slower
**left arrow** back a chapter
**right arrow** forward a chapter
**f** fullscreen

If you want xine to open in fullscreen mode, just use the **-F** switch.  You can make a launcher or edit a menu, and put this command with the -F switch.

---

### Post by d-x on 2006-03-19
Yeah I noticed, am very pleased because I was used to windows shortcuts and since that shortcuts are the same it's cool. Just stupid encryption sucks but when I fixed it I was pleased :D

---

