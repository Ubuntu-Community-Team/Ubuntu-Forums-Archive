---
title: "Only one MAJOR Problem...3D Maybe?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by DNABIOS on 2008-02-24
So I'm a brand new user (not just to Ubuntu but to Linux in general), and I have the standard story of wanting a 64-bit OS that wasn't as terrible as Vista.  Overall I'm VERY pleased.  It's my main OS now.  There were a few minor/major problems but after Internet was up I self-taught until I smoothed out the biggest bumps (yesterday I learned sudo = super-user do and wasn't just sumo mis-spelled!).

But now I'm in over my head, and could use a little help.  If there's a more appropriate forum for this let me know.  I'm a little lost.

So I've got an ATI Radeon 3850 and installed the proprietary drivers in the hopes it would be more compatible, but I'm getting TERRIBLE graphical corruption whenever I try to do anything more complex than 2D (see picture for what Arkhart gives me...Vegastrike is much worse and Wesnoth works fine).  I've tried compiling the drivers myself with no luck.  I'm not even certain what problem this is...could it be 64-bit vs. 32-bit?  System information at end of post.  Games are easiest, but if there are other programs that might be more diagnostic I don't mind running them.

The clues I have:
'glxinfo | grep -i opengl' says I must've done something right:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850
OpenGL version string: 2.1.7281 Release
OpenGL extensions:

'grep fglrx /var/log/Xorg.0.log' reports fglrx in use

'grep '^(EE)\|^(WW)' /var/log/Xorg.0.log' reports:
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24 which continues on for a while...

glxgears - info works fine with the little window, but glxgears -fullscreen gives the same corruption as Arkhart and friends.

During my one-time attempt to compile and install wine 0.9.56 before it hit the repositories (turned out not so good, but FYI if anyone else wants to try it now) I got an error that said it couldn't find opengGL, but I think I fixed that.

Can anyone think of anything else I can do?  I honestly don't know what my next step should be.

---
Video Card:  Gigabyte Radeon HD 3850
Mobo:  Gigabyte GA-X38-DQ6
CPU:  Intel E8400
OS:  Ubuntu
Mobo:

---

### Post by CCNA_student on 2008-02-24
If you want better drivers you will probably have to use the 32-bit version of Ubuntu. Other than that, I have nothing else useful to add.

---

### Post by DNABIOS on 2008-02-26
Weirdly enough, this actually did help.  I installed the 32-bit Ubuntu on the same drive and things appear ok now, even in the 64-bit version.  It's super-slow and choppy, and now the control center says it can't find the driver, but now that it at least works I'm reluctant to play with it.

Thanks!  :)

---

