---
title: "ubuntu 8.10: powerbook G4 DVI install diary"
date: 2008-10-31
forum: Apple Hardware Users
---

### Post by gft on 2008-10-31
This is the computer that this post focuses on:
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_800_dvi.html]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_800_dvi.html"). This post is intended to both find problems with the installation of ubuntu on this type of powerbook and when possible point out fixes.

Successfully downloaded (via torrent) ubuntu-8.10-alternate-powerpc.iso. Burned to a CDRW. Used the ctrl-alt-f2 modprobe ide-scsi trick and it recognized the CD.

Video is corrupt in the text installer. Parts of the image flicker both to the right and left of the center, perhaps an inch or an inch or two. If I remember right, previous linux installations have misdetected the radeon 7500 in this powerbook as a radeon 9000, though that might have just been X. Most of the setup is readable with some effort but the automatic keyboard layout detection is a big pain.

It's stuck on "Please wait..."

Restarting the installation without any network configured, perhaps the ubuntu servers being busy was causing the "Please wait..." to be stuck. I decide to try "install video=ofonly" which fixes the flickering video problem.

Maybe I was wrong about the network causing it to get "stuck". It's been at 6% saying "Please wait..." for at least 5 minutes while the DVD-ROM's been seeking like mad. I'll keep waiting a while before I decide it's bad media. Never mind, it's continuing.

The first time I log in I get an error about bonobo not being able to talk to a factory or something, and a bunch of dialogue boxes pop up telling me that some widgets or other can't start and do I want to delete them from my startup? I click no for all of them, enable networking, logout, log back in and everything works fine. Subsequent logins without networking work fine too.

The fadeout while logging out causes serious graphical anomalies. Parts of the screen move around and become distorted. Again, I suspect Xorg is thinking that the video card is a radeon 9000, as happened in ubuntu 8.04.

Sound is not working, likely because snd_powermac isn't being loaded. I'm guessing if I enable it sound will work but be choppy, as is the case with all ubuntu releases on this computer since 6.06.

After adding snd_powermac to /etc/modules, sound works but of course it's choppy. Basically useless for anything but system beeps.

---

### Post by gft on 2008-10-31
reserved

---

