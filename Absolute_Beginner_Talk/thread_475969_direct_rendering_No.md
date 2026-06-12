---
title: "direct rendering: No?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-16
I installed Beryl and wanted check out some of the cool eye candy and I don't think that its fully set-up properly.  
I opened a terminal and typed 
```

 glxinfo | grep direct

```

and recieved the following message:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

I have an ATI x1900xtx video card and I used envy to install get and install its drivers.

any advice to get things set up properly will be appreciated.

Thx in advance,

VC

---

### Post by Motoxrdude on 2007-06-16
Paste the output of
> fglrxinfo

---

### Post by overdrank on 2007-06-16
> **videocheez said:**
> I installed Beryl and wanted check out some of the cool eye candy and I don't think that its fully set-up properly.  
I opened a terminal and typed 
```

 glxinfo | grep direct

```

and recieved the following message:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

I have an ATI x1900xtx video card and I used envy to install get and install its drivers.

any advice to get things set up properly will be appreciated.

Thx in advance,

VC

HI and welcome have you tried the sticky posted in the forums
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
:popcorn:

---

### Post by videocheez on 2007-06-16
> **Motoxrdude said:**
> Paste the output of

Here ya go.

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

---

### Post by bone43 on 2007-06-16
You need to run a XGL session with your ATI card and possible beryl 2.0 its what i am using with my X1400.

 Beryl works fine but no direct rendering seems we cant have it all with ATI thanks to there lack luster Linux support :(

---

### Post by bobplano on 2007-06-16
you fglrx drivers aren't set up correctly. it should say something like ATI...
i don't really remember how i got mine working but looking on the internet these look like the commands i used. 
```
sudo mkdir /lib/modules/`uname -r`/misc
sudo cp /lib/modules/`uname -r`/volatile/fglrx.ko /lib/modules/`uname -r`/misc/fglrx.ko
```

---

### Post by videocheez on 2007-06-16
> **overdrank said:**
> HI and welcome have you tried the sticky posted in the forums
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
:popcorn:

Yeah man.  I read that link and already tried that.  Then I used envy to install closed source ATI drivers.  Perhaps i didn't do something right with that link because at the very end when I reboot, I don't know what the following statement means.

"Ubuntu 7.04 should now boot into GDM/KDM."

Should I use envy to unistall drivers before following the ATI driver guide  again?

Thanks,

VC

---

### Post by videocheez on 2007-06-16
> **bone43 said:**
> 
 Beryl works fine but no direct rendering seems we cant have it all with ATI thanks to there lack luster Linux support :(

Ok, if Beryl works fine.  How exactly do apply some of these cool 3d effect.  I see a bunch of setting to change but don't see how to apply them.

---

