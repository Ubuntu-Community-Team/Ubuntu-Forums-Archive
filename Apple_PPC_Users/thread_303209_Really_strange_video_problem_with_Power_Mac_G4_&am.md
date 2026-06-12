---
title: "Really strange video problem with Power Mac G4 &amp; ATI Radeon 9000"
date: 2006-11-19
forum: Apple PPC Users
---

### Post by blitterfly on 2006-11-19
Hi all,

I've recently installed Ubuntu 6.10 on a Power Mac G4 (Sawtooth) that has an ATI Radeon 9000 hooked up to a ViewSonic VX724 via DVI.

The problem I'm having is that when the machine first starts up and goes into X, the display is all weird... the image is slightly off-center and all of the areas of the screen that should be black are filled with red criss-cross pattern things.

The really odd part is that when I go into System -> Preferences -> Screen Resolution and then change the resolution from 1280x1024 (the native resolution for the display and the default I've got setup in xorg.conf) to 1024x768, the problem goes away and everything looks fine. I can then switch **back** to 1280x1024, and it is still fine until I next boot the machine.

I've been scouring the internet for a couple weeks now trying to figure out how to fix this, and I've not even come across anything remotely like it.](*,)  I'm hoping maybe someone out there has some insight into the problem. I have my workaround, of course, but it would be really nice if I could get it to work straight off without having to do that.

Thanks!

---

### Post by EuroCity on 2006-11-20
Same problem also with my Power Mac G4 (also here with a Radeon 9000, and a LaCie photon18blue at 1280x1024, connected through DVI): a strange screen distortion, with false colours and moving patterns (if one can call them so).

This has happened with all recent (since a year, or so) Linux distros I've tried on that computer: Fedora, Mandriva, SUSE and Ubuntu.

So, it must be some form of Xorg driver problem with the Radeon 9000: maybe a PPC-specific problem, also; and maybe something to do with the DVI connection? Difficult to say...

The fastest workaround could be to run a game that changes the screen resolution at startup, such as Planet Penguin Racer: then, as soon as the game has started and the resolution has changed, repeatedly press the Esc key to exit PPRacer, and you return to a good 1280x1024 screen (without artifacts) - much faster than opening the Screen Resolution control panel.

Really strange problem, anyway...

---

### Post by blitterfly on 2006-11-20
> **EuroCity said:**
> The fastest workaround could be to run a game that changes the screen resolution at startup, such as Planet Penguin Racer: then, as soon as the game has started and the resolution has changed, repeatedly press the Esc key to exit PPRacer, and you return to a good 1280x1024 screen (without artifacts) - much faster than opening the Screen Resolution control panel.

Really strange problem, anyway...

Actually it's pretty fast to just open Screen Resolution, select 1024x768, click OK, then hit "Use previous resolution" to fix it. Takes about 5 seconds, but it's damned annoying.

---

### Post by EuroCity on 2006-11-21
Of course, it's a matter of personal preferences...

One could maybe also write a startup script to change the resolution to 1024x768 and then change it back to 1280x1024: thus, it would all happen automatically!

Anyway, are any other people here experiencing this strange screen problem?

---

