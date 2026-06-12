---
title: "General Q's about getting my Linux feet wet"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Uber-n00b on 2008-04-04
No Linux experience to speak of but I liked the kubutnu 7.10 amd64 LiveCD enough to ask a buddy tossing a bunch of old IDE drives to save one for me so's I can dual boot without changing much. But before I get started with an actual Linux installation, I'm looking for a few pointers/pitfalls (links greatly appreciated) 

[List=1][*]How sig is it that I'm running on a 64bit CPU? (AMD 3300+) Does it really only apply to the distribution CD i need to use or does that extend to the prog repositories or anything else as well?[*]When I booted from the LiveCD, I got no sound and my monitor rez could go no higher than 1024x780 (rt now I'm using WinXPx86SP2, Creative Extigy ext card, and an ATI x1650 vid card.) Is that just because I was booting from disk or is finding/installing proper drivers really going to be as difficult as some people have made it out to be? BTW, even after I rebooted I still didn't get sound back... had to reinstall the creative drivers. I thought that was strange considering i must've seen 'this will not change your system' about 10 times.[*]I am also concerned about access to my local network here. There's 4 PCs in my apartment network that I totally depend on having access to shared files on. I couldn't figure out how to connect to the network when booting Linux (or I didn't spend enough time trying.) Can somebody shoot me a link? Figuring that out is a priority before dive in.[/list]So thanks in advance to anybody helping out a n00b like me.

---

### Post by hyper_ch on 2008-04-04
(1) Not sure what you mean there... if you want to use 64 bit to its full power you have to download the 64bit ISO versions of *buntu - however there are still a few things that need a workaround like Flash - but there are excellent guides on how to do that here in the forums.

(2) ATi is generally more hassle than nVidia or Intel... can't really comment on that... also my soundcard works out of the box.... when you run from the DesktopCD and apply changes, they won't be saved. The next time you reboot all changes are gone - that's what a DesktopCD is intended for (to not touch the system)... hence even installing drivers and rebooting won't help there...

(3) Wifi or LAN network?

---

### Post by kaivalagi on 2008-04-04
You might however want to install a Hardy 8.04 release when it is stable, towards the end of the month. 7.10 is about to be history. Some of the restricted drivers in 8.04 are newer than those found in 7.10. The below is relevant whatever you choose to do. If I were you I'd just dive in and search for help on the forums as you need it, you'll find all the answers on here somewhere :)

> How sig is it that I'm running on a 64bit CPU? (AMD 3300+) Does it really only apply to the distribution CD i need to use or does that extend to the prog repositories or anything else as well?
Just go ahead and install a amd64 version of ubuntu/kubuntu, you'll be fine. 64 bit support in linux is good and you shouldn't have any real problems...worst case you can still run a 32bit application in a 64 bit linux OS, you just need the appropriate 32 bit libraries, most of which will be installed for you by synaptic (package manager) if they are needed.

> When I booted from the LiveCD, I got no sound and my monitor rez could go no higher than 1024x780 (rt now I'm using WinXPx86SP2, Creative Extigy ext card, and an ATI x1650 vid card.) Is that just because I was booting from disk or is finding/installing proper drivers really going to be as difficult as some people have made it out to be? BTW, even after I rebooted I still didn't get sound back... had to reinstall the creative drivers. I thought that was strange considering i must've seen 'this will not change your system' about 10 times.

The LiveCD will not retain any changes you make after a reboot, for that you need to be installed on a hard drive and then install the relevant drivers. Install to disk and get the your install updated, after a short time the updater will prompt from the taskbar (if you have an internet connection), then install your needed drivers. 

> 
I am also concerned about access to my local network here. There's 4 PCs in my apartment network that I totally depend on having access to shared files on. I couldn't figure out how to connect to the network when booting Linux (or I didn't spend enough time trying.) Can somebody shoot me a link? Figuring that out is a priority before dive in.

The samba client will allow you to access windows networked PC's. Search for "smbclient howto" and you'll find all the help you'll need. It is straight forward.

I hope that helps.

Edit: beat me to the post ;)

---

