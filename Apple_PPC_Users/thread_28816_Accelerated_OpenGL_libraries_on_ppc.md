---
title: "Accelerated OpenGL libraries on ppc"
date: 2005-04-21
forum: Apple PPC Users
---

### Post by agravain on 2005-04-21
Hi, 

I'm missing the openGL libraries from ATI and NVIDIA for Linux/ppc.
Seems like ATI and NVIDIA haven't cared to build them for this platform. 
Would it be as simple as recompiling the libraries to make them work on Linux ppc (that is, assuming you are ATI/NVIDIA and got the source ready) ?

In any case, is there something we Linux ppc users can do to convince the vendors to release their openGL libraries for Linux ppc?

---

### Post by farruinn on 2005-04-27
Unfortunately, like good flash/shockwave support, this is something that the vendors simply don't see a need for. I believe there have been petitions in the past, but I don't think anything has ever come from them.

---

### Post by chascon on 2005-04-29
Try:
apt-get install swf-player

This is what 'apt-cache search swf-player' tells me:

Priority: optional
Section: universe/utils
Installed-Size: 152
Maintainer: David Schleef <ds@schleef.org>
Architecture: powerpc
Source: swfdec0.3
Version: 0.3.2-2
Depends: libart-2.0-2 (>= 2.3.16), libc6 (>= 2.3.2.ds1-4), libglib2.0-0 (>= 2.6.0), libgtk2.0-0 (>= 2.5.6), libmad0 (>= 0.15.1b), libsdl1.2debian (>> 1.2.7-0), libswfdec0.3, libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1)
Filename: pool/universe/s/swfdec0.3/swf-player_0.3.2-2_powerpc.deb
Size: 30108
MD5sum: 09bc46e08404ca1fce717f98eb4a88d7
Description: SWF (Macromedia Flash) player
 A GTK+ and SDL based player for Macromedia Flash animations.  Includes
 a Mozilla plugin, that embeds the player into Mozilla-based browsers,
 in order to allow seamless viewing of Flash animations in web
 pages.  Includes a GdkPixbuf loader, so that SWF animations can be
 used seamlessly as images in Gtk+ applications.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by chascon on 2005-04-29
As for an OpenGL alternative, you can try to get acceleration if you were lucky, or smart enoug to get a mac with a ATI video card.
Pass:
 glxinfo | grep "direct rendering"

If it says yes, you have acceleration. If not look around to see how to enable it.

---

