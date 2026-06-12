---
title: "[SOLVED] firefox crash???"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Fanin on 2007-10-24
I'm having a small problem with firefox. sometimes when it works with two tabs or more it just crashes and i have to "force quit" this doesn't happen every time i open a tab but just some times.
could it be because skype and ktorrent is also running, or just because my computer is slow
i installed gutsy 3 days ago and this didn't happen 'till yesterday :confused:
oh, and btw i'm a total noob so be gentle, huh? :)

---

### Post by FuturePilot on 2007-10-24
Are you viewing a site with any type of Flash content when it happens?

---

### Post by Fanin on 2007-10-24
> **FuturePilot said:**
> Are you viewing a site with any type of Flash content when it happens?

hmm, it does happen every time i try to install flash plugin in youtube.com
is that a problem?

---

### Post by enetic on 2007-10-24
i have a similar problem. when i watch youtube videos, firefox crashes sometimes...

---

### Post by TZRick on 2007-10-27
Is there anyway to make flash more stable?  Opera uses the Firefox Flash plugin and it is even worse...although the browser itself is more stable, the Flash applets crash and a square, grey box appears instead.  I've actually had instability issues with Firefox since 7.04, but I think it has gotten worse with 7.10.

---

### Post by Fanin on 2007-10-29
hmm, when ever I went to youtube (or anywhere) and tried to install flash plug-in, my computer crashed, but after a couple of tries and a lot of patience it worked.
it works just fine now :)
not exactly sure why it worked after a couple of tries. If anyone knows please do tell

---

### Post by laidback on 2007-10-29
My Firefox locks (crashes) when I use Youtube. I have to Force Quit or use System Monitor to Kill it. Happens more often than not. I'm pleased to read that others have the same problem; makes me feel better as previously I was under the impression I was always doing something wrong. Hitting the pause button will almost certainly cause a crash.

---

### Post by philinux on 2007-10-29
4 tabs up two youtube - no crash :confused:

I'm using 

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by TZRick on 2007-10-29
Well, I did something which seems to have made Flash more stable...no crashes since (fingers crossed).  I found out that Firefox had its own copy of Flash which was separate from the one that was installed on the system (weird, I know).  So, I went in and uninstalled Flash from Synaptic and then started removing all instances of Flash.  I did a search for libflashplayer.so and flashplayer.xpt (I think those are the correct filenames).  After removing all, and verifying that Firefox was once again prompting me to install Flash, I went back into Synaptic, found Flash and installed.  I think things are running better now.

Hope that helps.

---

