---
title: "iBook G3 + Ubuntu"
date: 2004-10-19
forum: Apple PPC Users
---

### Post by darrenism on 2004-10-19
Has anyone installed Ubuntu on an iBook G3 and if so.. what are your experiences with it?

It would be nice to know what hurdles I'd need to jump beforehand.

---

### Post by Castaa on 2004-10-19
I'm installing Ubuntu 4.10 RC *right now* on my 600 Mhz iBook.  I'll let you know if I get it running. :D

---

### Post by Castaa on 2004-10-20
Ok it installed off the CD created via the v4.10 RC .iso image.  It also updated itself via the Internet as part of the second phase of the install without a problem.

It booted first try to a very clean looking Gnome GUI again without a problem.

Problems I did find was that video DVDs would not play at all with their DVD player Totem.  Neither would audio CDs with any of the audio playing programs that were installed.  However it did detect the CD and the displayed the correct album title song list for the CD.

I ripped a few songs off of a Pearl Jam CD and it took an almost an hour to rip one song to .ogg format.  Oddly when it was ripping the CPU utilization was only 20%.  Maybe the CD-ROM/DVD-ROM IDE I/O is misconfigured or unoptimized?  That's a guess.  I played the newly ripped .ogg Pearl Jam song and it played but very very choppy over the iBook's speakers.  Again CPU utilization was about 10%.

I also noticed that it detected my Airport card in the iBook but once it fully booted up the Airport did not appear in the network devices list.  However I didn't try fiddling with the airport card since I do not have wi-fi access at that time.

All in all though I'm impress with such a good effort for a PPC build of Linux!  A hearty pat on the back to the devs out there making Ubuntu a reality! :D

---

### Post by pyx on 2004-10-20
Hi, 
your problems aren't ppc specific - the cd drive of apple computers aren't directly connected to the soundcard, so playing audio cd's is a bit tricky; try the xmms-cdread plugin, I heard this should work. DVD is another point: Because it is not free, you have to install some extra packages to get it work. At first i would recommend you to install totem-xine, and then these ones:
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3

Should work (better ;).) now.

---

### Post by Castaa on 2004-10-20
[quote=pyx]Hi, 
your problems aren't ppc specific - the cd drive of apple computers aren't directly connected to the soundcard, so playing audio cd's is a bit tricky; try the xmms-cdread plugin, I heard this should work. DVD is another point: Because it is not free, you have to install some extra packages to get it work. At first i would recommend you to install totem-xine, and then these ones:
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3

Should work (better ;).) now.[/quote]

Hey thanks, I'll check it out when I get home!

---

### Post by Castaa on 2004-10-21
Ok I the 4 packages listed above installed. :)

I also tried installing totem-xine but dpkg complained that totem-gstreamer conflicted and totem-xine would not install.

When I try to play a DVD (Bladerunner) I get the follow error from Totem:

[b]Totem cannot play this type of media (tmw_aspect_ratio_square_menu_item) because you do not have the appropriate plugins to handle it.
Please install the necessary plugins and restart Totem to be able to play this media.[/b]

---

### Post by pyx on 2004-10-21
It's perfectly fine that totem-xine and totem-gstreamer conflict, because the xine backend will replace the gstreamer one. If necessary, try to uninstall totem-gstreamer. You can also try to install vlc. Thats the player I use for DVD playback. Maybe does it bring some more plugins with it.. I'll just suggest trying it out..

---

### Post by gilgamesh on 2004-10-31
i've installeed ubuntu yesterday on my iBook 500MHz 60 Go internal.
The only problem i've encountered is the keyboard (you have to go in the keyboard perf panel (poste de travail> préférences bureau>clavier ie keyboard sorry it's in french ;-) ) and select Macintosh in the second tab. i still can't have the pipe, accolade and some other useful characters for web developper....

Airport is working fine whitout any configuration (you have to select the eth1 or ethO at the installation) and i've downloaded the updates through airport.
no problem

even on a 500 MHz ubuntu is amazingly fast and responsive.

Miss macOnLinux, bluefish and compatibilty with debian packages  (i'm an absolute nOOb ).

---

### Post by Huxley on 2004-11-04
Hi 

Installed in my G3 400 bronze with 128 mb ram.

Quiet - no more hd sounds like with os x - great.  Flash drive works.

DVD support - some dvd's will not mount and then I get the above (totem tmw_aspect_ratio_square_menu_item) error.

---

### Post by Huxley on 2004-11-04
Installed on a powerbook g3 400 bronze. 128 mb ram.
No problems.

I do have the same Totem dvd problem.
If the dvd does mount - I get the (tmw_aspect_ratio_square_menu_item) error.

---

### Post by Castaa on 2004-11-05
[QUOTE=Huxley]Installed on a powerbook g3 400 bronze. 128 mb ram.
No problems.

I do have the same Totem dvd problem.
If the dvd does mount - I get the (tmw_aspect_ratio_square_menu_item) error.[/QUOTE]
 Try installing xine-ui.  Go to the debian package site.  Use dpkg- i to install them.

---

### Post by chascon on 2005-01-09
pyx:  The below is simply not true for music CDs.   It's just plain wrong.  I installed xmms from main and it plays CDs fine.  apt-get install xmms will work fine.  And no you do not need xmms-cdread.  xmms comes with CD Audio Player 1.2.10 [libcdaudio.so].  To configure, cntrl "p" while mouse is over main window, select libcdaudio.so and "Configure" it to do digital audio extraction rather than analogue.  Choose OSS as output plugin (usually better than ALSA in the ppc world lately).  Voila, xmms now plays regular store bought music CDs!  To play music recorded as data, as I have recorded (no stupid mp3 for me thanks), no configuration is needed.

I think I've tried the xmms-cdread plugin on a mac with debian and I don't think it worked.  Debian or okle also had a script that enabled css install, not the install of extra libraries per say.  So I think the only library you're going to need is one pertaining to css, any others should install with a CD or DVD player, after all that is what they are made to do.

update: I just installed the css with the deiban script.  It works and is the only easy was to install css as the marilat, the repository recommended at [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats), does not have ppc packages (maybe someone should mention this to the mainter of the RestrictedFormats page?).  I tested both xine-ui and ogle.  xine-ui sound pops (the same alsa probem I've seen in xmms's use of the alsa plugin?) but ogle's is fine.  Both a a little choppy on sound and video on my slow compter.  The only problem I found with ogle is that the stop button doesn't respond.  So I just kiilled ogle to stop CD playing.  I don't know how good this is for the CD player.  Another bother is that none of these are showing up in gnome's subcontextual menus, and vlc in term doesn't start vlc; it's an illegal instruction.
Times like this I wish for debian's stability, although slow as it may be evolutionary.
Yes I agree that it should not be distro devs who should fix problems with apps (the app dev should).  For you guys complaing about slowness, there's a ogle-altivec for newer macs.  I haven't tried it.

Last thing, about the debian script, I didn't have to install fakeroot or anything.  I didn't even check for these things as the instructions to install css from the marilet site mention nothing about fakeroot or other deps before installing css.  Niether does sarge.  Just wait a while for it to take effect.  Restart apps.  I tried it with ogle-gui, xine-ui, and the default totem.  It worked well with the exception of totem.  That totem doesn't seem to play anything (even after the css script), and it never offers insight, not that we need it but it seems like a dumb app teamed up with gstreamer.



"Default Re: iBook G3 + Ubuntu
Hi,
your problems aren't ppc specific - the cd drive of apple computers aren't directly connected to the soundcard, so playing audio cd's is a bit tricky; try the xmms-cdread plugin, I heard this should work. DVD is another point: Because it is not free, you have to install some extra packages to get it work. At first i would recommend you to install totem-xine, and then these ones:
libdvdcss2
libdvdnav4
libdvdplay0
libdvdread3

Should work (better ;).) now."

---

