---
title: "Google Earth slow after update?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by digital_sabotage on 2007-06-27
I initially installed Google Earth and it worked great.  Used it several times.  Then it just stopped working properly.  Very slow on zoom... unusable.  I made no system changes ...only thing was critical updates.   Not sure what installed.  Was around June 10th to 15th I think.

I'm fairly noob so I'll just post what might be relevent info...

On starting GE through terminal.  Says...
> libGL warning: 3D driver claims to not support visual 0x5b
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try running with LIBGL_THROTTLE_REFRESH and LIBL_SYNC_REFRESH unset

Went to terminal...
```
graham@graham-laptop:~$ glxinfo | grep render
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20050225

```
And...
```
graham@graham-laptop:~$ dmesg | grep drm
[17179598.180000] [drm] Initialized drm 1.0.1 20051102
[17179598.180000] [drm] Initialized i915 1.5.0 20060119 on minor 0

```

And...
```
graham@graham-laptop:~$ cat /proc/version
Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri May 18 23:39:08 UTC 2007 (Ubuntu 2.6.17-11.38-generic)
```

>lspci shows my video card as...
> Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
I've searched high and low and none of the few suggested fixes did anything.

Any help is greatly appreciated.  Thanks in advance:-)

---

### Post by freebird54 on 2007-06-27
I've no idea what fixes you might have tried, but it sounds to me like you no longer have the 3d drivers enabled for your video card.  If what you hit was a kernel update, that can happen...

Do you remember what you did to get your video drivers going in the first place?  I suggest doing it again.. :)

If you find this vague, it's because I use a different card (ATI) - but if I saw anything about Mesa drivers I would know its proper driver wasn't working anymore.....

---

### Post by Golyadkin on 2007-06-27
Nooo! If the average orbital speed of Earth becomes much slower, there will be no more life on Earth! :D Noooo!!!! Please fix this problem quickly! The speed to aim for is 107218 km/h. ;)

---

### Post by digital_sabotage on 2007-06-27
I've just done a re-install of my xserver-xorg-video-i810 driver... no difference.  Good suggestion though freebird... thanks.  My drivers were installed with my original ubuntu install  ...I haven't had to do anything with them so far.

I should also mention that my beryl is working great (and no I don't have it running while troubleshooting this... I start in normal gnome session ...though google earth did work fine before as long as I wasn't using the beryl window manager, but metacity instead)

When I run glxgears in fullscreen I'm getting 203fps

I suppose I should look into modifying my driver settings... not that I have a clue where to begin.
I'll start reading.  

Still welcoming any suggestions offered.  Or miracle fixes... heheh.

Thanks all:-)

---

