---
title: "Yellow and Blue images, icons and image previews?"
date: 2006-01-20
forum: Apple PPC Users
---

### Post by erlyrisa on 2006-01-20
I just started with ubuntu a week ago (and may I say at last there is a simple and effective distro for the newbie)

I'm already using ubuntu and have no problems... but now I decided to get rid of os9 on my g3 power mac with 256mb and give kubuntu a try.

Everything is fine except for a quirk with images, specifically icon previews (as the actual icon and not the over hover preview) in konquerer, icon previews in gwenview, and zoomed previews (let's call them actual views --in the 'image window')   ,,, so what is the problemm..
They're all yellow!!. You can see them render to screen absolutely fine and then all of a sudden a yellow transparency get's renderd above them. This is the case when the image is 'zoomed out', when the image is 'zoomed in' from it's actual size then it's purple (or cyan I'm colour blind anyway).

Anyone else have this happening to them on PPC KDE? -maybe only on older hardware?

---

### Post by Peter76 on 2006-01-24
Having the same thing on a iBook 900 600mb... Anybody knows how to fix this?

---

### Post by erlyrisa on 2006-01-25
Hmm - I got a feeling we're the only ones!
I love kubunutu - and I can't be bothered putting os9 back on it (os9's useless today anyway and osX is too slow and besides doesn't have the software I want or the flexibility)

-Do you have that other problem where when the booting starts, after the yaboot 2nd stage , a couple of lines come up, that shouldn't, reading something like...

[blabla:errcodd] insmod - couldn't load blabla/ppckernel/libs/video/files - mostly graphical drivers

and then the kubunutu logo comes up for a short while (I have a feeling it needs those modules) and exits back to the console output (at least I can see what else is going wrong - although thankfully most of them are things I don't need anyway - bluethooth and junk)

I wonder if the vga drivers, which aren't installed, or aren't even included on the install CD but are a part of the debconfig are needed to render images properly. (personally I doubt it)

Anyway I'm downloading kubunut x86 at the moment so I'll see what happens if I don't load those particular modules on an x86 - maybe it really is the cure.

You know what the worst thing about those modules are - I dunno what deb package they are supposed to be a part of.-alright I rememmber a website specifically dedicated to file searches in packages and dowloads for them - but I'm having trouble networking too (but that's mostly my fault anyway)

Note to pros/coders that maybe reading this and would like to reply.
I also have a small error during init stating that memory at pci address bla:bla:1 (it's my scsi card) couldn't be located.
-I don't think it's a problem though b/c my root is contianed on the hardrive that is run by that scsi card - so I dismissed it as a problem that has something to do with the scsi driver thinking it's on a PC and trying to do something that the mac hasn't got (on board scsi ram?) or addresses differently. -could this memory addressing or whatever it is be conflicting with the display adapter?

-If peter76 - you have this line (which I doubt in the laptop) or another error upon initilisation then it would be kool if you wrote something about it:))
(I realise development for old G3's is probably not of concern but a quick reply would ease my mind)

---| on the whole though I wreckon this is a compile problem specific to kde and ppc that can't keep up. bet ya it's storing transparency masks for ALL images of certain variety even if they don't have one. Maybe the zoom flags, ie class flag : zoomed/in/out has leaked into the memory region of the transparancy and set the first/second int to ff
-which would make sence when the image transparency is rendering as yellow or cyan eg. RGB:ff,ff,00 = yellow or 00,ff,ff = cyan or magenta -I think
I betya the zoom flags are supposed to tell the renderer whether or not to zoom that transparency to the same zoom setting as the image itself. Sadly during compile the flag memory region has shifted some what - probably to the exact memory region of the transparacny mask - rendering it to a certain color.

We could also take a guess that the transparency and zoom flag are adressed via a pionter and that pionters value keeps shifting 4 bits between the start of the RGB and end of the RGB - why becuase you not only get yellow or blue getting rendered while in a static zoom state, you may get a mixture of both as it's getting rendered. - so the problem isn't any of the zoom code - it lies somewhere below that,(what a **&%) constantly changing pionter addresses or actaul file size in memory while it's rendering the transparancy.

---

### Post by N8K99 on 2006-02-01
I was having a problem similar to this when I first install KDE on my Ti Powerbook G4. The entire screen seemed to have a yellow transparency laid over it. Well, what I had to do to fix this was make sure that I had the correct resolution selected for X. Since I had nothing else on the computer at the time, I re installed and reselected the proper resolution.

There is a method of reconfiguring the xorg.conf file, I was not successful at it, but getting the resolution correct was teh solution to my probelm. I get the message about not having somethig installed during boot, but it does not effect my operations. I have thought that this is the Apple Bios bitching about not having the proprietary software running.

---

### Post by erlyrisa on 2006-02-01
Hmm - The Entire SCREEN! - well the G4's have nvidia's in them right?, as for G3's it's the r128. The ibook I have no idea. So it's not the driver coze the problems still present with two seperate drivers. (unless youv'e got the riva in your computer?)
I've finally got mine networked so I'll be looking into compiling some source - but first I have to figure out , or at least limit my options for what section(s) I should be checking/compiling. (I think I'm going to have to enlist into the bug forums)
I'm still downloading ubuntu to find out if it's just KDE doing something wrong (it is kde3.4 - development and not 3.3 so it's understandable, and the first thing to take out of / put in , the equation)
It's strange that you would of had this zoommy transparency over the whole X server output, My problem (an peter's) seems more limited to kde's proprietry software doing something wrong (unless kde ask's Xorg to do it's icon rendering?)
If Xorg seems to be the problem, that would be great (it should be fixed pretty quickly, and I'm wasting my time here)
Anyway I reccomend you keep that yellow problem in the back of your mind and upgrade Xorg when it's next version time - you'll then be able to get the resolutions you want without any yellow. -but I still wreckon it's KDE!

---

### Post by sarcasticfrench on 2006-03-10
I am having the same problem when I'm using Konquerer, but you can get around it by just using Firefox or some other browser for the web. Unless you can find another file manager your still stuck with using konquerer for non-web stuff. If this is any help to anyone who might know how to fix this, I'm using an ibook g3 300mhz.

---

### Post by erlyrisa on 2006-03-28
Ahh - Iv'e given up. -It's taken me weeks to download all the libraries and devolpers stuff via dialup - and yet I still wouldn't know where to begin anyway.

-stuff the mac I'm now on a duron 800. - the mac still good though - just looks crap. - oh and yes the problem persists in gnome aswell (although not as bad) - but gnome's a bit sluggish so I''ll make do with the yellow.

---

### Post by seatea on 2006-04-12
I think I have been experiencing the same problem you have on my  PM G4 400 Gigabit when I try to  play a DVD. I have an ATI Rage Pro 128 video card. My display is ok  until I try to play a DVD then the screen appears to get a yellow overlay  and other parts of the screen turn blue. Everything works fine, but I have to logout and then login again to correct the  problem. I found a partial solution  in  the xine FAQs. It  appears that Xv is buggy for my system, because if I start xine with XShm the DVD
 will play although I keep getting messages that my computer is dropping too many  frames. Here's an excerpt  from that FAQ:

"[B]I only see a blue (or green or black) video image most of the time.
[/B]
You are either watching a very boring video (just kidding) or you are suffering from a bug in the Xorg 6.7 implementation of X11.

The workaround is to add the line

   Option "XaaNoOffscreenPixmaps"

in the Device section of your X server configuration (usually /etc/X11/xorg.conf or /etc/X11/XF86Config).

[B]The image looks strange, it is shifted, cropped or shows weird lines!
[/B]
This points to a problem with the Xv extension, which is used by xine to display the video image. To verify this, try running xine with the XShm video output plugin:

   xine -V XShm

If that works fine, you just proved, that the Xv extension is buggy. xine will remember the last used video output plugin, so the setting will stay at XShm. You could simply continue using this, but XShm is a lot slower than Xv, so read on and see if you can get it working. Usually you should look for updated versions of the XFree driver module that belongs to your graphics card.

Other possibilites are limitations in either your XFree driver module or your graphics hardware. If your card could somehow be running out of ressources (graphics RAM perhaps) and displays an incorrect Xv overlay because of that, try reducing the display resolution and/or colour depth.

Consult the next question for more details on Xv.

**How can I make xine use the Xv extension and what drivers do I need?**

xine will normally use Xv by default if it is available. In some cases you might need to choose Xv playback manually (when the ~/.xine/config file for some reason says that you want to use XShm):

   xine -V Xv

If this doesn't work for you, it may be possible that Xv is not present on your system.

First you need to install/use XFree 4.x. Once you got that you have to make sure the XFree drivers you're using are supporting Xv on your hardware. Here are some hints for individual gfx chips:

    *

      3Dfx: if all you get is a solid black window, upgrade at least to XFree 4.1.0
    *

      ATI: if you only get "half a picture", try lowering your resolution or bit depth, disable DRI (looks like you ran out of video RAM)
    *

      Trident card: If you see vertical bands jumbled, upgrade to the latest xfree/experimental trident drivers (for the CyberBlade XP a driver exists here: [http://www.xfree86.org/~alanh/](http://www.xfree86.org/~alanh/) )
    *

      nVidia: With newer GeForce cards, Xv should work with XFree 4.2.0 or newer, for older RivaTNT cards use the binary drivers from nvidia (of course the binary drivers work as well for GeForce cards)
    *

      Mach64/Rage3D (not Rage128/Radeon) cards/chips get no XVideo with standard drivers, try GATOS drivers instead
    *

      intel: i815 has Xv support in XFree 4.x, others unknown
    *

      Permedia 2/3 has Xv support in XFree 4.x
    *

      Savage: at least some older drivers tend to lock up the whole machine, try the drivers available from [http://www.probo.com/timr/savage40.html](http://www.probo.com/timr/savage40.html) .
    *

      SIS: certain controllers (more info needed!) have Xv support in XFree 4.x
    *

      Chips and Tech 6555x, 68554, 69000, 69030 have Xv support in XFree 4.x
    *

      NeoMagic: certain controllers (more info needed!) have Xv support in Xfree 4.x
    *

      SiliconMotion: certain controllers (more info needed!) have Xv support in Xfree 4.x
    *

      Matrox: G200 or newer (but not Parhelia) have Xv support in XFree 4.x. For Parhelia, use the binary only drivers available from matrox' website. "

I am afraid that sorting  out the Xv problem is  way beyond my ability. I  am hoping
things  will be better in Dapper. Maybe you can get some use out of this information though.

---

### Post by erlyrisa on 2007-11-18
It's been a long time.... but I have some information to add (accidentally found this post of mine)

--> I got the same effect happening in Windows!!

If you increase the thumbnail size for windows the EXACT SAME effect occurs (well, only to the thumbnails for me, I haven't witnessed the other effects as described above)
Actually it's worse in windows. I used XP on a fairly decent machine (ok, on board Graphics MEM), and only increased the thumbnail size to 128pixels.... hwalla, what's this, in folders full of images, the thumbnails produced have a yellow aplha effect, with the actually image showing through between some banding (sections of pixels where the full info was read properly I presume) - and yes you get the blue shaded. or mixed blue/yellow shaded ones too.

SOOO to sume it up (my experiences anyway)

--> If anyone is planning to setup Gnome/KDE on an old PC, I would reccomend changing the default thumbnail size/quality to something a little more appropriate...(though, I think my complaining has fixed this... it seems as though, Ubuntu atleast, figures out an appropriate quality setting dependent on your PC --> I think?)
--->How to go about doing that is anyones guess (I would start by looking up just how gnome an KDE do their thumb-nailing - it seems to be shared with a common program, so it's that program/libraries settings that should be change)

---

