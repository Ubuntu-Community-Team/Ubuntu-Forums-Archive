---
title: "How To: Speed up Firefox"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-26
Just thought I'd share this post from my blog.  It's really helped me!

This tip will work on any of the official Firefox builds (Windoze and all Linux distros included). I've personally tried it on Ubuntu Edgy Eft, Feisty Fawn, and Windoze XP.

---------------------------------------------------------------------------------------------------------------------------

Here's something for broadband people that will really speed Firefox up:

1.Type "about:config" into the address bar and hit return. Scroll down and look for the following entries:

"network.http.pipelining"

"network.http.proxy.pipelining"

"network.http.pipelining.maxrequests"

2. Alter the entries as follows:

Set "network.http.pipelining" to "true"

Set "network.http.proxy.pipelining" to "true"

Set "network.http.pipelining.maxrequests" to 30.

3. Lastly right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0".

If you're using a broadband connection you'll load pages MUCH faster now!

---

### Post by Kobalt on 2007-04-26
Setting the pipelining to a number of 30 will turn Firefox into a nightmare for webmasters, as it will literally suck up the website bandwidth...
Up to 5 would be much more reasonable IMHO...

---

### Post by Seisen on 2007-04-26
I think there is a how-to in the ubuntu forums on how to do this already.

---

### Post by crazyclown on 2007-04-26
I was about to look for this information again.  I did these updates on my wifes WinXP machine, but have not made the changes yet to my Kubunu machine.

---

### Post by locke.dragon on 2007-04-26
it may turn it into a nightmare, but it makes it ALOT faster for the user.  which is what most people want.  it's up to the user to decide whether they want to do this or not.

---

### Post by fatphilthethird on 2007-04-26
Yeah, I thought that this was do-able in a technical sense, but considered rather bad form. Loooong discussion about it on Kuroshin where I first saw it a few years ago. 

If you want faster firefox, install Swiftfox. Much faster on my crappy old machine

---

### Post by locke.dragon on 2007-04-26
oh well.  i'll stick with this method.  i much prefer the normal firefox build.

---

### Post by Dragon546 on 2007-04-26
You can also install the fasterfox extension which does a similar job.

---

### Post by the_axiom on 2007-04-26
does this tip also work with ff in windows?

---

### Post by EddyMac on 2007-04-26
Yes it does

---

### Post by merlinus on 2007-04-26
> **the_axiom said:**
> does this tip also work with ff in windows?

Definitely!  At least with Win2000.

-merlin

---

### Post by locke.dragon on 2007-04-26
this tip will work on any of the official firefox builds.  i've tried it on ubuntu and windows xp and it works without a hitch.

---

### Post by UNOwen on 2007-04-26
[quote=Kobalt]Setting the pipelining to a number of 30 will turn Firefox into a nightmare for webmasters, as it will literally suck up the website bandwidth...[/quote]

I wouldn't worry about it. The official description for "network.http.pipelining.maxrequests" is:

> Determines the maximum number of HTTP requests in the pipeline (sent sequentially without waiting for a response). Values greater than 8 are assumed to be 8; values less than 1 are assumed to be 1. Default value is 4.

So it doesn't matter how high you set the preference, you are only going to get a maximum of 8 requests at one time.

UNOwen

---

### Post by zubrug on 2007-04-26
Just install opera, it is the speed queen out of the box!

---

### Post by supersonicdarky on 2007-04-26
this is REALLY old. its been around since firefox 0.7 i think (if not earlier).

as an alternative, there's [fasterfox](http://fasterfox.mozdev.org/)

---

### Post by locke.dragon on 2007-04-27
i realize there are other alternatives, i just prefer firefox to all of them and i like the hands-on feeling of editing about:config.  so you all can use what you want, extensions, different browser, whatever.  but i'm sticking with firefox, and it's a heck of a lot faster after this mod.  and sorry it's a tad old.  i know it is, i just thought i'd post it for the few who didn't know about it!  :D

---

