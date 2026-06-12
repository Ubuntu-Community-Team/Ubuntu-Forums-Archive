---
title: "Adobe FlashPlayer and Opera 9.24"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by PunkLV on 2007-10-25
Good day. Firt of all id like to say that ive been using Linux for the first time in my life, for the past straight 17 hours, i even began to belive in God, and that he likes me, when i got my NV drivers set up and fixed resolution problems, set up network+Inet, got opera, and flash-player (from the main site), did everything in terminal, thanks to sudo, SO NOW: ive spent last 3 hours in search of a solution to my problem (tried them all (reverting any changes if unsuccessful)), so its likely that ive just missed what ive been looking for, if so, im sorry for this thread, but im desperate.

**The Problem Is:** when i start viewing ANY flash video (YouTube, etc) it begins to load, it starts, and on the 20-80th sec WHOLE system freezes, like the "blue screen of death" in XP. Is there a way to fix this, or at least, WHY?

---

### Post by TeaSwigger on 2007-10-25
> **PunkLV said:**
> Good day. Firt of all id like to say that ive been using Linux for the first time in my life, for the past straight 17 hours, i even began to belive in God, and that he likes me, when i got my NV drivers set up and fixed resolution problems, set up network+Inet, got opera, and flash-player (from the main site), did everything in terminal, thanks to sudo, SO NOW: ive spent last 3 hours in search of a solution to my problem (tried them all (reverting any changes if unsuccessful)), so its likely that ive just missed what ive been looking for, if so, im sorry for this thread, but im desperate.

**The Problem Is:** when i start viewing ANY flash video (YouTube, etc) it begins to load, it starts, and on the 20-80th sec WHOLE system freezes, like the "blue screen of death" in XP. Is there a way to fix this, or at least, WHY?

It's working fine here (that is, Flash on Firefox and Konqueror, I don't use Opera). If it's supposed to work in Opera on Linux then you'll get it working. Why it's allowing your whole system to freeze, that's the question. So: you've worked on the graphics end already. But that's a suspect. In the file /etc/X11/xorg.conf, is it actually, specifically using the nvidia "driver"? Rather than saying "generic" or "vesa" or whatever. 

If you run (enter in a terminal) glxgears, how's the performance? Smooth or at all jerky?

And take it easy ;)

---

### Post by shad0w_walker on 2007-10-25
I would suggest you quickly have a look at the same sites from a different browser(s) and see if the same thing occurs. If it does then it helps to narrow it down from being either opera or flash or something different to just flash or something else (The above post is a possibilty)

If flash still crashes your system from firefox or epiphany or some other browser then its possible that somehow your install of flash is damaged or there is something else happening. If it doesn't then it helps narrow it down to something about the combination of flash and opera.

---

### Post by PunkLV on 2007-10-25
**20995 frames in 5.0 seconds = 4198.856 FPS**

Yes, 'nvidia' is in use, i guess 

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600"
EndSection

I know i can use FireFox, or whatever, (i dont want to start a "my browser ROCKS!"-type discussion) i just like Opera and what to use it. 

Mostly my concern is: WHY it freezes..

**2 shad0w_walker**

searched opera.com /adobe / developers / irc (not official ubuntu) supports... no luck

PS even when I press Save button upon editing this post, flash (i guess) animation plays OK, as all the res flash content on any sites, but not videos...

---

### Post by shad0w_walker on 2007-10-25
I don't think anyone is suggesting you switch browser, but know if it works or not in another is going to help out with this. Just try it. If it works, fantastic, we know its something specific to flash and opera, if it doesn't then its more likely a specific problem with flash.

---

### Post by PunkLV on 2007-10-25
> **shad0w_walker said:**
> I don't think anyone is suggesting you switch browser, but know if it works or not in another is going to help out with this. Just try it. If it works, fantastic, we know its something specific to flash and opera, if it doesn't then its more likely a specific problem with flash.

sorry, tired. 

Yes, it worked fine in FireFox, i belive its "opera <> flash" thing

---

### Post by shad0w_walker on 2007-10-25
Ok. Well that at least helps us narrow things down. How did you install flash? From the repos or manual download/install or?

---

### Post by PunkLV on 2007-10-25
Firefox installed it automatically. Then i DLd opera, installed it, DLd flash upon operas first request concerning flash content. than horrible stuff started, had too look through installers source code (am not a programer, dont know any language, especially python), appears that it had to find my opera plugins directory, but didnt, so, copied 'flashplugin.so' to the /usr/lib/opera/plugins.
Opera started to display flash content. Went to Youtube to try for sure -> failed. 
Removed firefox, opera, flash. used apt-get, same result, --purge remove.
Opened Synaptic Packet Manager, same actions, same result.
Add/Remove.. same result

Though, there were posts somewhere, that Flash player 6 works with opera fine.. will try that, if there will be no other options

---

### Post by shad0w_walker on 2007-10-25
That's very odd. I'm not quite sure what to suggest on it so I'll post and give you a bump so maybe someone else can help you out.

---

### Post by zvacet on 2007-10-25
[http://www.opera.com/linux/docs/plugins/install/]("http://www.opera.com/linux/docs/plugins/install/")

---

### Post by PunkLV on 2007-10-25
Yeap, tried that too, seemed too obvious to mention. ANYWHO

I DID IT! that ******* thing conflicts with Gnome desktop effects (Cube and Wobbling windows)

---

### Post by brn on 2007-10-25
You might look at ~/.opera/pluginpath.ini to see where Opera is looking for plugins.  Here is what mine contains:
> [Paths]
/usr/lib/opera/plugins=1
/usr/lib/mozilla/plugins=1
/usr/lib/flashplugin-nonfree=1
/home/brn/.mozilla/plugins=1
/usr/lib/firefox/plugins=1
/usr/lib/netscape/plugins-libc6=1

Flashplayer seems to work fine for Opera here except for the speakeasy.net/speedtest where it performs the download but never gets to the upload test.  No lockup, it just doesn't run that part of the test.

---

### Post by Brian R. on 2007-10-25
I only started using opera yesterday and had trouble installin Flash, the instalation program only wanted to store it in the mozilla folder. So i just copied the /home/MYUSERNAME/.mozilla/plugins to the /home/MYUSERNAME/.opera/ folder and it seems to work ok.

---

### Post by tad1073 on 2007-12-14
My problem is that it say I don't have permisson to write to the plugin file. I am new to linux and ubuntu and I don't know commands for the terminal etc. Help please.:confused:

---

