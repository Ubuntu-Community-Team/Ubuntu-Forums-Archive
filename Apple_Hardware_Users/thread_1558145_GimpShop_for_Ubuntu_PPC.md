---
title: "GimpShop for Ubuntu PPC"
date: 2010-08-21
forum: Apple Hardware Users
---

### Post by MacPenguin1972 on 2010-08-21
Hello 

I am running Ubuntu 10.xx for Macintosh PPC. I am running a dual 1GHz PPC G4 Desktop (the one with the silver/mirror drive door on the front) 

**GimpShop** [COLOR=Red]**DOES NOT work under Mac OS X**[/COLOR], _**even under X11**_ - Or at least I cannot get it to run for one simple reason:  On the install program there are all these weird characters where text should be- I cannot proceed with the installation due to this problem. And I have found no way to correct it so I can actually read whatever text is being displayed. I have no way to resolve this issue. I am neither a hacker or a programmer and have no way to correct this defect in the software.

Because of this GimpShop is NO option to me under Mac OS X 10.4.

**SO**-- I would like to know how to use it for Ubuntu on the Power PC G4.

All the Ubuntu versions I have seen for Gimpshop Ubuntu refer to an INTEL processor- is there any alternative? I am not a programmer. So I need a version that a "total idiot" can install and use. I would very much appreciate any recommendations anyone can offer. 

Thank you! :-) :p

MacPenguin

---

### Post by MacPenguin1972 on 2010-08-22
Hello again,

I don't mean to bump my own thread here. But I really could use some suggestions on how to fix my problems with using GimpShop- either find a way to make the text appear so I can install GimpShop, or else find a version that will work for Ubuntu 10.x PPC. 

After all, if I can't find out here where else can I go?

Please help. Much appreciated. Thx.

Sincerely,
MacPenguin

P.S. I have attached a screenshot of what happens when I try to install Gimpshop under Mac OS X 10.39 on my PPC G4 Dual 1.0GHz Desktop.

As you will see, loading becomes impossible since you cannot read what is being displayed.

---

### Post by libssd on 2010-08-22
> **MacPenguin1972 said:**
> All the Ubuntu versions I have seen for Gimpshop Ubuntu refer to an INTEL processor- is there any alternative? 

Does this help? [http://gimpshop.blogspot.com/2006/05/gimpshop-2211-universal-binary-for-mac.html](http://gimpshop.blogspot.com/2006/05/gimpshop-2211-universal-binary-for-mac.html)

I also have a PPC iMac, and am resigned to the fact that this hardware is old enough that fewer and fewer applications will be designed to run on it. Google Chrome is one example.

---

### Post by shawnhcorey on 2010-08-22
> **MacPenguin1972 said:**
> **SO**-- I would like to know how to use it for Ubuntu on the Power PC G4.

I checked the [official site]("http://www.gimpshop.com/") and there is no binary for PPCs.  You would have to build your own.

First, open System->Administration->Synaptic Package Manager.  Search for "build-essential" (note:  no 's' at the end) and install the package.  While you're at it, you might as well install the documentation for it too; search for "manpages-dev" and install it.

Now, download the source for Gimpshop.  Get the [stable version]("http://rapidshare.com/files/86270572/gimp-2.2.8.tar.bz2").  Unpack it and look for the files README and INSTALL.  Follow the instructions you find there.

---

### Post by MacPenguin1972 on 2010-08-22
> **libssd said:**
> Does this help? [http://gimpshop.blogspot.com/2006/05/gimpshop-2211-universal-binary-for-mac.html](http://gimpshop.blogspot.com/2006/05/gimpshop-2211-universal-binary-for-mac.html)

I also have a PPC iMac, and am resigned to the fact that this hardware is old enough that fewer and fewer applications will be designed to run on it. Google Chrome is one example.


Hello,

Thanks for the reply. Actually that site is where I got my copy of Gimpshop. And when I try to load it I get all those weird characters shown in my screenshot- wanting to know how to fix. I am going to school at ITT for computers by my Linux and programming classes won't be for several months yet. So for now I'm the typical "idiot book-reading end user" I'm afraid. lol! :-)

I have regular Gimp but that thing is a @#$%! to use! Especially for someone who has been using Photoshop for the last 12-15 years! The interface is not the same plus I'm trying to cope with the fact the menus take up half the screen giving you little workspace to do your artwork in. Probably something I will have to learn. I will miss Photoshop layers if I switch to Gimp. It doesn't appear to sport this option. :-(

Everyone wants the new hardware. I'm looking to replace my old G3 because while the blue and white G3 300MHz tower was awesome in it's day- today it's only a museum relic, if you want to have your own personal computer museum. (But the darn thing still works! Old as it is!)

I'll probably keep my G4 as a port back to the old OS9/OSX world so I can keep my Photoshop 6.0 (which serves me just fine- Photoshop 6 can do everything I need to do so I could care less if I get any of the CS versions right now.) 

Will have to start browsing Macofalltrades.com to see what refurbished WINtel Macs they're selling! lol! :-)

Cheers! 
MacPenguin

---

### Post by MacPenguin1972 on 2010-08-23
> **shawnhcorey said:**
> I checked the [official site]("http://www.gimpshop.com/") and there is no binary for PPCs.  You would have to build your own.

First, open System->Administration->Synaptic Package Manager.  Search for "build-essential" (note:  no 's' at the end) and install the package.  While you're at it, you might as well install the documentation for it too; search for "manpages-dev" and install it.

Now, download the source for Gimpshop.  Get the [stable version]("http://rapidshare.com/files/86270572/gimp-2.2.8.tar.bz2").  Unpack it and look for the files README and INSTALL.  Follow the instructions you find there.


Hello,

Thanks for the info. I'll have to give that a shot. I have the Mac OS  X version but I can't get rid of those weird characters on the screenshot I attached. If I CAN and am able to successfully load the program I supposed I'd be content to have it on the Mac OS side. 

I even wiped out my X11 and reinstalled it from the OS 10.4 DVD - it says not to download the version from Apple's site. 

I will have to try what you suggested and see if I can make it work. Thanks again! :-)

I am open to other ideas also. 

Cheers!
MacPenguin

---

### Post by libssd on 2010-08-23
I have no Photoshop habits to unlearn. :D On the Mac I use [Graphic Converter]("http://www.lemkesoft.com/") for image manipulation. Runs fine on a PowerPC and has good documentation.

I changed some of the defaults in gimp, so that it looks like the attached screenshot when it opens. Even on a 10.1" netbook, this leaves a usable amount of space for the image window.

My problem with the whole gimpshop project, if I understand it correctly, is that gimp is evolving, and gimpshop is never based on the current release. Or, am I misunderstanding gimpshop's release numbering system?

---

### Post by shawnhcorey on 2010-08-23
To tell you the truth, I never heard of Gimpshop before this thread.  I prefer to use [Inkscape]("http://inkscape.org/") for graphics since I can render it to any size I want.  Inkscape is available through the standard software sources.

BTW, with Inkscape you can create [things like this]("http://tavmjong.free.fr/INKSCAPE/DRAWINGS/clock2.svg").

---

### Post by MacPenguin1972 on 2010-08-23
> **libssd said:**
> I have no Photoshop habits to unlearn. :D On the Mac I use [Graphic Converter]("http://www.lemkesoft.com/") for image manipulation. Runs fine on a PowerPC and has good documentation.

I changed some of the defaults in gimp, so that it looks like the attached screenshot when it opens. Even on a 10.1" netbook, this leaves a usable amount of space for the image window.

My problem with the whole gimpshop project, if I understand it correctly, is that gimp is evolving, and gimpshop is never based on the current release. Or, am I misunderstanding gimpshop's release numbering system?



Ahhh, GraphicConverter! I haven't used that in years, except for mass image conversion (one file format to another). Always found the paint/drawing features way too limited for my needs. 

I am looking to eventually go to the Intel-based Mac. But don't want to spend hundreds for the CS Photoshop programs. So I've been looking for an alternative. People have told me gimpshop was the way to go for a more "Photoshop" feel.

How may I ask, did you get Gimp set up that way? Can you give me a few pointers? Thx. :-)


sincerely,
MacPenguin

---

### Post by MacPenguin1972 on 2010-08-23
> **shawnhcorey said:**
> To tell you the truth, I never heard of Gimpshop before this thread.  I prefer to use [Inkscape]("http://inkscape.org/") for graphics since I can render it to any size I want.  Inkscape is available through the standard software sources.

BTW, with Inkscape you can create [things like this]("http://tavmjong.free.fr/INKSCAPE/DRAWINGS/clock2.svg").


Thanks for the tip. Checked out Inkscape and tried to download it but it won't run on my machine (PowerPC G4 Dual 1.0GHz) 

What kind of machine do you use? Thx. :-)

---

### Post by shawnhcorey on 2010-08-24
I have a PowerBook G4 Titanium III.  I have no idea why it doesn't work on your machine.

---

### Post by libssd on 2010-08-24
> **MacPenguin1972 said:**
> How may I ask, did you get Gimp set up that way? Can you give me a few pointers? Thx. :-)
A picture is worth a thousand (well, a few dozen, anyway) words.

---

