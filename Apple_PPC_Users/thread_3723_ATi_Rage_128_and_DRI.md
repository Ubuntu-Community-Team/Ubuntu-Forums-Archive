---
title: "ATi Rage 128 and DRI"
date: 2004-11-08
forum: Apple PPC Users
---

### Post by sumanjay on 2004-11-08
I just felt I ought to mention that if your Mac uses the ATi Rage 128 graphics processor(eg. most G3 laptops like the Pismo and Lombard do), you will be better off reducing the default depth to 16 from 24 in your XF86Config-4 file. This enables Direct Rendering, aka 3D hardware acceleration, for the processor. Using this, my fps went to 540fps from nearly 40fps. I think the reason you need to reduce it is because when it's set at 24 bits, XFree tries to access more Graphics memory than is actually present in your graphics card. The steps to go about lowering the colour is-
1) Change into one of the Virtual Terminals using Ctrl+Alt+F1 (or Func+Ctrl+Alt+F1) and login with your username and password.
2) Type the following command to edit your XF86Config-4 file -
[CENTER]**sudo nano /etc/X11/XF86Config-4** [/CENTER] 
3) Move to the Section "Screen", which you can do either by scrolling down or by pressing Ctrl+W and typing "Screen"  into the search box.
4) Change the figure after DefaultDepth to 16 from 24. Press Ctrl+X to save the file.
5) You've now made the requisite changes, but to have them enabled, you will need to restart X itself. An easy way to do this is to switch back to X by pressing Ctrl+Alt+F7 (or Func+Ctrl+Alt+F7) and then pressing Ctrl+Alt+Delete. 
6) Log in and check if 3D acceleration is enabled by opening a Terminal (Applications->System Tools->Terminal in Gnome) and typing the following command-
[CENTER]**glxinfo | grep "direct rendering"** [/CENTER] 

If the answer is "Yes", then cheers!

---

### Post by trash on 2004-11-08
my G4, 466 has one to.. .my bit depth was 8 and i couldn't figure out why I has such a crappy resolution.... just tried 16 and and it's beautiful!

thanks sumanjay
also a great big thanks to the Ubuntu team(shhh, Ubuntu has replaced YDL on my G4):)

---

### Post by phatbob on 2004-11-11
[QUOTE=sumanjay]If the answer is "Yes", then cheers![/QUOTE]

  :) Cheer, indeed!

This also fixed a problem I was having with my Rev. A iMac. I couldn't get any resolution other than 528 x 384-- which was completely unusable. I followed sumanjay's advice above, and now I have a usuable computer with a decent and workable screen resolution.

Thanks, sumanjay!   :smile:

---

### Post by gilgamesh on 2004-11-11
hi
how do you get a pipe in ubuntu, on my ibook i can't get one using the macos sequence (option l )
thanks (by the way what about accolade and others )

---

### Post by Huxley on 2004-11-11
I have a powerbook G3 bronze 400 and hoary.
The result was

Xlib: extension "XFree86-DRI" missing on display ":0.0".
Direct rendering: No

---

### Post by muteaid on 2004-11-11
edit your  /etc/modules  files  and make sure agpgart and uninorth_agp  and r128 are listed in the module list


# sudo nano /etc/modules


add (if not already present)

uninorth_agp
agpgart
r128

---

### Post by Huxley on 2004-11-11
Thanks for the fast reply muteaid.

The result after adding
uninorth_agp
agpgart
r128
to /etc/modules

was

Xlib: extension "XFree86-DRI" missing on display ":0.0".
Direct rendering: No

---

### Post by muteaid on 2004-11-11
What does your XF86Config-4 look like?

---

### Post by gilgamesh on 2004-11-11
[QUOTE=muteaid]What does your XF86Config-4 look like?[/QUOTE]
 i've installed it on my ibook, it works but the arrow et now black. is it normal ?

---

### Post by Huxley on 2004-11-11
My XF86Config-4

---

### Post by sumanjay on 2004-11-11
[QUOTE=gilgamesh]i've installed it on my ibook, it works but the arrow et now black. is it normal ?[/QUOTE]
I assume you mean the cursor/pointer(?). Apparently, after coming out of sleep, X refuses to draw the cursor completely. I'm planning on filing a bug report after searching around a little more. An easy fix is logging out and back in. If that doesn't work, restart X using the Ctrl+Alt+Delete sequence. This is beginning to feel like one of the early Windows threads, where the cure for everything was "Restart the system".  :(

---

### Post by muteaid on 2004-11-12
here is what i got

---

### Post by TravisNewman on 2004-11-12
OK here's the interesting thing. I have an ati rage 128 in my G3 iMac running at 500 Mhz, using an external vga because the built-in died. I'm running in X at 1280x1024 at 24bpp, and I'm getting around 1500 fps in glxgears. Direct rendering is DEFINITELY on. I DO have 512megs of ram in it though, which could be part of it...

---

### Post by Huxley on 2004-11-13
Just reading this page
[http://geekounet.org/powerbook/driplusxv.html](http://geekounet.org/powerbook/driplusxv.html)

Any more installing to do for ppc support?

Thanks

---

### Post by sumanjay on 2004-11-13
Huxley, do let us know how it went. I'd just like to add that you might want to install Powerprefs using Synaptic so you can control the power-saving features of your Mac. Unless you'd rather hack the pbbuttons.conf file yourself. :grin: 
BTW, is your Powerbook a Lombard or a Pismo?

---

### Post by Huxley on 2004-11-13
Lombard - bronze 400

---

### Post by chascon on 2004-12-11
The problem with enabling accel, as what happens when you set the default to 16, is that the handling of accel, DRI, freezes the gui, keyboard and mouse on the imac slot loading imac from 1999 with rage 128 card. 

The problem has not been fixed in hoary (contrary to what is reported).  I updated to hoary and enabled accel to suffer the same freeze and having to hardboot (Fri Dec 10, 2004).

I encourage the mac hardware community to actively report bugs as this is the ONLY way we're to get a decent alternative to apple's OS (OS X being optimized for their [apple's] new hardware [and no I do not wish to argue this.  I know from personal experience]).  I say "ONLY" because our numbers work against us, whereas the pc community is so large that I believe their complaints are heard loud and clear because of their numbers.  This is not swipe at ubuntu but simply a realistic look at the facts.  I encourage that everyone try out even software that does not interest you as it'll help someone else who is interested.  For instance, I gather that not too many users are intersted in the audio alternatives that ubuntu-ppc offers because people have good aple alternatives (or because they are using ubuntu for other reasons than to play CDs, or just use MOL defeating the imputus to improve linux-ppc sound, etc), but for others that do not want to run OS X on old hardware, we're stuck with half baked sound apps.  For instance Rhythmbox freezes when listening to stations, xmms EQ doesn't work, xmms's volume seems to be circumscribed.  Volume can't do a gradual decrease in volume either.  Gstreamer is a headache, totem-xine is not part has not been ported to the official ppc repository.

When I report these problems I've gotton ushered to forums etc as if I don't know how to handle these apps or as if my concerns are not valid.

I'm tired of feeling that I'm a second class citizen in gnu-linux being that ppc hardware is supperior to pc (go to penquin ppc to learn if you disagree). 
Ironic isn't it?

The only thing I've gained from comeing from debian-ppc is that my scanner now runs non-root, but I've had to sacrifice accel.  I'm not sure I like this trade-off. I could stay with OS X and get crappy accel support and at least some scanner support, buggy as it is.  But this continues a dependence on propierttary software.  Yes, I know part of OS X is open, but I wouldn't even take money to run just darwin by itself.  Would u?  And yes I have run just darwin with kde over it so I know what I'm talking about.

Be loud and be heard to improve linux-ppc
Participate proactively in the reporting of bugs in the ubuntu bugzilla till the point of them getting sick of us.  Only then will we have a ppc distro tht we can proudly encourage to our fellow macppc users.


Chason

---

### Post by luboshiq on 2004-12-12
I agree. I have iMac G3 with slot-loading CDRW and my graphic acceleration is poor compared to Mac OS X. I tried to switch to 16bit color depth, but my X crushed. I wish next release will fix this and finally allow me to play some 3D game. I think installer should handle this, not me. I just want my ati rage 128 to work.

---

### Post by Castaa on 2004-12-12
Boy I was really hoping this would fix my xine DVD movie playback problem (dropped video frames) but no such luck.
 
 
Thanks for the tip though!  OpenGL 3D acceration now appears to work and it's orders of magnitude faster!

---

### Post by Huxley on 2004-12-12
Open Graphics Project.

Have ppl read about the open source graphics card project?
The mailing list would be a great place to ask about ppc linux support.

Some info at osnews.com
[http://www.osnews.com/story.php?news_id=9003](http://www.osnews.com/story.php?news_id=9003)

More on the project, mailing list archive and the slashdot.org link are at
[http://lists.duskglow.com/mailman/listinfo/open-graphics](http://lists.duskglow.com/mailman/listinfo/open-graphics)

---

### Post by slux on 2004-12-14
I'm not so sure a open graphics card is going to do much good with Mac hardware as one seldom puts  a mac together out of custom parts...If you're looking for well working GNU/Linux hardware and only want it to be PPC, no particular preference for apple, you could look at [Pegasos](http://www.pegasosppc.org/) .

But lets report our problems and participate in making Ubuntu a great PPC distro. It already shows a lot of promise in my opinion and isn't that far from being great. :)

---

### Post by Castaa on 2004-12-17
Pegasos.  That looks neat.  Does anyone actually use that hardware?

---

### Post by slux on 2004-12-17
I've seen a few of them demoed with (IIRC) the both available operating systems. Looked pretty nice (the stock case) and seemed to be working fine but then I didn't try them out so much. I'd imagine it's a fine little piece of hardware but the price is somewhat more than you'd need to pay for a considerable mac I guess. Still cool, I might even get one if I was on the market for a PPC desktop. Wonder if they'll make G5 versions. :)

---

### Post by chascon on 2005-01-03
This is what works for me on debian-ppc for my old iMac DV slot loading 400 mhz with a Rage 128 VR.  Maybe someone could try this on their iMac if they are at their wits end.  Remember ubuntu activiely discourages mixing debian with ubuntu so take responcibility.  I'd do this myself if I didn't have my debian-ppc running nicely.

Please post results.


What woud be intersting is if one went to F1 (cntrl-option F1) and as su added 
deb [http://people.debian.org/~daenzer/dri-trunk/](http://people.debian.org/~daenzer/dri-trunk/) ./

update: I tried this with (seems better suited for ubuntu-ppc):

deb [http://people.debian.org/~daenzer/dri-trunk-sid/](http://people.debian.org/~daenzer/dri-trunk-sid/) ./
deb-src [http://people.debian.org/~daenzer/dri-trunk-sid/](http://people.debian.org/~daenzer/dri-trunk-sid/) ./

to the
/etc/apt/sources.list
did a
 apt-get update
then uninstalled xserver-xfree86 and installed xserver-xfree86-dri-trunk
[the recommended package by apt-get xlibmesa3-dri-trunk is replaced with xlibmesa-gl1-dri-trunk in daenzer's sid xserver]

-removed rss-glx
-removed xscreensaver-gl
-turn off xscreensaver latter in X 
or even remove xsceensaver (there will be a warning about a dep named desktop? but I've been told this is only a place holder so this should be nothing to worry about)
(on debian-ppc make sure you don't have: xscreensaver xscreensaver-nognome xscreensaver-gl)

X Config
then change default depth to 16 in XF86Config
-make sure "Load DRI" is enabled
-maybe make sure r128 is included rather than ati as driver (for the Rage 128 video card)

PS-the default xfree86 in debian-ppc freezes the screen, as does installing xscreensaver xscreensaver-nognome xscreensaver-gl so there seem to be two issues here in debian-ppc at least.  Ubuntu dev please take heed and maybe talk to Daenzer (Mr.Cooper?) to ask why he made his branch of xfree86 and how it works.  And maybe pick up an old iMac with the said video card.  They are cheap.

Oh and panickedthumb, you mind posting your XF86Config file so that we all could benefit from your discover of 1500 fps?

The below is not a bad idea, although I have never noticed a diff doing this:

# sudo nano /etc/modules
if not already present add

uninorth_agp
agpgart
r128

If XF86Config says r128 then this should be r128 else if it says ati, then I imagine this should say ati

---

### Post by daniels on 2005-01-03
[QUOTE=Castaa]Pegasos.  That looks neat.  Does anyone actually use that hardware?[/QUOTE]No.  I have one under my desk, however.

---

### Post by chascon on 2005-01-03
In addition to my above posted message concerning the debian-ppc "xserver-xfree86-dri-trunk" to hopefully stop X from freezing.

maybe add: xlibmesa3-dri-module-trunk
and
drm-trunk-module-src
and
xfs
and
libglide3 if you can find it.  I couldn't.  But there is a libglide3-dev
Stay away from opengl stuff.  Seems mesa is the way to go for my comp.
You might want to try xlibmesa-gl too (upon checking i already have it.  It might have gone in as dep with something previously installed).  These tid bits should pop up as suggested and recommened when you apt-get install the above ignore the recommendation to install xserver as the "xserver-xfree86-dri-trunk" is the xserver; I don't know why it recomends this even when one is already in X! 

chascon

PS-I never had these troubles with mdk-ppc but mnk-ppc may be defunct and it does not benefit from official support post-9.1 or so.
PS-Once again, buy some old macs devs

---

### Post by daniels on 2005-01-03
There have not been any actual bug reports on this matter.  Furthermore, original iMacs are around $au300 on eBay.  We can't own every computer ever made, y'know; I'm making do by running 2xi386, amd64, sparc, and powerpc in my house alone, which I thought was a reasonable effort, but apparently not.

---

### Post by chascon on 2005-01-04
I myself reported this bug (Rage 128 freeze when enabling DRI) in bug 4125 ([https://bugzilla.ubuntu.com/show_bug.cgi?id=4125](https://bugzilla.ubuntu.com/show_bug.cgi?id=4125)).  You yourself deemed it a duplicate of 2411 ([https://bugzilla.ubuntu.com/show_bug.cgi?id=2411](https://bugzilla.ubuntu.com/show_bug.cgi?id=2411)).  It was then reported as fixed in hoary.  I dist-upgraded to suffer the system freeze with DRI enabled in hoary.
So no, this problem has been reported ubuntu bugzilla and as my documentation in thos reports show, it is widely reported in other distros. So in answer to the question if there is a problem here, it's self-evident.

I took my own words and installed ubuntu-ppc last night again. I uninstalled xserver-xfree from console and installed xserver-xfree86-dri-trunk after adding the the appropiate source to the sources.list.
Removing xserver-xfree removes ubuntu-desktop, x-window-system-core, xfree86-driver-synaptics, and x-server-xfree86.  I also removed xscreensaver, xscreensaver-gl, and rss-glx.  I then configured XF86Config-4 to detail Driver r128, and set the default depth to 16.  I then added agpgart, uninorth-agp, r128 to /etc/modules and reinstalled x-window-system-core.

The result?
I have X with accel now, glxinfo | grep "direct rendering" puts out "yes" and it hasn't crashed all night.
To be fair, I've gotton accel working without the /etc/modules stuff, but apparently it shoud work better with agpgart, uninorth-agp, r128 added to  /etc/modules.  

The only issue, if it is one, is that I can't install the recommended libglide2 and drm-trunk-module as they seem to be obseleted or simply not in the repositories I have in sources.list.  I know I can get them from the debian-ppc ones but not sure if I should do this (ramifications?).  Yes I know libglide2 is old.  (Funny thing is that debian-ppc sarge suggests libglide3 not 2 during this process.)

Of course, the other concern is how will this affect an upgrade to hoary.  I guess to be on the safe side one could remove xfree86-dri-trunk and then dist-upgrade.  Then check thru to see that no undireable packages were installed during the upgrade post-upgrade.  I'm sure there is an elegant wa to do this.  Please feel free to add.

Chascon

PS-I apprecite your enthusiasm daniel but there is obviously a problem with the Rage 128 VP on mac-ppc.  I just happen to be one of the few ppc users that is bothering to report this problem.  But this does not mean it doesn't exist as luboshiq himself has reported in this thread.  By the sounds of it, he has the same model as mine, " iMac G3 with slot-loading CDRW ... Rage 128", but with the CDRW.  This would have been the Grey iMac slot loading from 1999, the step above mine with a CD-RW built in rather than just the CD/DVD reader I got.

And panicedthumb about, "I'm getting around 1500 fps in glxgears", I can't believe this is fps.  You're reading frames per five seconds as that is approx what I get for frames per 5 secs (I get 2000 actually).  If you look over t the right, you'll actually read frames per second are something like 405.600 fps and I have double the ram you have, which makes it more unlikely you're getting 1500 fps.

---

### Post by chascon on 2005-01-04
sorry Rage 128 VR not VP.
I always makes this mistake

---

### Post by daniels on 2005-01-04
Sorry to be blunt, but if it's not in the bug tracking system, then I likely don't know about it (and if someone just tells me offhand, I'm likely to forget, being human and all), and if I don't know about it, then as far as I'm concerned, the problem doesn't exist.

(And I managed to miss all the additional comments on that bug for whatever reason; part of it probably to do with the fact that yesterday was my first back after a fortnight's holiday.)

---

### Post by dkitty on 2005-01-06
Heh, I dropped by to mention that I tried sumanjay's recommendation but X froze. At first I thought I'd done something horribly wrong. I'm glad I'm not the only person using an iMac DV with rage128 (possibly VR, I'm not sure) who experiences this problem.

My explination probably wouldn't have been half as detailed as yours chascon. Your solution sounds a bit over my head, but I may try it.

---

### Post by chascon on 2005-01-07
Don't worry about configuring XF86Config-4 or the /etc/modules section at first, as a working system does not depend on this if you already had X working.  Just get through the replacing default xserver, replace it with daenzer's version, and uninstall the xscreensaver stuff. That should give you a working stable system.

You can take the other stuff (XF86Config-4 and /etc/modules) slowly at a comfortable pace as you learn to do it (use nano just as how you probibly edited to get accel working in the first place with the accel hack).  This is NOT essential because if they worked before the hack, they should work after.  You did have X up and running, so you probibly do not need to change you Xf86Config-4 file.  I only mention it because I'm demonstrating that one can both get accel going and have a stable non-crash system.  Meaning, not only that my hack works, but I'm demonstrating that Ubuntu-ppc has actual (real) problems with the iMacs with the ATI Rage 128 vidieo cards (at least).  I appreciate your comment as at one point I too thought that I was alone or that perhaps it was my particular machine that had issues.  Intersting how people are comming out of the wood works.  Make your voice heard and participate in the debugging at [https://bugzilla.ubuntu.com](https://bugzilla.ubuntu.com)
I've already shown you the links where this bug and the bug numbers (se this thread earlier) if the links don't work (really one like it because it wasn't the same bug as the fix did not fix it) is being tracked.  Follow it and please feel free to add anything.  I understand that the ATI Rage 128 works on the pc side, so I gather that at first there seemed to be disbelief that this was a Rage 128 problem (to others: please don't argue this because I can provide documentation).  Anyway, what I'm trying to say is, make yourself (meaing your iMac with a Rage 128) known and counted at bugzilla.

  I've said it before, this is the only way we're to get a linux-ppc distro that we can proudly recommend to our fellow mac users.

---

### Post by daniels on 2005-01-07
The problem is actually with the hardware -- the monitor doesn't provide us with any sensible way to access its sync ranges.  But I'm pretty sure I know what the fix is, and it'll be in the next revision of xorg (due earlyish next week).

---

### Post by chascon on 2005-01-07
That's great news Daniel!  I look forward to the fix.

I gather this fix will take care of both the DRI problems that xscreensaver demonstrates and the xfree issues demonstrated by freezes when operating non-daenzer xservers.

Maybe I'll upgrade to hoary when it's implemented to try it.

---

### Post by daniels on 2005-01-07
The freezes are a separate problem, and I'm going need to dive into the Fedora RPMs for the fix; should still be in next week's revision, though.

---

### Post by Patchoulol on 2005-01-08
chascon> I followed your instructions but now the system is extremely slow and completely unusable (and hangs very quickly) :(
When I set the default depth to 24 bits, it is fine, but the DRI doesn't work.

I noticed that when I installed xserver-xfree86-dri-trunk, xserver-xfree86 was re-installed...

I have an iMac DV SE 500Mhz (RAM : 256Mb)

My sources.list :
> deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview powerpc Binary-1 (20041020)]/ unstable main restricted 

deb [http://people.debian.org/~daenzer/dri-trunk/](http://people.debian.org/~daenzer/dri-trunk/) ./ 

# deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) unstable main contrib non-free  
# deb [http://non-us.debian.org/debian-non-US/](http://non-us.debian.org/debian-non-US/) unstable/non-US main contrib non-free  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 


My XF86Config-4 :

> # XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"macintosh"
	Option		"XkbLayout"	"fr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
	Driver		"r128"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	HorizSync	60-60
	VertRefresh	75-117
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
	Monitor		"iMac"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


Hope this helps :)

---

### Post by chascon on 2005-01-08
[QUOTE=][/QUOTE]
 Patchoulol: 
First of all, did you remove xscreensaver,xscreensaver-gl, and rss-glx?  I have the same issue when I enable accel and still have xscreensaver,xscreensaver-gl, and rss-glx.  Make sure you install xlibmesa2-dri-trunk also.  So all this from console (ie., alt-cntrl-F1) so you don't risk freezing.

I had a quick review at my Config-4 and the only difference there I spot is that I have the ati Rage 128 VR not Pro.  It could be that this work around only works for the the VR version of the card.  My system is slower but still very usable (but I have a gig of ram) and it is very stable now.

I just noticed that you have multiverse and universe enabled.  I have not tested this with the workaround (I'm about to and should report back).  My guess is that it is the multiverse might have something to do with the unstableness as this stuff is not supported (but then again so isn't this hack).  As I humbly see it, potential issues here could be: unsupported software, little ram, and and different Rage 128 card (or a combination).  I suppose my system is still fairly speedy because I have lots of ram and because I managed to enable accel to compensate

To recap (check in this order): 
-remove xscreensaver,xscreensaver-gl, and rss-glx?  Make sure you install xlibmesa2-dri-trunk also.
-try it with only main software for now
-then try to enable accel, if successfull you'll be able to offset some of the speed lag.
-run it for a few days; test it out including doing ordinary things you do (that iniciate the problems).
-If that works out then, try to put some restricted stuff back in, but slowly so that you can figure out what might be causing the instablility if it isn't the fact that you didn't remove the xscreensaver stuff in the first place.
-Assuming it isn't an incompatibility of the card with this work around, I imagine you should find a solution somewhere in the above list.

Finally, stick some ram in there.  Do some research but I think you'll find out that you might be able to stick a gig of ram in even though I think it was probibly only originally supposed to take 0.5 gig, mine was (might be useful if not now, down the road).  There's a mac app made by a weird mac kid from th U of Alberta in Canada called mactracker? (there's also a website by the name and last I heard they were in talks about purchasing the rights) that should be able to tell you everything you want to know on macs such as ram.  Run it on OS X (I assume you have a dual boot).  There is also apple-history? but I don't know if they keep to date or just regurgetate apple specs at the time of production.  

Hope this helps.  

I run at 16 rather than the supposed 24 my card is supposed to run at.
If it helps, here is my Config-4 file:
 Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
#	FontPath	"/usr/lib/X11/fonts/CID" #told to delete this in any file with this line.
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 (RL/VR AGP)"
#	Driver		"ati"
	Driver		"r128"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"iMac"
	HorizSync	60-60
	VertRefresh	75-117
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 (RL/VR AGP)"
	Monitor		"iMac"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

AND and my sources.list

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview powerpc Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb [http://people.debian.org/~daenzer/dri-trunk/](http://people.debian.org/~daenzer/dri-trunk/) ./

---

### Post by daniels on 2005-01-08
For what it's worth, I have a Rage 128 in my PowerPC system now, and it seems to work fine.  And Fedora don't have any fixes for any r128/GL lockups.

---

### Post by chascon on 2005-01-09
Daniels: What model are you running?  Maybe we assume too much to think it is an issue with Rage 128 but something else with iMac DVs.  You're running hoary right and have accel enabled?  Can you post you Config-4?

I spoke to the fedora-ppc guys at irc and drbyte hasn't tested his iMac DV with accel (I now doubt they have a fix because ydl4, which is a fedora-port also suffers from the same problem [they disable dri from the install onwards presumably to get around this]).  Mandrake-ppc 10.1 was stable in this respect so they might prove more useful to look into.

While you're comparing with other distros for fixes, you might also look into gentoo-ppc (just a fix to enable accel and presumably without lockups):

[http://forums.gentoo.org/viewtopic.php?t=262889&sid=cef79c4d8a9bf7375c8faf64663c0753](http://forums.gentoo.org/viewtopic.php?t=262889&sid=cef79c4d8a9bf7375c8faf64663c0753)
claim it has found a fix:
"Looks like the x11-drm package is broken for PPC as well. Will wait for the bug to be resolved before proceeding

Frank
Back to top 	
View user's profile Send private message
russofris
Tux's lil' helper
Tux's lil' helper


Joined: 14 Sep 2003
Posts: 89

	
PostPosted: Wed Dec 15, 2004 3:06 pm    Post subject: 	Reply with quote
So I now have hardware acceleration. The solution was to....

Download the latest DRI snapshot (common and mach64)
Extract it to /usr/src
Switch to gentoo-dev-sources as mm sources are missing symbols
compile the new kernel with DRM support
Go to usr/src/dripkg and run the installer for the mach64 kernel module
re-emerge x.org cause the dri whiz-bang installer coppied some i386 binaries (libGL.so) to my box."

Hope this helps to figure out what the prob is.  Looks like what ever the prob was, it seems to have been been fixed with the latest DRI snapshot (looks like you're right about it being a DRI issue).  There also seems to be some other issues perhaps of their own going on too.

Not sure about the model, but notice that the issue is also with an old Mac.

Chascon

---

### Post by daniels on 2005-01-09
I don't have an iMac, I have a Pegasos.  But I'll dive into Mandrake's RPMs.

---

### Post by chascon on 2005-01-09
Daniel: I don't know so I'll ask, are the standard mandrake rpms for PSs going to be different on a substantial level from the mandkrake-PPC ones in respect to this problem?

---

### Post by chascon on 2005-01-11
I just found a new dri-trunk xfree for sid which might prove faster.  Daniel:  So apparently what ever modifications the dri-trunk has, it hasn't made it into the reg debian x11 else there would not be dri-trunk for sid (I believe the earlier dri-trunk came out around the time of woody).  I'll try it tonight.

I'm going to try just to change the sources.list then perform an update.
I'll post as to how it goes, concerning accel and speed, gen, performance, etc.

From: [http://lists.debian.org/debian-powerpc/2003/02/msg00019.html](http://lists.debian.org/debian-powerpc/2003/02/msg00019.html)
Read the thread too.

"On Mon, 2003-02-03 at 14:26, Michel Dänzer wrote:
> deb     [http://people.debian.org/~daenzer/dri-trunk/sid/](http://people.debian.org/~daenzer/dri-trunk/sid/)        ./
> deb-src [http://people.debian.org/~daenzer/dri-trunk/sid/](http://people.debian.org/~daenzer/dri-trunk/sid/)        ./

Actually, I just changed that to

deb     [http://people.debian.org/~daenzer/dri-trunk-sid/](http://people.debian.org/~daenzer/dri-trunk-sid/)        ./
deb-src [http://people.debian.org/~daenzer/dri-trunk-sid/](http://people.debian.org/~daenzer/dri-trunk-sid/)        ./

hope this didn't cause any inconvenience.


-- 
Earthling Michel Dänzer (MrCooper)/ Debian GNU/Linux (powerpc) developer
XFree86 and DRI project member   /  CS student, Free Software enthusiast"

---

### Post by chascon on 2005-01-13
Patchoulol: you might want to use daenzer's xserver sid as it shoudl be more suitable for ubuntu-ppc.  I get more speed out of having it installed on my iMac.  If you still have the older version of daenzer's xserver, just hop into console and add the sid versions of xserver to sources.list, comment out the old entries, save, apt-get update, then sudo apt-get remove xserver-xfree86-dri-trunk xlibmesa3-dri-trunk, install xserver-xfree86-dri-trunk xlibmesa-gl1-dri-trunk

You can read the updated posting above where I first? proposed this.  It says "updated" a few lines from the start.

---

### Post by Huxley on 2005-01-16
Thanks for all the work.
Any news?

---

### Post by daniels on 2005-01-16
It's apparently fixed in Mesa 6.2.x branch, which I'm pulling for a whole swathe of updates that should also include this fix.  Unfortunately I was sick for a couple of days last week, so I didn't get to it as soon as I hoped (also, the fix wasn't as straight-forward as I thought it might be).

---

### Post by daniels on 2005-01-19
I'm hearing reports that 6.8.1-1ubuntu11 fixed it -- you might want to give that a shot.

---

### Post by chascon on 2005-01-22
"I'm hearing reports that 6.8.1-1ubuntu11 fixed it -- you might want to give that a shot."
Is this xorg?  Is it in hoary?
I guess I could install it into warty and hten pin it.

---

### Post by daniels on 2005-01-22
Yes, yes, and that would be unwise.

---

### Post by Patchoulol on 2005-01-22
chascon : I did all you wrote but always have the same problem. Here is the end of my /var/log/XFree86.0.log 
```
(EE) R128(0): Idle timed out, resetting engine...
(EE) R128(0): Idle timed out, resetting engine...
(EE) R128(0): Idle timed out, resetting engine...
```

---

### Post by Patchoulol on 2005-01-22
Then I installed xorg 6.8.1-1ubuntu11 , but it freezes completely (black screen with nice colors at the bottom :p) and there are not even the lines I quoted above in the log...

---

### Post by chascon on 2005-01-23
I'm at a loss.  I guess this hack a little more model specific than I'd like.
I don't know what to say but to try debian-ppc.  It works great for me (with kde), but this me too again.  Really the daenzer xserver works well for on debian-ppc.  But if that doesn't work for you there is also the default xserver from the main repositories.

The install is basically th same as the ubuntu-pcc.  A few more questons.  I usually go in and do a basic install first (no X).  Then I apt-get my xserver, and do a min kde install.  After that I can add kde packages that are allocated into groups.

Anyway that's my way, but you can get a desktop right from the start if you select desktop when prompted.  I just don't like doing that 'cause I like to put things in myself.

print off your xconfig-4 just in case you have to manually hack the config in debian.
 
I'm guessing because debian is older that you might get better luck with support.
Stay away from xscreensaver and opengl screensavers as this same problem can act up in debian (for me anyway).  Oh, and the reg xserver also locks my computer up too.

Have you thought that maybe you're experiencing a different bug?

---

### Post by Patchoulol on 2005-01-23
Thanks a lot for your help.
But I don't want to spend more time resolving unsignificant bugs for me : my linux desktop is already perfect for my needs, and apparently I don't have the same bug as you.
FYI I ran debian unstable until september and don't want to re-use it as there are too many bugs (and too few support) with the packages (I remember that in the end alsa didn't work anymore).

---

### Post by chascon on 2005-02-16
I would never run debian unstable (sid; Only daenzer's sid xserver package).  Sarge is pretty stable, and it is "close" (debian sense here) to being claimed officially stable.
So to clarify, I used to run debian sarge with daenzer's sid xserver.  It was a mix and it ran well.  Only I never made my scanner work as reg user.  This seems to be a cross-linux distro problem in general, except for ubuntu.

Hey daniel,
I found  something at:
[http://d-i.alioth.debian.org/manual/en.powerpc/ch05s01.html](http://d-i.alioth.debian.org/manual/en.powerpc/ch05s01.html)

"5.1.6. PowerPC Boot Parameters

Many older Apple monitors used a 640x480 67Hz mode. If your video appears skewed on an older Apple monitor, try appending the boot argument video=atyfb:vmode:6 , which will select that mode for most Mach64 and Rage video hardware. For Rage 128 hardware, this changes to video=aty128fb:vmode:6 . "

Would video=aty128fb:vmode:6 make a difference?

update:
come to think of it, googling the above line found this:
"> Many thanks for this, it wasn't a complete solution but it put me on the
> right track, I'm grateful.
>
> For the benefit of anyone Googling this group later on, here's my fix.
> -uncomment the "Load dri" line as Colin suggested
> -put this in the "Device" section of the XF86Config,
> Option "UseFBDev" "true"
> -in /etc/yaboot.conf remove any existing "append=video" lines and replace
> with this,
> append="video=aty128fb:vmode:6"
> -run ybin to install the modified yaboot.conf, reboot and startx
>
> All should now be well :)) "
Can someone try this?
(teh original poster suffered from crashes if this was set up correctly)

---

### Post by chascon on 2005-02-22
Thought below taken from a irc chat might shed some light.
This below was meant for the devs,

Topic for #mandrake-ppc set by spturtle at Thu Dec  9 18:06:05
<Faustus> hi
<Faustus> any one running a iMac DV in?
<Faustus> I want to know if yaboot.conf lists "append="video=aty128fb:vmode:6"
<stew_b> I don't know that people are using video= kernel arguments so much anymore
<-- cminyard has quit (Remote closed the connection)
--> cminyard (~cminyard@c-24-1-209-28.client.comcast.net) has joined #mandrake-ppc
<Faustus> I'm trying to figure out why most distros screw iMac with rage 128 up.  enabling accel ends up on X freezing
<Faustus> Mandrake-ppc doesn't have this problem now, with 9.1 the default kernel had this problem but the alternatibe ben Herrenschmidt didn't
<stew_b> yeah, I remember r128 had issues on 9.1
<Faustus> do you recall what the problem or solution was?
<Faustus> beyond using hte ben kernel  What was the difference between the stock and ben kernel?
<Faustus> I think I might be viewing two problems.  One seems to be a dri or X problem that most distros have and the other a kernel one.  I'm wondering if they are related.
<stew_b> Faustus: well the madrake kernel is patched quite heavily, and probably was using different driver code than BenH's (although I think I tried at one point to patch in from his tree)
<stew_b> mandrake* kernel
<stew_b> X is also patched, so you'd have to review the differences in the sources

---

### Post by JLF65 on 2005-02-23
I'd just like to chip in on this thread. I just installed Warty on my iMac DV+ 450MHz G3. It runs like a charm as long as you leave it in 24bit mode. Switching to the r128 driver and 16bit causes it to freeze when X starts up. I get a black screen, the X cursor appears, then the bottom half of the screen turns green and everything is frozen.

---

### Post by chascon on 2005-02-25
yes it runs fine at 24 default depth but without graphics acceleration.  That's the point, we want acceleration.  And you can't do this at 24 but at 16 (the problem is that it locks up at 16).  So we're forced to pick between no accel or accel with crashes.  Not much of a choice as anyone would choose to run at 24 and forego the lockups, but there should be the freedom to run at 16 with accel and without lockups.

---

### Post by chascon on 2005-03-26
Update:
It's been a while since there has been any input here.
I am pleased to note that as of March 25, 2005 hoary handles accel fine!
Let's hope that this keeps till the official release!
Thanks Daniel and all others who looked into this and more such as looking into other distro's drivers.

Just be sure to set a default depth of 16 in xorg.conf rather than the XF86Config-4 under /etc/X11/

I still don't trust xscreensaver, rss-glx, and any related screensavers.  Even when I did get accel going without freezing on Debian, having xscreensaver and related screensavers installed would undermine previous gained stabiility with accel enabled.

 To uninstall this stuff you'll have to uninstall ubuntu-desktop but this is just fine as it is only a place holder. If someeone wants to test these with accel enabled, be my guest but please report back.

 ... and just a recommendation, install xfce4 rather than gnome, it's better suited for these older iMacs with lesser processing power.

Just for reference, I did a dist-upgrade from warty to hoary.  If you installed daenzer's xserver make sure you uninstall it and all if any related software was installed.  I had a hard time upgrading (stuck between a warty and a full hoary version) untill I uninstalled a certain dri package I'd forgotten about (xlibmesa-gl1-dri-trunk).  And make sure you have 'locales' as the upgrade seems to forget to install this, leading to complaints when you install apps.  I had to do a sudo 'apt-get -f install' to fix dep problems once, maybe twice.  I think what helped me get there partially is doing a sudo 'apt-get upgrade' before 'sudo apt-get dist-upgrade'.  I don't know why but the two commands seemed to run differently, 'apt-get upgrade' allowed upgrading and holding problematic software that would cause 'apt-get dist-upgrade' to crap out.  Anyway, 'apt-get upgrade' allowed me to get partiall up to hoary.  'apt-get -f install' fixed some problems with 'apt-get dist-upgrade'.

To be clear, I'm not sure why these two commands should evoke different programs to be installed as one would think that once having upgraded to hoary (or something close to hoary as in my case) both commands should simply do the same thing, update software.

PS-Daniel, what was the problem?  Not being able t access the monitor's sync rates?  But aren't these problems of inaccesability typical of even older monitors, and not supposed to be a problem with a monitor from 1999?  Or was it a DRI issue?  Driver issue? xserver?

---

### Post by shadie on 2005-03-27
Just finished the upgrade to Horty, still no hardware acceleration on a Powerbook "Lombard", changed to 16 bit as per the last post.

Glxgears FPS has improved from 40 to 67, but still no tuxracer  :-k 


Any ideas?

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. 3D Rage LT Pro"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by Patchoulol on 2005-03-28
chascon> Good news!

Could you post your xorg.conf?

---

### Post by daniels on 2005-03-28
i didn't actually merge any fixes for this, so it was probably a kernel issue that got fixed at the drm layer

---

### Post by chascon on 2005-03-28
Here's my xorg.conf that works with accel on my iMac 400 DV Rage 128 via Hoary.  Hoary seems to have taken it verbatim from my previous XF86Config-4 file in Warty.

# XF86Config-4 (XFree86 X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the XF86Config-4 manual page.
# (Type "man XF86Config-4" at the shell prompt.)
#
# This file is automatically updated on xserver-xfree86 package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xfree86
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands as root:
#
#   cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.custom
#   md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/XF86Config-4.md5sum
#   dpkg-reconfigure xserver-xfree86

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
#	FontPath	"/usr/lib/X11/fonts/CID" #told to delete this in any file with this line.
	FontPath	"/usr/lib/X11/fonts/Speedo"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xfree86"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage 128 (RL/VR AGP)"
#	Driver		"ati"
	Driver		"r128"
	VideoRam	8834
	Option		"UseFBDev"		"true"
	Option		"AGPMode"		"2"    
# The below are taken from the net but [http://www.xfree86.org/current/r1286.html#6](http://www.xfree86.org/current/r1286.html#6) doesn't show as options.
#	Option		"AGPFastWrite"		"true" #experimental,freezes X as of sept 2003 but "works" w/rage128
#	Option		"EnableDepthMoves"	"true" #should be fine for rage 128
#	Option		"EnablePageFlip"	"true" #crashes iMac Rage128 w/ sarge & daezner's X, Feb16,2005
#	Option		"backingstore" 		"true" #from Xorg config for Radeon9200 but wrks w/ above line's setup
#	Option 		"RenderAccel" "true" #[http://www.esdebian.org/forum/viewtopic.php?forum=3&showtopic=10918](http://www.esdebian.org/forum/viewtopic.php?forum=3&showtopic=10918)
EndSection

Section "Monitor"
	Identifier	"iMac"
	HorizSync	60-60
	VertRefresh	75-117
Modeline "1024x768"     78.80   1024 1052 1148 1312    768  769  772  800 +hsync +vsync
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 (RL/VR AGP)"
	Monitor		"iMac"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

#for radeon 9200 except maybe Option DAMAGE ...
#Section "Extensions"
#      	Option "Composite" "Enable"
#  	Option "RENDER" "true"			 
#  	Option "DAMAGE" "true"			 
#EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by philip987 on 2005-03-29
I have followed this thread for a few months now hoping to get DRI going on an iMac DVSE with 256M ram. I am running hoary with xorg.  I have checked /etc/modules for
uninorth_agp
agpgart
r128

I have removed xscreensaver and glx-rss

I have edited my xorg.conf file as described by chascon (and many others) but whenever I set my default depth to 16 the x system slows down so much as to be unusable, taking over 2 minutes from a logon to the point that you actually get a desktop. I have enabled the Driver options that were comented out in chascom's posting and they havn't caused any crashes in 24 bit mode yet (its only been a few hours) but none of them made the system work in a 16 bit mode

I am missing something here but I am not sure what :???:

Thanks
Philip

---

### Post by shadie on 2005-03-29
Just about to try a clean install on my Lombard 400Mhz, if DRI still does not work I can install on my Pismo 400Mhz, has anyone got it working on a Pismo yet with Hoary?, if so what steps were required except for changing the bitdepth from 24 to 16 in xorg.conf.

I wonder if it has anything to do with the "unknown" monitor type, will check that when it's rebuilt.


cheers

---

### Post by daniels on 2005-03-29
Another thing to try is 'Option "SWCursor"' in the Device section of xorg.conf.

---

### Post by philip987 on 2005-03-29
I enabled SWCursor in xorg.conf but alas, no improvment in performance when the default depth is set to 16 bit. The xsystem just slowly crashes away. On the positive side in 24 bit depth my fps rate in glxgears has improved to about 85fps from about 55 and the graphic performance seems "better". I am not sure if this is because of the SWCursor or the other driver options I have enabled from chascom's post :


# The below are taken from the net but [http://www.xfree86.org/current/r1286.html#6](http://www.xfree86.org/current/r1286.html#6) doesn't show as options.
# Option "AGPFastWrite" "true" #experimental,freezes X as of sept 2003 but "works" w/rage128
# Option "EnableDepthMoves" "true" #should be fine for rage 128
# Option "EnablePageFlip" "true" #crashes iMac Rage128 w/ sarge & daezner's X, Feb16,2005
# Option "backingstore" "true" #from Xorg config for Radeon9200 but wrks w/ above line's setup
# Option "RenderAccel" "true" #[http://www.esdebian.org/forum/viewt...showtopic=10918](http://www.esdebian.org/forum/viewt...showtopic=10918)

In 24 bit mode none of these options have caused any instant crashes of my system (iMac DVSE) yet.....but no dri

I suppose I will stay in 24 bit mode and watch this space. 
Thanks for the help

---

### Post by chascon on 2005-03-31
I wouldn't enable those options I had hashed.  Some of them are hashed because they crashed my computer.  Others are hashed because athough they didn't crash my computer, I didn't notice an improvement in performance, and/or I could not confirm that they did anything with the Rage 128.  Plus, I'm not even sure if Xorg supports these options, or how well as these are my XF86 days.

I think Daniel might have it right; It could be related to the kernel.  Just in case it is, 'uname -r' gives  2.6.10-5-powerpc
try running that kernel if you don't have it.

I would also confirm that you have the same modules I have listed in my config
Try enabling: Option "RenderAccel" "true", although this is supposed to be default.
Also do you have glx, dri, and that GLcore in Section "Module"? 

When trying to get accel going I found it helpfull to work with a plain jane config file, else it may skew results.  Once you got accel going, then you can add options one by one so that you trace any crashes to one particular option, and not misattribute crashes.

You don't have to run you comp for a few hrs to see if it wil crash.
A good test to see if your computer will crash with accel enabled is simply to run 'glxgears'.  It'll usually, in my experience, crash within seconds if something is wrong. 

Philip:
-Did you upgrade or install hoary off the bat?  Just so that we all know (but not sure if this woud make a difference, probably not), I upgraded.
-What does 'glxinfo | grep direct' say?
-which Rage 128 card are your running?  I've got the VP version.
 Rage 128 (RL/VR AGP)

Please report back as I'd like to know why I am having success and you don't.
You are running a iMac with Rage 128 right?  iMac DV ? iMac SE?

And I'm not sure about the changing the 'Monitor Identifier' from 'generic' to 'iMac'.  I haven't been able to get a system to work differently by doing this, but who knows.   
Try it.

---

### Post by philip987 on 2005-03-31
[QUOTE=chascon]I wouldn't enable those options I had hashed.  Some of them are hashed because they crashed my computer.  Others are hashed because athough they didn't crash my computer, I didn't notice an improvement in performance, and/or I could not confirm that they did anything with the Rage 128.  Plus, I'm not even sure if Xorg supports these options, or how well as these are my XF86 days.

       I have had then switched on for a few days now without any drama. I consider myself warned about this potential instability.  If things fall over I know where to be suspicous I was carefull about enabling them, doing it one option at a time, change to 16 bit, restart X, watch it crash, ssh via the network to change back to 24 bit, restart X and then the next option. Quite an exercise in recursion really. 

I think Daniel might have it right; It could be related to the kernel.  Just in case it is, 'uname -r' gives  2.6.10-5-powerpc
try running that kernel if you don't have it.

       I am running 2.6.10-5-powerpc, I updated it last week when I read that dri was working now!

I would also confirm that you have the same modules I have listed in my config
Try enabling: Option "RenderAccel" "true", although this is supposed to be default.
Also do you have glx, dri, and that GLcore in Section "Module"? 

       here is my modules list
Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

       I have the option of RenderAccel set to true. That was one of the options I had high hopes  for myself...Oh well

When trying to get accel going I found it helpfull to work with a plain jane config file, else it may skew results.  Once you got accel going, then you can add options one by one so that you trace any crashes to one particular option, and not misattribute crashes.

You don't have to run you comp for a few hrs to see if it wil crash.
A good test to see if your computer will crash with accel enabled is simply to run 'glxgears'.  It'll usually, in my experience, crash within seconds if something is wrong. 

Philip:
-Did you upgrade or install hoary off the bat?  Just so that we all know (but not sure if this woud make a difference, probably not), I upgraded.

      I upgraded from warty to hoary by changeing my apt sources

-What does 'glxinfo | grep direct' say?

      direct rendering no

-which Rage 128 card are your running?  I've got the VP version.
 Rage 128 (RL/VR AGP)

        I am not sure exactly The machine is a circa 1999 white (snow) iMac DV SE that has an ati rage 128PR I beleive. A very nice machine in its time.

Please report back as I'd like to know why I am having success and you don't.
You are running a iMac with Rage 128 right?  iMac DV ? iMac SE?

And I'm not sure about the changing the 'Monitor Identifier' from 'generic' to 'iMac'.  I haven't been able to get a system to work differently by doing this, but who knows.   
Try it.[/QUOTE]

my monitor was set to iMac here is the relevant part of xorg.conf

Section "Monitor"
	Identifier	"iMac"
	HorizSync	60-60
	VertRefresh	75-117
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
	Monitor		"iMac"


Thanks for you time and effort and it has been a good learning execise for me

---

### Post by JLF65 on 2005-04-16
I just did a clean install of the official Hoary release on my iMac DV+ 450MHz G3. Leaving it at a depth of 24 works, but without acceleration. Changing the depth to 16 causes it to hang just as it did in Warty.

I tried adding uninorth_agp, agpgart, and r128 to /etc/modules and changing the driver in /etc/X11/xorg.conf to "r128" with no change. Depth of 24 - fine. Depth of 16 - hang. It would be really nice if this problem got worked out. There are a lot of us iMac G3 users who would greatly appreciate it.

---

### Post by m.buchmeier on 2005-12-09
I have just installed breeze on my imac 
with "ATI Rage 128 Pro VR PR (PCI)" chipset
and found that X hangs in 16 bit mode as described in
this thread. Does anyone know how to get
16bit working ? I would like to have 1024x768
resolution which is not possible in 24bit mode.

---

### Post by hennewou on 2005-12-22
Same problem here. Also in Debian Sid

But I have to say that 15 bit works with the r128 driver (probably also with the ati driver). But when starting glxgears, it's fluenty for the first two seconds, but after those two seconds, it's shaky. 

I hope there would be someone who can resolve this problem. My Mac g3 works great in Linux, except for the video acelleration of course. I really like to try out luminocity, but I need hw-accell for that.

---

### Post by fatbuttlarry on 2006-12-21
First and foremost, thanks ubuntu / kubuntu for such an awesome OS.  Been using it for about a year now x86, x86-64, and now ppc.

Thanks to the posters too, this thread has provided a lot of insight on Rage 128 + DRI, and I've read every thread on these boards that I could find.

-----------------------------------

Sorry to bump a dead thread here, but I just did a fresh install of Ubuntu 6.10 on an iMac I just picked up and cannot get DRI functioning.  I've tried a few of the fixes, but still strange behavior.

First thing is PNGs become discolored upon reboot.  Not sure if all are affected, but restarting the X-Server fixes this.

6.10 defaults to 24 bit.  Perhaps the previous posts about DRI needing 16bit color are accurate even in 6.10.  Unfortunately, 16bit w/ DRI enabled hangs the X server, utilizing 99.9% CPU.

On 24bit color, DRI reports "direct rendering: No" even if its enabled in the Xorg.conf.


I noticed a bunch of the successful steps include older "XFree86"... I'm hesitant to replace the X server for obvious reasons... :-k 

Thanks in advance guys!

-FBL

---

### Post by fkdev on 2006-12-23
phillip987, I won't ensure GL will work even after this, but try adding this to xorg.conf, in the Device section of xorg.conf, along with 16 bit color.
This should, at least make xorg start, with direct rendering, at 16 bit color depth. GL apps might not work though, I don't know.
```

  Option "ForcePCIMode" "true"
```

---

### Post by Knoeki on 2007-05-11
> **sumanjay said:**
> 
1) Change into one of the Virtual Terminals using Ctrl+Alt+F1 (or Func+Ctrl+Alt+F1) and login with your username and password.
2) Type the following command to edit your XF86Config-4 file -
[CENTER]**sudo nano /etc/X11/XF86Config-4** [/CENTER] 
3) Move to the Section "Screen", which you can do either by scrolling down or by pressing Ctrl+W and typing "Screen"  into the search box.

when I did this, I just get [ "SCREEN" NOT FOUND ]

what should I do? I don't have much experience with linux  yet (just a bit of BASH under OSX)

I read through this thread, but it was all confusing for me...>.<

sorry about reviving an old topic...

---

### Post by fkdev on 2007-05-12
> **Knoeki said:**
> when I did this, I just get [ "SCREEN" NOT FOUND ]

what should I do? I don't have much experience with linux  yet (just a bit of BASH under OSX)

I read through this thread, but it was all confusing for me...>.<

sorry about reviving an old topic...
Those instructions are a little old, so here are some simple instructions on doing this now:
1. ```
 sudo gedit /etc/X11/xorg.conf 
```
2. Using gedit, change:
```
DefaultDepth 24
```
to 
```
DefaultDepth 16
```
3. To prevent xorg from freezing, add:
```
Option "ForcePCIMode" "true" 
``` in the Device section

Now see if dri works (run glxgears and see what happens). If it doesn't, then you'll have to disable it by either:
1. Change DefaultDepth back to 24
2. or remove ```
 Load "dri" 
``` from Module section

---

### Post by Knoeki on 2007-05-12
...I can't save the document (it says 'read only')...

---

### Post by dpny on 2007-05-13
> **Knoeki said:**
> ...I can't save the document (it says 'read only')...

Instead of 

```
gedit /etc/X11/xorg.conf
```

Type

```
sudo gedit /etc/X11/xorg.conf
```

You will be asked for your password. Just enter it.

---

### Post by Knoeki on 2007-05-13
> **fkdev said:**
> 
Now see if dri works (run glxgears and see what happens). If it doesn't, then you'll have to disable it by either:
1. Change DefaultDepth back to 24
2. or remove ```
 Load "dri" 
``` from Module section

okay... I can get it all to work, but how do I know if dri works? should I just be seeing the gears rotate? or?


oh yeah... after running glxgears, my cursor turned black...

---

### Post by Knoeki on 2007-05-14
Can anyone please confirm this? (sorry for the double post and stuff...>.>)

---

### Post by stmiller on 2007-05-14
> **Knoeki said:**
> okay... I can get it all to work, but how do I know if dri works? should I just be seeing the gears rotate? or?


oh yeah... after running glxgears, my cursor turned black...

The output of

glxinfo

should include a line at the top which says

direct rendering: yes

---

### Post by fkdev on 2007-05-14
As stmiller said, if glixinfo says direct rendering is enabled and glxgears doesn't crash your system, your good.

If your cursor keeps getting corrupted after running GL apps, try adding
```
 Option "SWCursor" 
```
to the driver section of xorg.conf (along with the ForcePCIMode option)

---

### Post by Knoeki on 2007-05-14
okay, I followed all instructions... when I ran glxgears, it crashed... so I removed load "dri" from the modules section, and now glxgears runs, but very slow.

also, after removing that, glxinfo said:

direct rendering: no


is this supposed to happen?

---

### Post by Knoeki on 2007-05-14
Okay, I follwed all instructions... I changed bitdepth to 16 and added Option "ForcePCIMode" "true",,, when I did that, glxinfo said 'Direct Rendering: yes'.
when I ran glxgears, the system crashed... so I removed 'load "dri"' as sugested..
now glxgears runs VERY slow, and glxinfo says: 'Direct Rendering: no'...

...and I still can't set my resolution higher than 1024x786 (which should be possible)...

*sigh* maybe I just need to find an other videocard... v_v

---

### Post by stmiller on 2007-05-14
3D drivers under PowerPC Linux are unstable for most. You are lucky you managed to get dri working. I disable dri just because it makes my machine unstable. :-(

---

### Post by Knoeki on 2007-05-15
well, when I have DRI working and the bitdepth on 24, it works fine, untill my screensaver goes on (system crashes). when I have DRI working and bitdepth on 16, my system crashes ~5 minutes after logging in...>.< so yeah... new videocard it is I guess...>.>


(oh, sorry for the double post above... first one may be deleted.. ^^)

---

### Post by DirtDawg on 2007-06-11
I have a red imac g3 with a rage 128 video card. I've been trying to get 3D apps runnig, but it's just not working for me. "glxinfo" gives me "direct rendering: no"

I have edited xorg.conf so my driver device reads "r128". I also tried the suggested method of changing my default depth to 16. However, this causes everything to run so slowly the system is not usable. Any time anything on the screen needs to be drawn, it takes up to 5 minutes or more. I couldn't even get into the failsafe terminal, so I had to use a recovery CD.

Should I just accept the fact that 3D (direct) rendering is a no-go on this computer? The more research I do, the more it looks like that's the case, but maybe I'm missing something obvious or maybe someone with a similar setup has managed to get 3D acceleration running?

Thank you

---

### Post by Jimbob17 on 2007-06-12
> **DirtDawg said:**
> I have a red imac g3 with a rage 128 video card. I've been trying to get 3D apps runnig, but it's just not working for me. "glxinfo" gives me "direct rendering: no"

I have edited xorg.conf so my driver device reads "r128". I also tried the suggested method of changing my default depth to 16. However, this causes everything to run so slowly the system is not usable. Any time anything on the screen needs to be drawn, it takes up to 5 minutes or more. I couldn't even get into the failsafe terminal, so I had to use a recovery CD.

Should I just accept the fact that 3D (direct) rendering is a no-go on this computer? The more research I do, the more it looks like that's the case, but maybe I'm missing something obvious or maybe someone with a similar setup has managed to get 3D acceleration running?

Thank you

Yeah, I've been messing about with an iMac 400MHz Graphite trying to get reliable graphics acceleration working, my conclusions are it's not possible on this machine. I can get direct rendering enabled by doing the 16 bit depth trick and adding some other bits to my xorg.conf but then the computer freezes after about 5 seconds (sometimes more, sometimes less) when testing glxgears or the other test glx program.

---

### Post by DirtDawg on 2007-06-12
> **Jimbob17 said:**
> Yeah, I've been messing about with an iMac 400MHz Graphite trying to get reliable graphics acceleration working, my conclusions are it's not possible on this machine. I can get direct rendering enabled by doing the 16 bit depth trick and adding some other bits to my xorg.conf but then the computer freezes after about 5 seconds (sometimes more, sometimes less) when testing glxgears or the other test glx program.

Okay thanks. As long as I know it's a lost cause I can move on with my life.

---

### Post by gvigorus on 2007-08-10
Hi. Is it confirmed that dri is lost cause? I've got 3D ATI Rage LT Pro on 400Mhz Lombard. Adjusted xorg.conf with 16 depth and "forcePCImode" true. When i run glxinfo it says dri no, but glxgears work, but slow. Nothing crashes:)
I'm on Feisty Fawn with Xubuntu....
Any progess anyone?! :)

---

### Post by Ripfox on 2007-08-16
I second this question.

---

### Post by rcxjflores on 2007-10-17
dropping the default depth was a major help! Thanks! :)

---

### Post by stream303 on 2008-05-28
Is this still an issue with Hardy?

---

### Post by Phonan on 2008-06-18
I installed Hardy CLI and did Fluxbox on that, and I'm still having problems. I tried all the steps, but glxgears and any other GL app freezes everything such that I have to force reboot. I have a Rage 128 VR and I hear this might be the problem. Is there any help for this? My hopes are up now that I've seen glxgears running smoothly, albeit for 2 seconds.

---

### Post by larsh on 2008-06-23
> **fkdev said:**
> Those instructions are a little old, so here are some simple instructions on doing this now:
1. ```
 sudo gedit /etc/X11/xorg.conf 
```
2. Using gedit, change:
```
DefaultDepth 24
```
to 
```
DefaultDepth 16
```
3. To prevent xorg from freezing, add:
```
Option "ForcePCIMode" "true" 
``` in the Device section

Now see if dri works (run glxgears and see what happens). If it doesn't, then you'll have to disable it by either:
1. Change DefaultDepth back to 24
2. or remove ```
 Load "dri" 
``` from Module section

hi
im new to linux and have installed 8.04 on a g3 ibook. Everything seems fine and im using it right now. but i get a 5cm black "frame" on the right side and the top of my screen is duplicated at the bottom. and i cant change to a resolution above 800x600. ive read alot in these forums but i cant really get anything to work. the latest ive tried is this defaultdepth above. but my xorg.conf doesnt say anything about defaultdepth. this is all it says.

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"

im not sure this is the fix anyway. glxgears runs fine. and glxinfo says direct rendering yes.

larsh

---

### Post by larsh on 2008-06-23
uploading a xorg.conf screenshot

---

### Post by stream303 on 2008-06-23
If you wanted to try a 16 - bit depth in Hardy, here's what it would look like after editing the "Screen" section:

```
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth 16
EndSection
```

I just logout and then log back in to see the change.  You may also need to manually specify your vertical and horizontal freqs, but this might be a start...

---

### Post by jbruder on 2008-06-24
I know this may be simplistic, but what would be necessary to reconcile the differences between the way video is setup for the ATi Rage 128 in 6.06 & 8.04? 

I installed 6.06 yesterday and it was great, except for the inability to run WPA encryption on the original airport card. 

There's a driver build for the newer kernel in 8.04 that may allow that, but without working graphics, what is the point?

I appreciate the help and support that the frequent users of this forum have provided. This is my first attempt at an Ubuntu install in a long time, and I've seen some of your names quite a lot in the last couple of days.

Edit: Haven't had my coffee yet, missed a verb or two.

---

### Post by stream303 on 2008-06-24
The thing to do here is to copy your existing /etc/X11/xorg.conf file to paper or usb disk etc, and then use the info from that as a starting point for manually editing the xorg.conf file in Hardy.  If graphics don't come up at all, you may have to get to a shell via CTRL-Alt-F1, or maybe even go into a rescue shell at the second-stage yaboot boot: prompt to do your editing.

With all distros moving to the new x server, they are trying to reduce the need for anyone having to manually edit their xorg.conf, and Hardy's xorg.conf looks quite bare.  Unfortunately, it appears that unless the manufacturers release more PPC info, we are going to be stuck editing it anyway.

I suppose you could just try and swap your old 6.06 xorg.conf into the 8.04 install and see how it works, although I'd be tempted to just add what the major things are, like monitor freqs, device driver, etc and test by looking at what shows up in /var/log/Xorg.0.log each time you add something.

It can be done, but it can be time-consuming if an xorg.conf swap doesn't work.  Coffee can help. :)

---

### Post by jbruder on 2008-06-27
Thanks much! It's a great suggestion and would work exactly as needed. I may still go back and look at the 6.06 xorg.conf to see if i can make any further improvements.

Fortunately, however, I was able to save a few minutes by taking a look at this post: 

[Working G3 imac xorg.conf]("http://ubuntuforums.org/showthread.php?p=4808544")

To make a G3 ibook work with 8.04, I made the changes suggested in the above link, and then switched to 1024 x 768. I haven't removed the splash yet, but I probably will - a full minute of darkness on startup is just a little unsettling.

---

### Post by DirtDawg on 2008-06-27
> **jbruder said:**
> Thanks much! It's a great suggestion and would work exactly as needed. I may still go back and look at the 6.06 xorg.conf to see if i can make any further improvements.

Fortunately, however, I was able to save a few minutes by taking a look at this post: 

[Working G3 imac xorg.conf]("http://ubuntuforums.org/showthread.php?p=4808544")

To make a G3 ibook work with 8.04, I made the changes suggested in the above link, and then switched to 1024 x 768. I haven't removed the splash yet, but I probably will - a full minute of darkness on startup is just a little unsettling.

Does this configuration allow for direct rendering, 3D, etc? Could someone please elaborate what this configuration actually improves? Thanks.

---

### Post by stream303 on 2008-06-27
The configuration shown in that link improves stability at the expense of 3d and dri - they are both disabled at the end of the configuration.

I think the key issue is that if you do want dri / 3d, with this card you'll have to drop your default depth down from 24 to 16 with a small reduction in stability.

---

### Post by Phonan on 2008-06-27
How about starting a new thread in the new Apple Users forum? I've been reading a lot about my particular problem with the GL freezing, and it looks like it's a problem deeper down than I'm comfortable with, involving Xorg and code problems, stuff I can't really fix. I think we may get more help posting in the new forum instead of reviving one from years ago. What do you think?

---

