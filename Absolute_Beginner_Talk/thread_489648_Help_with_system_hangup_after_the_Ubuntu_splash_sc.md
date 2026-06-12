---
title: "Help with system hangup after the Ubuntu splash screen"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by myacademy on 2007-07-01
Just wanted to let everyone know how much of a help this forum has been to me in the last few days! I HAD Feisty up and running with just about every Windows game I needed (Doom3, Guild Wars, all the Steam games, etc.), mp3 support, DVD playback, and even Beryl under XGL, all thanks to the community.

Another note: I'm no slouch. I've tried everything that has been posted in order to remedy my problem to no avail. I've Googled, searched, and even snooped around in real physical books to try to figure out whats going on - no dice.

Anyway, onto the problem (prefaced by system specs):
ASUS K8N4-E Deluxe Socket 754 Mobo
AMD Athlon 64 3700+ (Clawhammer) CPU
ATI Radeon X1950 Pro (PCIe) Video card
1GB Corsair Value Select Memory
19" Acer AL1912 LCD Monitor
1 Maxtor 80GB ATA HD
1 Western Digital 200GB ATA HD (removed)

Now as I said, I had a fully operational Feisty system a few days ago. The problems started once I got around to actually mounting my 200GB WD HD. It has historically failed me more than it has worked, but I figured since 80GB wasn't much space for media, that I would install it and just hope for the best. Anyway, everything went fine, got it mounted and accessible to users other than root, and started loading it up with media from my external HD. Anyway, I used amarok to do some MP3 listening, and upon restart, what a surprise! Bad sectors on my 200GB HD!
Not a big deal I thought, so I let whatever Linux was doing run its course, at which point I was told that the error on my HD was preventing my system from booting (in so few words). I proceeded to curse at the drive, remove it, and reset my 80GB to master. I removed the mounting instructions in FSTAB, and everything seemed to be working fine.
The Ubuntu splash screen loaded up, and proceeded to fill itself with orange. When it got to the end, instead of showing the Nautilus loading screen, it was simply an ocean of black. I'm not easily discouraged however, and tried doing everything from resetting my xorg.conf file to totally reinstalling.
Nothing seemed to work. Even the liveCD I had previously used to install Feisty (without a hitch mind you) was failing me, with the Ubuntu splash screen refusing to even fill itself up.
I tried a text install from the alternate 32bit CD (as suggested by a sticky topic in this forum, with regard to my video card) and still, my system refused to get beyond the Ubuntu splash screen.
So this is where I'm at, typing desperate messages from my Macbook in hopes that I won't have to break out my Windows XP install disc. I realize with my video card that I am prone to adversity in the world of Linux, but thats fine by me.
If anyone can help me out, I would greatly appreciate it. There seem to be some very bright folks around here, so my hopes are pretty high!
Thanks in advance!
*Edit:* I can boot into GDM just fine from the recovery console, however upon doing so I get the "Failed to initialize HAL" error. This never happened before I mounted my other HD.

---

### Post by myacademy on 2007-07-02
Problem solved!
Figured I'd bump this, just in case anyone is having a similar problem.
Anyway, after I removed the problem drive, I set the primary IDE slave to "none" in my BIOS.
Turns out that to make all my components play nicely, I had to change the "none" setting to "auto."
For some reason or another, my computer just liked figuring things out on its own, rather than being told straight up.
Hope this helps someone! Mods can lock this and mark it as solved!

---

