---
title: "[SOLVED] No wireless OR wired?  What the heck?"
date: 2008-07-22
forum: Apple Hardware Users
---

### Post by travnewmatic on 2008-07-22
Hey guys,

I just did a clean install of ubuntu-8.04.1-desktop-powerpc.iso on a Powerbook G4 15".

Leopard was running kind of sluggish, like a wet sponge, so I thought I'd speed things up a bit with Ubuntu.  Everything got installed, except for the airport extreme firmware.  I thought to myself, no biggie, I got it working before (when I had an earlier version of Ubuntu installed), i'll get it working this time.

I went through the [tutorial]("http://joona.kuori.org/ubuntu-powerbook/#airportextreme") that I used in the past as well as [the one]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware") that was suggested to me in the terminal.  I tried using the fwcutter that they told me to get in the second tutorial, but the tar.bz2 wouldn't extract properly.  The first one worked without a hickup except that I still don't get wireless.

Oh, and I also have no ethernet port.

Tell me what screen caps you want and I'll get them to ya.  It's really stupid, Ubuntu sees that it needs to get the firmware, tries to, but then can't because the ethernet port isn't configured.

I have a feeling that if I could get the ethernet to work, then Ubuntu could get the broadcom driver (hopefully).

Thanks a bunch guys!
I really appreciate it!
-Travis
travnewmatic_at_gmail_dot_com

---

### Post by kosumi68 on 2008-07-22
Hi travenewmatic,

sounds like you are running on a Macbook Air. Try this link:

[https://help.ubuntu.com/community/Macbook_Air](https://help.ubuntu.com/community/Macbook_Air)

EDIT: except you said it was a G4 - anyways, the trick to load the drivers to the macOS partition should work for you, too.

---

### Post by stream303 on 2008-07-22
As far as the ethernet port goes, did you ever see an option to use ethernet-over-firewire when installing?  If so, you don't want that. :)

I've been tripped up by this when flying through an install..

---

### Post by travnewmatic on 2008-07-22
....the cable was bad!  I went downstairs to my buddies place and hard-wired into his base station with his cable and viola, it downloaded fwcutter and got the drivers that it needed.  I'm posting this reply using my newly configured powerbook!

Thanks!
-Travis

---

