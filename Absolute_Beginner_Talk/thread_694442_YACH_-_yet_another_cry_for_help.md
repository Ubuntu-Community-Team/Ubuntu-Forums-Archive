---
title: "YACH - yet another cry for help"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-02-12
I've got to be messing up something somewhere, but I don't know what or where.

The problem:  I have a PIII-500 system with 512mb.  I had done a fresh install of Gutsy when it first was released and ran it for a couple of months.  I seemed to have problems with video either just staying on 1 frame or being all choppy.  I had the "bad" and "ugly" packages installed so I could supposedly play wmv files, etc..  Yet everything was always choppy or didn't move - even things like ABC news clips on the net.  I had additional problems - mainly that my cpu seemed pegged all the time.

So, I put in an 80gig drive and did a fresh install of Feisty in it.  Installed vmware server so I have an old version of win98 running so I can run Family Tree Maker.  Everything was going along just fine - the aforementioned videos played fine, etc..

Then I installed Pitivi, avidemux and Cinelerra, as I need to do some rudimentary video editing.

In the meantime Ubuntu has applied a few updates as well.

Now my video problems are back.  It either stays on one frame while the counter goes up, or it is VERY choppy.

I'm at my wits end - can anyone advise me?

Thanks so much! :)

---

### Post by banewman on 2008-02-12
Which video player are you using?
I always use vlc as it has never had an issue on any of my systems and plays all codecs I can find.
Try it and see if that is the issue
:)

---

### Post by oedha on 2008-02-12
install gstreamers or ubuntu-restricted-extras
install vlc
work fine on me........:)

---

### Post by anewguy on 2008-02-14
Installed VLC and already had the gstreamer packages as mentioned.  Still not good.  One of the things that gives me problems is when looking at a news video linked from Yahoo.  I checked the package in synaptic that said it was a VLC addon for Firefox, yet that doesn't show under tools/addons, if it is supposed to.

Perhaps a PIII-500 is too slow for all of this?

Thanks!:)

---

### Post by oedha on 2008-02-14
you just watch it.....doesnt related to your specs.......maybe the connection.........

---

### Post by anewguy on 2008-02-15
> **oedha said:**
> you just watch it.....doesnt related to your specs.......maybe the connection.........

This is the quandry - I COULD just watch it when I first installed Feisty 7.04.  When I installed Gutsy 7.10 from scratch I had these problems.  I did a completely new install of Feisty again - worked at first, but apparently one of the updates done automatically has changed something, as I can't just watch it anymore.

---

### Post by spiderbatdad on 2008-02-15
ubuntu-restricted-extras? Did you install it?

---

### Post by agim on 2008-02-15
I had some problems with vlc as well. I now use mplayer, and mozilla-mplayer. Its works so much better for me.

---

### Post by anewguy on 2008-02-16
> **spiderbatdad said:**
> ubuntu-restricted-extras? Did you install it?

Yes - had that installed before everything went wacky.  :)

---

### Post by anewguy on 2008-02-18
bump.

---

### Post by Beefeater on 2008-02-19
Try changing the Output module in vlc to "X11 video output" and see if it gets you started with vlc at least.

---

### Post by slambrick on 2008-02-19
> **anewguy said:**
> I've got to be messing up something somewhere, but I don't know what or where.

The problem:  I have a PIII-500 system with 512mb.  I had done a fresh install of Gutsy when it first was released and ran it for a couple of months.  I seemed to have problems with video either just staying on 1 frame or being all choppy.  I had the "bad" and "ugly" packages installed so I could supposedly play wmv files, etc..  Yet everything was always choppy or didn't move - even things like ABC news clips on the net.  I had additional problems - mainly that my cpu seemed pegged all the time.

So, I put in an 80gig drive and did a fresh install of Feisty in it.  Installed vmware server so I have an old version of win98 running so I can run Family Tree Maker.  Everything was going along just fine - the aforementioned videos played fine, etc..

Then I installed Pitivi, avidemux and Cinelerra, as I need to do some rudimentary video editing.

In the meantime Ubuntu has applied a few updates as well.



Now my video problems are back.  It either stays on one frame while the counter goes up, or it is VERY choppy.

I'm at my wits end - can anyone advise me?

Thanks so much! :)

Make sure your video card has the right drivers as well. If you use nvidia or ati try installing ENVY.

---

