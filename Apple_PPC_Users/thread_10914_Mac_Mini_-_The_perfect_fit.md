---
title: "Mac Mini - The perfect fit?"
date: 2005-01-12
forum: Apple PPC Users
---

### Post by killerfish on 2005-01-12
Hello gang,

I've been looking to get another machine for awhile that I can use as a 'playground/development' machine.  My normal box dual boots Windows and Ubuntu.  Problem is, it drives my wife nuts because she refuses to try Linux and everytime she goes to use the computer, it's in Ubuntu :).  Net, she has to reboot.

With the Mac Mini, however, I could dual boot it between OS X and Ubuntu and leave the other machine as Windows only.  Then, i could hook them up with a KVM switch.  Net, everyone's happy!  

Looking at the specs, is there any reason to think I'd have trouble with ubuntu on it?

KF

---

### Post by jdodson on 2005-01-12
[QUOTE=killerfish]Hello gang,

I've been looking to get another machine for awhile that I can use as a 'playground/development' machine.  My normal box dual boots Windows and Ubuntu.  Problem is, it drives my wife nuts because she refuses to try Linux and everytime she goes to use the computer, it's in Ubuntu :).  Net, she has to reboot.

With the Mac Mini, however, I could dual boot it between OS X and Ubuntu and leave the other machine as Windows only.  Then, i could hook them up with a KVM switch.  Net, everyone's happy!  

Looking at the specs, is there any reason to think I'd have trouble with ubuntu on it?

KF[/QUOTE]

from what i have read it seems you should have no problems.  it seems to be a minimalist machine running an ati dedicated video card.  if the dvd rom adheres to atapi/dvd "standards" then it should be fine.

let us know what happens:)

---

### Post by killerfish on 2005-01-12
Will do.  Taxes just may get done early this year!  As this is where the $'s are coming from! :)

---

### Post by jdodson on 2005-01-12
[QUOTE=killerfish]Will do.  Taxes just may get done early this year!  As this is where the $'s are coming from! :)[/QUOTE]

thats right, those are due soon.......  :shock:

---

### Post by tiiim on 2005-01-12
[QUOTE=jdodson]thats right, those are due soon.......  :shock:[/QUOTE]
 well i run Ubuntu on a ppc platform and get no problems with that. So you have no trouble at all. Ubuntu is easisy the best ppc distro out there.

---

### Post by slux on 2005-01-12
Sounds like a great idea! :)

Do remember that there are some drawbacks to running GNU/Linux on PPC as opposed to x86 (caused by non-free software packages) though.

You won't get playback for all the video codecs with mplayer that you can get on x86, no flash (except for a basic free software plugin) and 3d-acceleration is only available in the DRI form. Most non-free software packages being sold for Linux are not available either.

If those are ok for you, go right ahead. Apple hardware is fantastic and OS X is fairly good too even I happen to prefer Linux. :)

---

### Post by killerfish on 2005-01-12
[QUOTE=slux]Sounds like a great idea! :)

Do remember that there are some drawbacks to running GNU/Linux on PPC as opposed to x86 (caused by non-free software packages) though.

You won't get playback for all the video codecs with mplayer that you can get on x86, no flash (except for a basic free software plugin) and 3d-acceleration is only available in the DRI form. Most non-free software packages being sold for Linux are not available either.

If those are ok for you, go right ahead. Apple hardware is fantastic and OS X is fairly good too even I happen to prefer Linux. :)[/QUOTE]


Very informative...Didin't realize this, but none are show stoppers for now... Thanks!

---

### Post by daniels on 2005-01-12
[QUOTE=slux]3d-acceleration is only available in the DRI form.[/QUOTE]Er, there's nothing wrong with DRI.

---

### Post by chele on 2005-01-12
[QUOTE=slux]Sounds like a great idea! :)

Do remember that there are some drawbacks to running GNU/Linux on PPC as opposed to x86 (caused by non-free software packages) though.

You won't get playback for all the video codecs with mplayer that you can get on x86, no flash (except for a basic free software plugin) and 3d-acceleration is only available in the DRI form. Most non-free software packages being sold for Linux are not available either.

If those are ok for you, go right ahead. Apple hardware is fantastic and OS X is fairly good too even I happen to prefer Linux. :)[/QUOTE]
 * DRI works out of the box for me also, on this PB/G4/550.

* I am looking into Flash support, there is a gstreamer plugin, no?

* movie formats & streaming video, likewise, I have not had a chance to look at yet

* As far as non-free codecs & apps go, who needs them. If I wanted to limit myself to that, I wouldn't be here.

---

### Post by killerfish on 2005-01-13
[QUOTE=chele]* DRI works out of the box for me also, on this PB/G4/550.

* I am looking into Flash support, there is a gstreamer plugin, no?

* movie formats & streaming video, likewise, I have not had a chance to look at yet

* As far as non-free codecs & apps go, who needs them. If I wanted to limit myself to that, I wouldn't be here.[/QUOTE]
 Any reco's for a good DVI KVM?  I can only find some that support up to 1600 x 1200 resolution.  Problem is, I have an Apple 20 Inch LCD also in my sites with a res of 1680x1050.  Net, I'm pretty sure these KVM's won't work properly.  Unfortunately, I'm am relagated to needing both a PC & MAC.

Thanks!
KF

---

### Post by muteaid on 2005-01-14
You can't use the built-in wifi (airport extreme) in linux, but you can buy a cheap usb wireless dongle for when you are in Ubuntu.  Also, check out Fink and DarwinPorts, it might give you your linux fix, and you won't have to dual boot.

---

### Post by slux on 2005-01-14
[QUOTE=daniels]Er, there's nothing wrong with DRI.[/QUOTE]

DRI is great and there's nothing wrong with it *per se*, but you won't play Doom 3 with it and certainly it is slower than the proprietary drivers for pretty much any given card. You might be able to run UT2003 with it but before that you need to get the s3tc code which can't be included in Ubuntu and other distributions because of software patent issues. 

Not that any of this currently matters much on PPC as neither of the games I mentioned has a port. DRI probably won't have problems with most of the 3d-accelerated stuff available currently, but if there were better drivers we might see more ports.

I like DRI a lot and appreciate the effort. I just wish the card manufacturers would get more involved instead of doing their own binary-only and x86-only drivers.

---

### Post by Huxley on 2005-01-16
Would dri work? With the ati 9200?

---

### Post by daniels on 2005-01-16
Yeah, it does.

---

