---
title: "Video problems with ATI 7500 on PowerMac 3.1"
date: 2020-02-29
forum: Apple Hardware Users
---

### Post by este.el.paz on 2020-02-29
> **gsahli said:**
> If you get to the boot prompt, can you try this command:
Linux quiet splash radeon.agpmode=-1 modprobe.blacklist=ams

I was having this same issue with my PowerMac3,1 . . . after upgrading the video card to a Radeon ATI 7500 my install of possibly U-MATE 16.04 would only boot to black, after going to splash and cursor . . . tried all kinds of boot params . . . .  Then I found this thread, tried these, again failed, but I had a DVD with U-MATE 17.04 Zesty PPC burned, so I booted to that, added the boot params . . . and, into a working GUI!!! 

So I went for the install, and selected the "upgrade 16.04 to 17.04" option . . . a number of crashes were happening, "webkit" crashed a few times during the slow install process . . . and it "finished" but adding that "a few packages could not be installed, so when you reboot you can add them manually" . . . .  So I shut down.

On cold boot I selected "L" from Yaboot, and yea!!! we get the splash, the cursor, the log in window, we log in, the desktop image loads . . . and the display goes to black??????  In the good olde days of PPC linux, if you used boot params to boot a live image, those were added to yaboot **automatically** . . . those days of yore are gone I guess.  I rebooted and this time again added the boot params listed above, and yes . . . a working desktop with all of my files from 16.04 . . . not too many, but there.

Rifling through the system freshly installed . . . hmm . . . no Firefox . . . hmm . . . opened the console, ran "sudo apt install firefox" . . . "no package found" . . . ???  While I was there I tried to run another apt update/dist-upgrade . . . a bunch of "404 errors" showed up . . . and something like, "so many broken links, it's not safe to run an upgrade like this . . . "  Tried to install synaptic via console, something basic . . . a number of packages showed up to be installed, I clicked "y" and that again errored out.

So, I can boot to the Zesty system, but whatever it was when I downloaded it . . . that's what it is . . . you could try to get Zesty Ubuntu-MATE and those boot params would possibly work, but PPC is "no longer supported" by ubuntu, "Software Boutique" loaded a blank white window . . . .  I guess I could try for a basic browser, but really the system isn't viable for web interfacing and/or keeping itself upgraded . . . .  Not sure who is offering the 32 bit PPC linux system these days??  Don't think any of them are "fresh" . . . or have a browser that can navi the present web pages????  PPC is dead, long live PPC machines . . . .

e.e.p

---

### Post by imixmuan on 2020-03-05
Linux on PPC is, to qoute Jim Kerr, "Alive and Kicking..."

For starters we have: working for the most part: Void Linux PPC and Adele Linux PPC. We have Fienix PPC, working for 64 bit PPC. We have MintPPC (complete with original developer) back although the upstream Debian ports constantly break it, we have Debian Sid port working until it breaks on you as well. Finally, and probably for most users here the best options, we have Wicknix's rebuilds/respins of ye olde hoary 16.04 and 12.04 Lubuntu's. They run off USB sticks. Yes, I said it. Live USB's, with persistence. These are not your grandpa's Lubuntus, they have updates to apps, security and updated browsers. Oh, speaking of browsers we have not one, not two but THREE mo-dern Linux ppc 32 bit browsers.

1.Arctic Fox (Built from Palemoon, a Firefox fork but with the Goanna web engine)
2.Spider Web (Built from UXP, but with Seamonkey's interface) Also, Spider Mail if you still do email, which is like, so 1999...
3.Interweb (Built from Basilisk, a Firefox fork)

Don't ask me for support, cause it ain't 1999 and homey don't play that. Post yr questions in the Macrumors forum, Wicknix is very helpful. There is also a  PPC Linux Wiki. Read it. Backwards and forwards, then sideways. Also there is a Wiki for OpenBSD on PPC, if you are a glutton for serious punishment. There is only one decent browser for OpenBSD, that's Otter Browser. You will have to build it yourself, otherwise you are stuck with using Netsurf and Links. Read the wiki like your life depended on it. Some PPC macrumors users totally love OpenBSD 6.6. Fast secure, and with WindowMaker, you can party like its 1988 and Steve is still alive and kicking...
In fact, its a great time to be alive and into PPC and Linux. Head on over to the PowerPC user forum on macrumors, cause....that's where all the action is, people. Not here.

---

### Post by este.el.paz on 2020-03-06
> **imixmuan said:**
> Linux on PPC is, to qoute Jim Kerr, "Alive and Kicking..."

For starters we have: working for the most part: Void Linux PPC and Adele Linux PPC. We have Fienix PPC, working for 64 bit PPC. We have MintPPC (complete with original developer) back although the upstream Debian ports constantly break it, we have Debian Sid port working until it breaks on you as well. Finally, and probably for most users here the best options, we have Wicknix's rebuilds/respins of ye olde hoary 16.04 and 12.04 Lubuntu's. They run off USB sticks. Yes, I said it. Live USB's, with persistence. These are not your grandpa's Lubuntus, they have updates to apps, security and updated browsers. Oh, speaking of browsers we have not one, not two but THREE mo-dern Linux ppc 32 bit browsers.

1.Arctic Fox (Built from Palemoon, a Firefox fork but with the Goanna web engine)
2.Spider Web (Built from UXP, but with Seamonkey's interface) Also, Spider Mail if you still do email, which is like, so 1999...
3.Interweb (Built from Basilisk, a Firefox fork)

Don't ask me for support, cause it ain't 1999 and homey don't play that. Post yr questions in the Macrumors forum, Wicknix is very helpful. There is also a  PPC Linux Wiki. Read it. Backwards and forwards, then sideways. Also there is a Wiki for OpenBSD on PPC, if you are a glutton for serious punishment. There is only one decent browser for OpenBSD, that's Otter Browser. You will have to build it yourself, otherwise you are stuck with using Netsurf and Links. Read the wiki like your life depended on it. Some PPC macrumors users totally love OpenBSD 6.6. Fast secure, and with WindowMaker, you can party like its 1988 and Steve is still alive and kicking...
In fact, its a great time to be alive and into PPC and Linux. Head on over to the PowerPC user forum on macrumors, cause....that's where all the action is, people. Not here.

@imixmuan:

Wasn't actually asking for help, as in this sub-forum it's hard to find let alone expect it . . . but, glad to hear there might be some options for PPC 32-bit users . . . .  I wasn't using my old G4 units too much because the iBook has less than 1GB of RAM, and that makes accessing today's web requirements difficult . . . and I think the HD is dying.  My PM 3,1 was intermittently dying after 40 mins of run time, whether I was running it in OSX or 16.04, so I changed the video card in it to see if the card was "fading to black" . . . and that seems to have maybe revived the OSX side, but numerous updates/upgrades to 16.04 failed to recognize the hardware change of ATI Radeon card to another ATI Radeon card.  Just didn't have time to mess with a dying machine until recently I made some time to try to find "an answer" and found my way to that other "black display" thread . . . which I attempted to revive and hijack for my own selfish pleasures . . . .  : - )))  The mods caught me at my crimes . . . .

Anyway, I used to be very familiar with the various "PPC wikis" and spent a lot of time on various forums trying to get something working . . . first starting with fink some 12-14 years ago, then going to MintPPC which broke all of the time back then, to then the various ubuntu flavors . . . to now the last of the PPC iterations, but the backports are erroring out and it's not too tidy, so once an install is done there aren't new packages available . . . and even with the 2 GB RAM in the 3,1 . . . stuff happens slowly on the interweb . . . .  I might get around to the macrumors site you mentioned or look into Wicknix for persistent live action . . . .  But . . . do have other stuff to do with my time . . . I only would have to add the recent boot params to the /etc/yaboot.config file and I could boot into an unsupported version of Zesty . . . maybe on the next rainy day we have in SoCal.

---

