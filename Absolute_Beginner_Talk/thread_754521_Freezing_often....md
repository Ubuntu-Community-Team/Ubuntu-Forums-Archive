---
title: "Freezing often..."
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Innernet on 2008-04-13
Hi all.
My compfuser is freezing at any time, the screen remains, the mouse moves but does not click left nor right. Power cycle is the only way to restore functionality, I do not know of other way. No hardware changes, nothing new downloaded.
In the paranoia chapter, am afraid that Google and companies are intruding and causing trouble.  I see them reported in the bottom line as 'looking for...'  and waiting for...' and 'transferring from...' while accessing web sites.

How do I forbid  doubleclick.com and google-analytics.com among other googlians from accessing my system ?

Where do I delete stored cookies and temporary internet files?

I respect favorable opinions from knowledgeable people about Google, but I am _convinced_ they are not a good thing.  They are to make _more_ money from users.

Thanks.

---

### Post by ryan22158 on 2008-04-13
> **Innernet said:**
> Hi all.
My compfuser is freezing at any time, the screen remains, the mouse moves but does not click left nor right. Power cycle is the only way to restore functionality, I do not know of other way. No hardware changes, nothing new downloaded.
In the paranoia chapter, am afraid that Google and companies are intruding and causing trouble.  I see them reported in the bottom line as 'looking for...'  and waiting for...' and 'transferring from...' while accessing web sites.

How do I forbid  doubleclick.com and google-analytics.com among other googlians from accessing my system ?

Where do I delete stored cookies and temporary internet files?

I respect favorable opinions from knowledgeable people about Google, but I am _convinced_ they are not a good thing.  They are to make _more_ money from users.

Thanks.

Okay, so I can't really help you with your computer freezing but one thing I can tell you it is not google or doubleclicks fault. 

To let you know what those site that you listed are doing is saving cookies in a folder in firefox so it can advertise to you things that it thinks are of your interest. The only way to stop them is to stop using google. Which is impossible because they are either used by a site for the search fuction. Or the site is owned by google. 

And how you delete your cookies in firefox just press the key combination ctrl+shift+del and the after the window comes up click on the blue arrow.

---

### Post by mgranet on 2008-04-13
Firefox with the NoScript plugin should do the job nicely. As for the freezing, I am also unable to assist.

---

### Post by mgmiller on 2008-04-13
As far as freezing goes, have you tried turning off compiz?  I had a similar problem when I started using beryl as my window decorator instead of compiz fusion.  I switched back to c-f and so far, no more lock ups.

---

### Post by Innernet on 2008-04-13
Thanks...
As far as I know, I do not have compiz nor beryl nor decorators.  I keep my system very lean, as originally installed; have not downloaded things I do not need. Do not go into unknown content/reputation sites.

The last time it crashed earlier today I was marking to delete arabic , chinese, laos, and other oriental alphabets and fonts from 'Synaptic package manager' and was not connected to the net at all. Not running or sharing any other operative system, 

If apport is supposed to present a UI, it did not.
In my ignorance, I cannot tell if it is a Firefox or Grub or else hiccups.

---

### Post by halitech on 2008-04-13
have you tried booting from the Live CD and running memtest? might be either a memory or heat issue

---

### Post by Innernet on 2008-04-13
Thanks, I will try that.  How do I perform a memory test?  Do I type "mem tst " on the terminal prompt ?

---

### Post by halitech on 2008-04-13
when you boot from the live cd, you should get a couple of different options, memtest should be one of them, select that and it will boot into the memtest

---

### Post by mgmiller on 2008-04-14
> As far as I know, I do not have compiz nor beryl nor decorators. I keep my system very lean, as originally installed

Ubuntu tries (as of 7.10) to enable compiz by default.  It would depend on your video card.  Take a quick look at System > Preferences > Appearance and in the visual effects tab, make sure "None" is selected.  When possible, by default, the system will select "Normal", which does use compiz-fusion.  The "None" option turns that off.

That being said, I think running memtest is a very good idea.  Make sure all your fans are working and there are no dust bunnies in the case or clogging the air intake areas/filters.

My son recently had random freezing and reboots with 7.10 that gradually got worse until one day the system simply would not boot at all.  When I checked it, I found all the air intakes and front air filter clogged with cat hair (he has 2 cats) and dust.  The memory had overheated and fried.  Neither stick would boot the machine, 2 gig up in smoke.  The manufacturer, Gskill, was good enough to replace the ram under warranty and his computer has been smooth as silk since.  I also showed him how to clean his air filters once a month or so.

---

### Post by zamb on 2008-04-14
What type is your VGA adapter?

Did it happen with older Ubuntu releases or this one (7.10) only?

Were you running anything when the system crashed? (Like running 3D applications or watching movies.)

I ask all these questions because I have a problem with my ATi Radon 8500LE that's similar to yours.  My system used to hangs at what appear to be a random intervals, until I noticed it only happened if there's something involving the VGA adapter (using Comize (instead of MetaCity) or MPlayer).

I found a stupid workaround by running```
sudo /etc/init.d/gdm restart
```immediately after I start my system (I rarely turn it off, so it doesn't bother me that much. I know I should investigate more and file a bug report, but I'm a little busy and I wouldn't know where to start).

Hope this helps.
Ziyad.

---

### Post by Innernet on 2008-04-14
Thanks.
My video port is integral of the mommyboard, an Intel D845GVSR; with Intel Celeron D325 at 2.53 GHz and 256MByte memory.   Never happened before with 7.10 until a couple of days ago nor with 3 previous versions of Ubuntu, no drivers have been altered in two years, the video driver CD was supplied with the mommyboard and installed in 2006, no downloads, same exact hardware.

The temperature should not be an issue, as I can run 6 hours and probably more listening streaming, the drives are laptop plugins on the front panel running cold, fans are clean and running fine.

It has not frozen for 24 hours since deleting cookies and cache. Hope will continue...

Edited: Added----> When froze I was browsing ebay (twice) browsing youtube (twice) and once while editing Sinaptic with DSL disconnected.

---

