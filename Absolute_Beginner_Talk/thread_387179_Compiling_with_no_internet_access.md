---
title: "Compiling with no internet access"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Orinoco on 2007-03-18
I've recently installed Ubuntu Edgy Eft on my new (formerly Vista OS) laptop.  So far, it's running OpenOffice, the Gimp and Blender just fine, but the movie and music player complains that it doesn't have the proper codecs.  I need to connect the computer to the internet.  

Unfortunately, my isp is windows based.  So, I need to install wine to get access to the internet.

My problem is in installing wine with no internet access.  I can download files on my XP desktop computer, and transfer the files via USB memory stick, but all the documentation I've looked at assumes a working internet connection.

So: I have source code for wine on the desktop, unpacked into a folder.  I attempted to run ./tools/wineinstall as the read-me said to, but got a configure error
> configure: error: C compiler cannot create executables

So I'm stuck.  What do I do next?

---

### Post by taurus on 2007-03-18
Insert the Ubuntu install CD into a drive and type these into a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by Orinoco on 2007-03-18
Thanks for the quick response, Taurus.  I think I'm moving forward.  

./tools/wineinstall went further this time, and got to

> checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package.

Configure failed, aborting install.


Where can I find the flex package, and are there any more that will be needed that I could get at the same time?
Never mind, I think I found it at [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by Orinoco on 2007-03-18
OK, after installing flex, M4 and bison, the ./tools/wineinstall command got through the configuration part and gave me a bunch of warnings, seemingly telling me I could proceed, but nothing would actually work.

> 
configure: WARNING: X development files not found. Wine will be built without
configure: WARNING: X support, which currently does not work, and probably
configure: WARNING: isn't what you want anyway. You will need to install devel
configure: WARNING:  packages of Xlib/Xfree86 at the very least.

configure: WARNING: Wine will be build without OpenGL or Direct3D support
configure: WARNING: because something is wrong with the OpenGL setup:

configure: WARNING: Your system appears to have the FreeType 2 runtime libraries
configure: WARNING: installed, but 'freetype-config' is not in your PATH. Install
configure: WARNING: the freetype-devel package (or its equivalent on your distribution)
configure: WARNING: to enable Wine to use TrueType fonts.

configure: WARNING: FontForge is missing.
configure: WARNING: Fonts will not be built. Dialog text may be invisible or unaligned.


I will go look for the Xlib/Xfree86 development packages, and hopefully the "at the very least" remark is just a warning that there may be other files needed to make those puppies work.  Also the freetype-devel package and FontForge.

Any ideas on how to diagnose and fix "something is wrong with the OpenGL setup?"

How do I put 'freetype-config' on my PATH?

---

### Post by ghoutman on 2007-03-29
I am a raw beginner so take any advice with a grain of salt...  I have an Internet connection but my install of Wine went very much the same as yours.  After I got to the point where you were a week ago I opened the Synaptic Package Manager, found FontForge, (Homepage: [http://fontforge.sourceforge.net/](http://fontforge.sourceforge.net/)) freetype1-tools, freetype2-demos, and wine in the "Package" list; selected and applied the packages.  The Synaptic Package Manager found a dependency and applied it during the install but after that I was able to run a Windows app - stng260.exe (McAfee).

Good Luck

---

