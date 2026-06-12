---
title: "LTSP video help request"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by lcbruzer on 2007-07-26
Hello - may need redirection on this question but wasn't certain on which forum.
I changed from Fedora to Ubuntu because of (in addition to other things) the better LTSP support.
Using 7.04 as LTSP server. (Linux homeserver 2.6.20-16-generic #2 SMP Thu Jun 7 19:00:28 UTC 2007 x86_64 GNU/Linux)

Have running ltsp i386 clients built with ltsp-build-client.
Thin clients have poor onboard video but otherwise work (although have not tested sound).
I bought a GeForce nvidia fx 5200 video PCI card for them.
Server also runs this video card.

When attached to the GeForce card, the client boots with the logo, etc. but screen goes black probably on starting X and then you cannot login.

The /opt/ltsp/i386/etc/X11/xorg.conf file in the clients is different than on the server in that it has:
In the Device section, client xorg.conf has "nv" vice the server's "nvidia" driver.
In the Module section, client has more listed than the server.
I tried putting the server's xorg.conf details I thought relevant into the client; same behavior.
Since I see the Ubuntu splash and the first progression of the orange line I feel the card is almost working but maybe the "nv" driver isn't what I need; maybe I need to build the client with more modules... Any ideas?

---

### Post by thenone on 2008-01-04
Have you found the solution yet?

I intend to setup LTSP server for gaming purpose and I am proposing to use FX 5200, but still dont have the time for the experiment due to my tons of work to do.

---

### Post by Dragonbite on 2008-01-14
I had the issue where my clients see the Edubuntu logo and the status bar, but them I'm stuck in a CLI login prompt which doesn't work.  It worked with my one and only 4MB nVidia video card, but not anything else (onboard or PCI).  When I was successful with the following change now ALL of my systems are working.

Please pardon me because I don't recall the exact location of the file(s). I will try and find the details when I get home.

Baiscally there is a configuration file called lts.conf located at (I think)  /var/lib/tftpboot/i386/lts.conf although I know I found an lts.conf file in one location that told me it is no longer used there and it gave me location to make my own lts.conf file to modify.

Supposedly there is an example file but I haven't found it yet.

In this lts.conf I added the following lines:
```
[default]
X_DEFAULT_DEPTH=24
X_DEFAULT_RESOULTION="800x600" "1024x768"
```Make sure you put in [default] ... I have been beating my head against the wall for weeks and found this was the cause (the other 2 lines didn't get run).

Oh, and for the resolution, X starts with the first one and then goes to the next so if you have a resolution you know works and you prefer you can probably safely put that one first.

I found the location from this [[COLOR="Blue"]Topic Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=610377&highlight=lts.conf")

---

