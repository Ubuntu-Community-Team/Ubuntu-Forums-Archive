---
title: "Xine question"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by Fornie on 2006-06-08
please i need your help on this one...

since i do have problem with totem and mplayer, i tried installing Xine...

it actually fix my VCD issue but the problem is the video/sound is not sync...

i did go terminal and type xine-check but i dont understand this...can someone explain this to me and what's the fix? please help...thanks a lot!!! :confused: 

===

fornie@Boi_Bibo:~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.15-23-386)
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
[ hint ] /dev/dvd is /dev/dvd, not a DVD device
         /dev/dvd is the default device that xine uses for playing DVDs.
         You could make your life easier by creating a symlink named /dev/dvd
         pointing to your DVD device (something like /dev/scd0 or /dev/hdc).
         If your DVD-ROM device is /dev/hdb (slave ATAPI device on primary bus),
         rm /dev/dvd
         ln -s hdb /dev/dvd
         typed as root will give you the symlink.
         Alternatively, you can configure xine to use the real device directly,
         using the setup dialog within xine, but I can't check your DMA
         settings in that case...
         press <enter> to continue...

[ good ] found xvinfo: X-Video Extension version 2.2
[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to do color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         [http://www.linuxvideo.org/gatos/](http://www.linuxvideo.org/gatos/)
         press <enter> to continue...

[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to do color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         [http://www.linuxvideo.org/gatos/](http://www.linuxvideo.org/gatos/)
         press <enter> to continue...

[ hint ] Your X server doesn't have any XVideo support...
         XVideo is an X server extension introduced by XFree86 4.x. This
         extension provides access to hardware accelerated color space
         conversion and scaling, which gives a great performance boost.
         If you have a fast (>1GHz) machine, you may be able to watch all
         kinds of video, anyway. You will waste lots of CPU cycles, though...
         press <enter> to continue...


===

i checked one of the threads...[http://ubuntuforums.org/showthread.php?t=76000](http://ubuntuforums.org/showthread.php?t=76000) and did the

sudo apt-get install libxine1c2 libxine-dev 

and try it again but i have an error message 

"the amount of dropped frame is too high, your system might be slow, not properly optimzed or just too loaded...

hmmm???

---

### Post by Hairy_Palms on 2006-06-08
it sounds like u need to enable dma for your cd-rom with hdparm
[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by Fornie on 2006-06-08
whaaa :confused: [-o< DMA is already enabled but just to make sure i did follow the instruction but still not working...the same error appears...this is making me insane whaaa please help! thanks

---

### Post by taurus on 2006-06-08
Have you tried to play that with vlc???

---

### Post by Fornie on 2006-06-08
whohohoooo! thanks dude! it worked...=D> is it ok if i just uninstall xine/mplayer on my machine? will it affect VCD capability or just leave it there? thanks again...you're the man!!!

---

### Post by taurus on 2006-06-08
Glad to hear that vlc works for you.  If you like vlc, you can uninstall both xine and mplayer with apt-get...
```

sudo apt-get remove xine mplayer

```
But if you have space, you can leave both of them on your machine.  Either way, it wouldn't hurt anything.

---

### Post by maddbaron on 2006-06-08
question i just downloaded the vlc player. i can hear the video playing but cant see it. it stays in mini mode. how do i fix that?

---

### Post by Fornie on 2006-06-08
hello :)

i just typed this code in the terminal window...

sudo apt-get update
sudo apt-get install vlc vlc-plugin-esd

if this one still did not work, try to install codecs...

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Multimedia_Codecs)

---

