---
title: "Please im going nuts!!"
date: 2008-10-17
forum: Apple Hardware Users
---

### Post by proud_rock on 2008-10-17
I've been ripping my hair out all day over this, i will worship anyone who helps. 

I am trying to install Ubuntu 8.04 hardy from a live cd (the alternative one thats for mac) onto a mac powerbook 400mghz, 64mb ram, 10gb hd. i load the cd by holding down "c". if i boot with default i get the "frozen white screen". so if I boot with live video=ofonly eventually i get this message "running local boot scripts". it just sits there. alt + f2 brings up command, but alt + f7 is blank. 
so, i press alt +f2 and type startx, i get:

..."module loader present
markers: (--) probed, (**) from config file, (==) default setting
(++) from command line, (!!) notice, (II Informational (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==)log file: "/var/log/xorg.0.log"
(==)using config file "/etc/X11/xorg.conf"
(WW)****INVALID IO ALLOCATION****b: 0xf0000400 e: 0xf00004ff correcting
(EE)end of block range 0xefffffff <begin 0xf0000400
(EE)unable to find valid framebuffer device
(EE)R128(0): Failed to open framebuffer device, consult warning and/or errors above for possible reasons(you may have to look at the server log to see warnings)
(EE)screen(s) found, but none have a useable configuration.

fatal server error:
no screens found

waiting for X server to begin connections giving up.
xinit: connection reset by peer (errno 104): unable to connect X server
xinit: No such process (erno3):server error

any help?

---

### Post by mkvnmtr on 2008-10-17
I don't believe you have enough ram to run much less install Ubuntu. I think you better look for a another distro. Someone will probably recomend one for use with your unit.

---

### Post by proud_rock on 2008-10-17
Oh, I never thought of that, I thought it could run on old systems.Thanks, I feel... strangely relieved. Well, can anyone recommend? I'' start trying maybe xubuntu

---

### Post by MikeTheC on 2008-10-18
Well, consider this data point.

I have a PowerMac G3 "desktop" unit, 584 MB RAM, 6MB VRAM (I upgraded it), OC'd from 266MHz to 300MHz, and it's running Debian Etch and Gnome just fine.

The caveat is "for a machine of it's age". But it does work, so you might possibly want to go that route.

The thing about putting any distro of Linux on Apple hardware (particularly G3/G4 hardware) is that there's a lot of stuff that's either undocumented by Apple, or it's just older-than-the-hills and was abandoned by Apple, and trying to support all of that can be a problem.

I'd simply suggest maxing out your RAM on that system, and ensuring how much video RAM (VRAM) you have, because there may well be some minimums.

Good luck though!

---

### Post by ppc_guy on 2008-10-19
Not enough ram bud, though you are on the right track with the alt cd. I have a G3/333 w/ 192mbs of ram here that so far I've been able to boot Finnix and Arch in live enviroments. Both being completely CLI. I'm trullying to see if I can get Arch to install, being it's source based, my learning curve is pretty steep. But I'm getting there. For continuties sake I would love to get Ubuntu on the machine eventually. And like I've posted before. From my own research these machines seem to be happier with CD-RW's and are really picky with CD-R's.


As always, your mileage may vary,
ppc_guy
-----------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel.
-----------------------------------------------------------------------

---

### Post by ssam on 2008-10-19
64mb of ram would probably be fine for a command line only (server install). but i am guessing thats not what you want.

---

