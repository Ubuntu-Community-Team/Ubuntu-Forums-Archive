---
title: "Shaking Wacom"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by buddhalover on 2006-08-19
I've done the steps in this guide [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

The Tablet has been detected before hand but the cursor is shaky.
I did the steps outlined in the guide in the hopes that the shaking stops.
It didn't work.

Any suggestions?

---

### Post by slimdog360 on 2006-08-19
stop drinking so much coffee? sorry I had to say that, I was compelled.

---

### Post by buddhalover on 2006-08-19
It's not my hands. :-\" 
It moves around but when pressure is applied the cursor begins to shake.
[crazee... ]("http://www.youtube.com/watch?v=7KWEN4wKaMc")

---

### Post by buddhalover on 2006-08-20
Why is it shaky when pressure is applied? 
The thing worked fine back in XP. :p 
To give it to Ubuntu, it was instantly detected prior to
my following the steps in the guide.
I really hope to get it working here in Linux.
All the help would be deeply appreciated.
I cannot draw with the shaking. :(

---

### Post by buddhalover on 2006-08-21
](*,)

---

### Post by buddhalover on 2006-08-22
Can no one help?

---

### Post by buddhalover on 2006-08-24
](*,)	](*,)	](*,)	](*,)	](*,)	](*,)	](*,)	](*,)

---

### Post by buddhalover on 2006-10-10
Perhaps someone can encountered this problem before?
I would really appreciate some help on this. Thanks. :)

---

### Post by buddhalover on 2006-10-10
I am presently using the shaking-cursor tablet.
It is usable and I've learned to be less annoyed but would still like help fixing it. (I can draw very shaky drawings) What details would you require in order for you to understand the problem better? And where would I find those details?

---

### Post by karora on 2006-11-08
Hi,

I am having the same problem with the Wacom Graphire tablet giving a shaky mouse cursor.  Well, my wife really, but I have to fix the &$%*&^ problem or I'll have to install XP on a PC for her and I would dearly love to have the tablet working for her in The Gimp so she can at least try and learn to use that rather than Photoshop (which she admittedly does some beautiful work with).

Anyway, I have given up on getting it working with Dapper and have upgraded her to Edgy to see if that makes a difference.

Things that I can confirm did not make a difference are:

Option "Suppress" "6"

and many other tweaks to settings and stuff.

If the Edgy upgrade doesn't fix it I will try with a 2.6.18.1 kernel and the absolute latest Wacom drivers.

Failing that I will try hacking the Wacom drivers to allow arbitrarily setting the "Suppress" option to numbers larger than "6".


I have found looking at wacdump (without X even running) that the tablet is returning a constantly shifting position.  This very strongly suggests that (a) it is not a problem with interaction between mouse and wacom, and (b) it is not a problem with the XInput driver.

I will report back later with my success (or failure)...

Regards,
Andrew McMillan.

---

### Post by karora on 2006-11-09
Well I have tried a whole bunch of things with my wife's Wacom Graphire to try and reduce the jitter, but unfortunately without success...

I have tried using the absolute latest drivers and a 2.6.18.1 kernel as well, on my laptop, and I still see way too much jitter for it to be useful.  The problem seems to definitely be in the kernel driver, rather than in X.

I also tried a much newer Graphire 4 that one of our designers at work was using, and when I look at that with 'wacdump' it only ever seems to twitch the X/Y location by 1 digit, rather than the older tablet which twitches it +/- about 10 digits.

I've logged a whole bunch of stuff about the tablet though, including problems with it detecting the switch from Pen -> Eraser and back, and have now filed two bugs on the linuxwacom project about it:
[Jitter problem]("http://sourceforge.net/tracker/index.php?func=detail&aid=1593800&group_id=69596&atid=525124")
[PEN/ERASER switch not noticed]("http://sourceforge.net/tracker/index.php?func=detail&aid=1593805&group_id=69596&atid=525124")

Meanwhile, I've ordered a new Graphire 4 to keep [Heather]("http://fibrilliform.comics.geek.nz/") happy :-)

Regards
Andrew McMillan

---

### Post by euchrid on 2006-11-20
I had this problem too; have you edited your xorg.cong file? I found, when I edited it with Gedit, that it left behind a *second* xorg.conf (with '~' at the end of it). Deleting it stopped the shaking. (Have a look in /etc/X11 just in case something weird happened and another program did this to you would be another suggestion).

Also, to get my tablet working, I had to remove (using Synaptic) all the wacom-tools, wacom-kernel-source and xserver-xorg-input-wacom packages, then install linuxwacom and set it up. See [this post]("http://ubuntuforums.org/showthread.php?p=1782974#post1782974").

Over the course of my experimenting, I found restarting the computer (not just X) seemed to sort out another occasion when I had some shaking of the cursor. It seems to happen when another program is in some sort of conflict; as if two drivers are fighting for control of the tablet. You don't have Kubuntu or Xubuntu installed as well, do you? That gave me a couple of weird problems (now sorted too).

Hope this helps! Good luck.

---

