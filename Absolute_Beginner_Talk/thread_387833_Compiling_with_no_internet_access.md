---
title: "Compiling with no internet access"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Orinoco on 2007-03-18
I am attempting to compile Wine from source on a laptop not connected to the internet.  At first configure quit with complaints that flex wasn't present.

After installing flex, M4 and bison, the ./tools/wineinstall command got through the configuration part and gave me a bunch of warnings, seemingly telling me I could proceed, but nothing would actually work.

> configure: WARNING: X development files not found. Wine will be built without
configure: WARNING: X support, which currently does not work, and probably
configure: WARNING: isn't what you want anyway. You will need to install devel
configure: WARNING: packages of Xlib/Xfree86 at the very least.

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:

configure: WARNING: Your system appears to have the FreeType 2 runtime libraries
configure: WARNING: installed, but 'freetype-config' is not in your PATH. Install
configure: WARNING: the freetype-devel package (or its equivalent on your distribution)
configure: WARNING: to enable Wine to use TrueType fonts.

configure: WARNING: FontForge is missing.
configure: WARNING: Fonts will not be built. Dialog text may be invisible or unaligned.


I will go look for the Xlib/Xfree86 development packages, and hopefully the "at the very least" remark is just a warning that there may be other files needed to make those puppies work. Also the freetype-devel package and FontForge.

Any ideas on how to diagnose and fix "something is wrong with the OpenGL setup?"

How do I put 'freetype-config' on my PATH?

---

### Post by eljalill on 2007-03-19
I had the same error, when I compiled wine.

The error about PATH disappeared, when I had the right package installed, same with the OpenGL error, when I installed freeglut3 and possibly libgl1-mesa-dev ( I have that installed now, I am not sure anymore, whether wine was the reason to install it though, same with a few other libgl packages).

But are you sure you need to be compiling? You should be able to download installation packages from winehq....

Hope this helps...

---

