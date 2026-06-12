---
title: "Ubuntu Experience - Day 1"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by bbarcelo on 2007-05-05
I've just installed Ubuntu and have been using it for less than 24 hours now. I'm a novice nix user, not a beginner, but that said, it's been a long while since I've done much besides host a server with Apache or something here and there.

I have a file server that utilizes 10+ hard drives at one time and was having stability issues in Win Server 2003. It finally got to the point where I really needed to make the switch and finally did - to Feisty Ubuntu. I first tested the LiveCD to see if it would recognize all these drives across the multiple IDE and SATA controllers and, suprisingly enough, it did a great job.

So here I am now, I've configured Samba, installed one app, and used the Ubuntu Restricted Drivers Manager to install the nVidia drivers (Oh, and VNC configured correctly). The computer I'm using is as follows (short version):
CPU: AMD Athlon64 3000+
RAM: 1.5GiB Mixed DDR (@ DDR2700)
Motherboard: Soltek (Don't want to bother looking up the exact model since I forgot)
Controller Cards: Highpoint, Western Digital, and Silicon
Graphics Card: Nvidia MX420 (I can hear the sighs already)
No CD/DVD Drive. No floppy. Two PSUs that work great in tandem.

I like the look and feel of Ubuntu, though it feels a little sluggish on this machine that I consider to be pretty high end of a basic Ubuntu install. That aside though, the disk performance seems to be on par with that I achieved in Server 2003. However.. In Server 2003 my computer blue-screened, something it obviously can no longer do and THE primary reason I made the switch. While I've been writing this forum post though, my Ubuntu machine has decided to do two things, the only two things I've found wrong thus far with my switch to Linux, but GIANT problems nonetheless.

1. Kicking me out to the login screen:
[INDENT]This happens both through VNC and while using the computer with a monitor and keyboard. Not really sure why this is happening. Checked power management settings, the only real direction I had found for a fix, and everything was OK there. So this is still going on and, speak of the devil, just happened. Logging back in (which must be done at the machine) usually results in slow OS loading times and is pretty annoying to have to go and do.[/INDENT]
2. Locking up:
[INDENT]I think this is a severe issue related to my Nvidia MX series graphics card. While the graphics card inside this computer really doesn't matter, I need something that won't be interferring and crashing the machine constantly. This happened at the beginning of this post and has been happening quite a bit in the last <24 hours. Probably somewhere around 10-15 times that I have to do a hard restart. This is VERY aggravating.[/INDENT]

Attempts to fix the Lock Ups:
I've tried modifying my xorg.conf file with the following options:
NvAGP 0
RenderAccel Off
IgnoreDisplayDevices DFP,TV
NoRenderExtension Off
AllowGLXWithComposite Off

So, please, someone provide some insight that I might be able to resolve these problems and continue life as a happy nix user. I really do not like the idea of switching back to the (more stable given my conditions) Server 2003 OS.

To any Admin who feels this post might do better in the Troubleshooting section: Feel free to move this post. Just wanted to let beginners know about some of the problems they might face.

---

### Post by cypherzero on 2007-05-05
Feisty is still kind of new, if your using your computer as a server rather than as a workspace have you considered trying Dapper LTS, it should be much more stable?

---

### Post by ubnewbie2 on 2007-05-06
I think both problems may be related to the graphics card driver.  Are you using the restricted driver (the one from nvidia)?  If not, it's worth a try, and if you are, try not using it.  See which is more stable.

---

### Post by knightnet on 2007-05-11
If you were having problems under Windows and now under Linux, I would strongly suggest that you have hardware problems.

Sadly, these are all too common on modern hardware that is constantly pushing the limits for minimal margins.

It may be time to start swapping components to find out where the problem lies. I've had similar problems on my PC's in the past. They have invariably come down to dieing motherboards, memory or other components.


Regards, J.

---

### Post by bbarcelo on 2007-06-12
Just realized I never updated this post. Even though memtest86 had showed all of my RAM to be in perfect working order, I experimented with uptimes while certain sticks of RAM were in and out. My conclusion was that a 1GB stick, of course, had gone bad. Bad according to my personal opinion, not according to any technical tests I could run with any kind of results. So it is that compatibility stood strong and that the real failure of the system was due to some cloaked faulty RAM.

---

