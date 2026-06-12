---
title: "VLC errors and DVD questions"
date: 2004-11-29
forum: Apple PPC Users
---

### Post by adamward on 2004-11-29
I installed VLC via apt-get, as well as vlc-gnome.  When trying to run it does not load.  I tried the command line and got the following error:

root@ibook:/home/award # vlc
VLC media player 0.7.2 Bond
Illegal instruction


Any ideas on how to fix this?

Also, how does one play DVDs?  I followed the multi-media howto, but I get an error with apt-get when trying to connect to:
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

any ideas on how to get DVDs to play?

I'm a linux newbie, so any help would be appreciated!

--adam

---

### Post by eggie on 2004-11-29
synaptic  search for xine  after checking that universe repositiories are enabled under repositiories.
mark xine for installation and click.

---

### Post by adamward on 2004-11-29
I have xine installed.  Still no DVD playing.  Any other thoughts?

The error I receive in Xine is:
Error reading NAV packet.

When launched from terminal, I get the following message:
root@ibook:/home/award # xine
This is xine (X11 gui) - a free video player v0.99.1.
(c) 2000-2003 The xine Team.
libdvdnav: Using dvdnav version 1-rc5 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Encrypted DVD support unavailable.
libdvdnav: DVD Title: SHREK
libdvdnav: DVD Serial Number: 2b1c7427
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/root/.dvdnav/SHREK.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1


Anything else I can try?

--adam

---

### Post by pistooli on 2004-11-30
**libdvdread: Encrypted DVD support unavailable.**

obviously this is the problem... a package called libdvdcss is needed imho...

cheers - pistooli

---

### Post by adamward on 2004-11-30
[QUOTE=pistooli]**libdvdread: Encrypted DVD support unavailable.**

obviously this is the problem... a package called libdvdcss is needed imho...

cheers - pistooli[/QUOTE]
 The thing is, I have libdvdcss installed.  I can not get DVDs to play at all for me under the gnome environment.  For the heck of it, I did an apt-get install kdebase, re-logged in to a KDE session, and DVDs play in both xine and vlc...

Now that they play, is there anyway to "speed up" the playing.  I have a iBook G3 600 mhz and the dvd playback is very choppy.  I'm guessing it's caused by Ubuntu using software decoding instead of hardware decoding on my iBook, but is there anything I can do/try to get a little more speed out of the unit?

Thanks!

--adam

---

### Post by eggie on 2004-11-30
sudo hdparm -d 1 /dev/hdwhateveryourcdromis

will turn on dma if not on. Will help if playback is choppy I think.

---

### Post by adamward on 2004-11-30
[QUOTE=eggie]sudo hdparm -d 1 /dev/hdwhateveryourcdromis

will turn on dma if not on. Will help if playback is choppy I think.[/QUOTE]
 How do you find out what your CDrom drive is?

Sorry to keep asking questions!

****EDIT****
Never mind, I figured it out!  I really need to learn more of this linux stuff *LOL*

--adam

---

### Post by adamward on 2004-12-03
[QUOTE=eggie]sudo hdparm -d 1 /dev/hdwhateveryourcdromis

will turn on dma if not on. Will help if playback is choppy I think.[/QUOTE]
 Is there any way to make this a default on machine boot so I don't have to type it in each time?

--adam

---

### Post by M-Rick on 2004-12-03
VLC doesn't work great for me too ... :-( Under OS X I have no problems but there ...
But I use vlc, not vlc-gnome, because the interface is much better, not so ugly :-(

Does Xine can read m4a (MPEG 4 audio) ?

---

### Post by Viro on 2004-12-05
[QUOTE=adamward]Is there any way to make this a default on machine boot so I don't have to type it in each time?

--adam[/QUOTE]
 You need to edit the /etc/udev/cdsymlinks.sh and add dvd to the line that says "echo cdrom"

---

### Post by Caesar on 2005-03-08
[QUOTE=Viro]You need to edit the /etc/udev/cdsymlinks.sh and add dvd to the line that says "echo cdrom"[/QUOTE]

I doesn't have that script.
I've only the file "/etc/udev/cdsymlinks.conf" and i can't find that line.

Any help?


TIA

---

### Post by Viro on 2005-03-09
[QUOTE=Caesar]I doesn't have that script.
I've only the file "/etc/udev/cdsymlinks.conf" and i can't find that line.

Any help?


TIA[/QUOTE]
 I don't have Ubuntu anymore, just plain old debian, so you'll need to post the entire contents of /etc/udev/cdsymlinks.conf. Will be able to tell you more then.

---

