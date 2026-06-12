---
title: "can´t install ubuntu on mac G4"
date: 2012-03-21
forum: Apple Hardware Users
---

### Post by andersond on 2012-03-21
Hello!

I had all my home pc´s stolen. The only survival was an old gray desktop Mac g4 [(this one)]("http://everymac.com/systems/apple/powermac_g4/stats/powermac_g4_733.html"). 

The Mac OS installed was 10.3 (old), but i could not update it to newer ones due to hardware limitations (apple sux), and as a consequence, the experience on it became boring. So I decided to install linux on it, in order to take advantage on up-to-date software and drivers.

I had an old 5.04 breezy for mac installer cd (actually, lot of them, from the times when canonical used to send them via conventional mail). I installed it, and could update to dapper, using some tutorials on ubuntu EOL sections. Unfortunatelly, when did the next steps to update the distro again, got problems to boot the machine - and it was adviced on EOL section of ubuntu - "apple users may experience problems when updating to 7.x"

Well, I also downloaded and burned the latest versions for powerpc, 12.04 (from today, mar21-2012, 10.04, 10.10,11.04, 11.10, 8.04) some of them live, some just the minimal cd, some of them I tried both. Each one had a different problem during installation. 

Well, talking about the 12.04 - the latest- the problem has some to do with framebuffers on my video card- ati rage128 - and it boots to prompt. I have read some things about this issue on net and some workarounds through editing xorg.conf and other system files, but once there´s nothing really installed, it´s running from cd, how could I fix it definetly? ok, i could try to use the terminal text editors (by the way, how do I exit vi?? I always get stuck on it!is there any more user-friendly editor?), to fix that system files to run well the video card but - after this, how could I re-start the live on graphics mode, proceed the installation to hd, and, more important, grant that these fixes were also installed?

Well, I also tried to remove the agp original rage128 card from the mac, and installed a very old 1mb pci card, but I got no video, is it necessary to set up some thing on mac telling to it use the pci video? or the pc video card is not compatible?

Well, resuming hte history, what do you guys suggest for my case? All I want is to get the latest (or the newer possible) version of any linux running on this g4, just until I can afford a new PC.. I also looked for other distros, but all of them stopped upgrading by 2008-2009, like yellow dog for example..

thanks in advance and sorry for the long text..

---

### Post by 2F4U on 2012-03-21
There is quite an extensive faq Ubuntu on PowerPC:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

A special section is dedicated to graphics problems. What I get from your problem I would first try the easy workarounds, for example adding nomodeset to the grub kernel parameters. If that allows you to start the liveCD, don't forget that you have to carry over these parameters to your install.

---

### Post by Perfect Storm on 2012-03-21
Moved to 'Apple Users' forum.

---

### Post by rsavage on 2012-03-21
Nano is a good easy text editor.

To start an x session after editing an xorg.conf use the command:

sudo start lightdm

---

