---
title: "WoW/Wine/Cursed Intel... :("
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Baen on 2007-12-12
So, I finally threw Windows out the window a few days ago (noob warning right there) and jumped on Ubuntu, which I so far adore, except for the trying-to-get-World of Warcraft-to-work part, which is getting me ready throw the entire computer out the window. Im sure Im not the first, and sadly no the last either.  
Im having a lot of fun figuring out how stuff works, but Im loosing my faith in my ability to solve any problem by googling it. :P  So hopefully someone here can help me?

I've managed to get WoW to start with Wine, and I've pretty much followed the standard advices (editing the config.wts, poking around winecfg, etc...) but I've got lag and framerate from hell and the graphics are often (tho not always, strangely enough) completely messed up. Somehow I figured this must be Intel's fault (using Intel Mobile 915GM/GMS/910GML Express Graphics Controller), it seems a lot of people are having difficulties with it.

Seems Im using the i810 driver and I was hoping getting the 915 driver (i915-20060403-linux.i386, which from what I could find is the newest) would fix it but I cant get the thing installed. 

"sudo sh install.sh"  just gets me 

Compiling...[: 696: ==: unexpected operator
install.sh: 696: Syntax error: Bad fd number

Dont know what to make of this. Was suggested that I need to enable DRI, but I cant figure out how.
Another suggestion was to use

"sudo bash install.sh" which stops with

Compiling...
ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

Which is:

"make DRM_MODULES=i915.o modules
make[1]: Entering directory `/home/malin/Desktop/i915-20060403-linux.i386/drm/linux-core'
make -C /lib/modules/2.6.22-14-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/malin/Desktop/i915-20060403-linux.i386/drm/linux-core/drm_auth.o
In file included from /home/malin/Desktop/i915-20060403-linux.i386/drm/linux-core/drm_auth.c:36:
/home/malin/Desktop/i915-20060403-linux.i386/drm/linux-core/drmP.h:44:26: error: linux/config.h: No such file or directory
make[3]: *** [/home/malin/Desktop/i915-20060403-linux.i386/drm/linux-core/drm_auth.o] Error 1
make[2]: *** [_module_/home/malin/Desktop/i915-20060403-linux.i386/drm/linux-core] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/malin/Desktop/i915-20060403-linux.i386/drm/linux-core'
make: *** [i915.o] Error 2"

Whatever that means. Anyway, figured Id get the latest kernel modules and that'd be that, except it seems I already have them. Bummer. 

And that's where I'm stranded. Am I even on the right track? Should I be doing something completely different to get wow playable, or will getting that cursed driver installed help - and how do I even do that?

Sorry about the long post (tho I guess you're used to it. :D ). Hope I make some sort of sense to you,  since I really haven't got the foggiest idea what Im doing. I guess it shows. :P

---

### Post by spiderbatdad on 2007-12-12
did you read this article:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Baen on 2007-12-12
Read, followed, got it to work. But it doesnt cover my problems, it only gets me to the point where I can run WoW, not how to run it in a playable way.

---

### Post by wheredidrealitygo on 2007-12-12
What does the "915resolution" package in synaptic do for you?

---

### Post by reacocard on 2007-12-24
I'm also trying to run WoW on an Intel 915, but I also cannot get good performance from it. 4fps is the max thus far.  I haven't tried installing 915 drivers, but the i810 driver has been superseeded by the 'intel' driver in gutsy which is supposed to support all intel cards, but apparently still performs badly here. Howver, out of curiousity I did try running WoW with -opengl in Windows and the graphics were completely messed up, so I guess its possible that intel chips, opengl and WoW just don't get along. :(

---

### Post by wheredidrealitygo on 2007-12-24
I'm beginning to think OpenGL and Intel are a problem too. 

Since my last post in this thread (a week ago) I have been trying, unsuccessfully to get WoW working on an intel chip (on a laptop) with Gutsy and it just is not happening. For the record it's 945gm.

All of my other machines run nVidia cards and it runs perfectly on the rest of them.

P.S. Reacocard, love your repo.

---

### Post by reacocard on 2007-12-24
I found a workaround!! it's incredibly simple. All you have to do is install directx in wine, and run wow in directx mode. that's all there is to it. the reason it was sucking before was that it was falling back to the opengl software renderer for the operations that the intel card doesn't support. by installing directx we now use the directx software renderer for those operations, and it appears directx's is better for this. I now get a mostly playable 10-15 fps, and I haven't even tried more tweaking yet!  I'll post back here if I find more improvements.

---

### Post by mjkelly on 2007-12-25
Ok how did you install directx with wine and then use wow through directx?

Im using the 945 chipset and i can get to the character screen and i get this error: 
Mesa 7.1 implementation error: i915_program_error: Exceeded max nr indirect texture lookups

---

### Post by reacocard on 2007-12-25
> **mjkelly said:**
> Ok how did you install directx with wine and then use wow through directx?

Im using the 945 chipset and i can get to the character screen and i get this error: 
Mesa 7.1 implementation error: i915_program_error: Exceeded max nr indirect texture lookups

I just used the directx installer that came with wow. you may have to set your wine windows version to XP first though. WoW should use directx by default unless you changed your config.wtf to force it into opengl mode.  I'm using wine 0.9.51 (from the winehq ubuntu repos) with WoW 2.3.0 on Gutsy with the 'intel' graphics driver, if any of that differs from your setup that may be the problem.

---

