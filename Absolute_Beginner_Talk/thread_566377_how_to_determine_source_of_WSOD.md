---
title: "how to determine source of WSOD"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by eatloaf on 2007-10-03
i recently installed feisty and i get the WSOD within 1 minute to 3 hours of using the desktop, directly or through VNC.

I would appreciate any help in learning how to isolate the source short of doing an A-B comparison of all of my hardware and software.

I have looked at the system log and found no obvious commonality between crashes.

TIA.

---

### Post by Delvien on 2007-10-03
WSOD= White screen of Death?

what are you doing when this happens?

---

### Post by eatloaf on 2007-10-04
Yes. The White Screen of Death. Although I've also seen random patterns: stripes or cubes.

As to what I'm doing, nothing specific.  Browsing the filesystem or editing conf files etc.  There's no pattern to the crashes except that i'm actively using the desktop.  I haven't seen it crash after returning to the computer after a period of inactivity.

This happens in Gnome and KDE, 7.04 and 7.10beta (both amd64 versions)  Both installed and when using a LiveCD.

Also, this happened both with the default ati drivers and the restricted drivers.

I've recently switched from Fedora and never experienced it there.  I've made no hardware changes except swapping out a bad drive in a raid 5 ( which prompted the distribution switch )

I was hoping that there would be a dump I could load up that might tell me where it was crashing?

---

### Post by nowshining on 2007-10-05
maybe Gutsy will sort this out for you, u can download the beta now or you can wait and try then.

---

### Post by RomeReactor on 2007-10-05
Hi. eatloaf, try this from the terminal:
```
cat /var/log/Xorg.0.log
```
Look for anything that could be an error message, and post that here for people to see, and hopefully help you diagnose the problem.

---

### Post by eatloaf on 2007-10-21
the following Xorg.0.log entries look suspect?

```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
```

```
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
```

I don't really know what i'm looking it so it's hard to evaluate what's important.

I was hoping there would be a memory dump or something that would contain the stack when it died?

---

### Post by RomeReactor on 2007-10-21
> (EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

These two lines are error messages relating to your ATI card; however, I don't have ATI, so I can't really be of further assistance with your problem, except to suggest you use the **ati** driver instead of **fglrx** (which means no acceleration and no 3D). Surely someone who has an ATI card can provide you with appropriate help.

---

