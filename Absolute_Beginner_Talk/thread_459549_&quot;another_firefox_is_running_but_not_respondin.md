---
title: "&quot;another firefox is running but not responding please restart&quot;"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by medya on 2007-05-30
hey every often , firefox becomes stupid and when I run it says 
"another firefox is running but not responding please restart your system"

is there any way to run firefox without restarting it ? I am sick of restarting my whole system just because of firefox...and it happens much !

---

### Post by alienexplorers on 2007-05-30
If this is a continual problem you might try making a new profile.  You profile may be corrupted.  I had this problem and making the new profile helped.

---

### Post by Acglaphotis on 2007-05-30
when that happens do a:

```
killall firefox firefox-bin
```

---

### Post by floke on 2007-05-30
Or go to system monitor and kill firefox.bin

---

### Post by northicert on 2007-05-30
This happens to me but under different situation.  It could help and it doesn't hurt to try.  If I click on the X to close FF and it asks me if I want to close tabs I say no.  If I close all tabs this way it doesn't shut down the browser.  Close each tab by itself.  It's a pain to do but if you're on a server you can't always shut the server down whenever you want to.

---

### Post by eeried on 2007-05-31
A friend of mine has had exactly the same problem: Xubuntu Dapper.
Creating a new profile didn't help.
I ended up removing Firefox and installed Firefox2 from mozilla.com. now of course as firefox is part and parcel of Xubuntu desktop, no end of problem, I'm going to reinstall Dapper.

The tight integration of software into a desktop environment or Ubuntu itself is a bad thing. I'd like to be free to remove firefox without removing a host of other things. This really sucks.
When I started with Linux (Libranet distro, Debian-based, about 3-4 years ago) things were simpler. You could remove whatever you wanted. Dependencies existed of course, but not on that scale. It seems to be getting rather like M$ and its IE,OE etc. :-\

---

### Post by rajeev1204 on 2007-05-31
> **Acglaphotis said:**
> when that happens do a:

```
killall firefox firefox-bin
```



Yep this is what i would suggest too .

Happens to me a lot of times .

---

### Post by eeried on 2007-05-31
> **rajeev1204 said:**
> Yep this is what i would suggest too .

Happens to me a lot of times .

Okay, thanks for the tip but I'm not sure this is an entirely acceptable situation. not a very nice thing for newbies eager to enjoy Linux, is it?

---

### Post by rajeev1204 on 2007-05-31
> **eeried said:**
> Okay, thanks for the tip but I'm not sure this is an entirely acceptable situation. not a very nice thing for newbies eager to enjoy Linux, is it?


Hi

Actually what i have noticed is when u quit firefox or it crashes for some reason and we immediately try to restart it , we get that error .

Waiting a few seconds before restarting  is a good idea .


Also when it says another FF is already running , that is the first thing we all do .... go to system monitor and kill it .

---

### Post by apunc1 on 2007-05-31
it's a multi platform firefox bug

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by HarmonicaGoldfish on 2007-05-31
> **eeried said:**
> Okay, thanks for the tip but I'm not sure this is an entirely acceptable situation. not a very nice thing for newbies eager to enjoy Linux, is it?

Same thing happens in windows and you have to 'kill' it in the system monitor by shutting  off the process. 

Seems like a FF issue to me, not a linux one. 

Seeing as it happens across platforms I don't think something like that would affect a newbie's (which I am ;)) decision to go linux.

---

### Post by eeried on 2007-05-31
Glad to hear it isn't an Ubuntu issue! I have no recent experience of Firefox in Windows so I wouldn't know. 

It'd be a good idea to report this issue on the Mozillazine forum then.

---

### Post by apunc1 on 2007-05-31
> **eeried said:**
> 

It'd be a good idea to report this issue on the Mozillazine forum then.

they are aware

> apunc1 	it's a multi platform firefox bug

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

---

### Post by nvteighen on 2007-05-31
I can assure you I got this message in WinXP with some frequence. The solution in Windows is Ctrl+Alt+Del and stop (I reserve "kill" for Linux systems) firefox.exe.

---

### Post by GabrielDunn on 2007-05-31
killall firefox firefox-bin

is the fix..its like ending the process in XP.  Usually if the program crashes but is still active in memory this can happen.  The kill switch above should dump it.

---

### Post by medya on 2007-05-31
wow I see this topic become so popular, just waned to say the kill thing didnt work for me but I think the ohter things which explained in [http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)
will help me

---

### Post by eeried on 2007-06-01
I've never had this problem with Firefox, ever -- been using it for 2,5 years. Strange..

I have other problems with Firefox, though -- [http://ubuntuforums.org/showthread.php?t=451244](http://ubuntuforums.org/showthread.php?t=451244)

---

