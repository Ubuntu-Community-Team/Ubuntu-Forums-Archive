---
title: "Firefox 32 vs 64 bit - having problems"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by marmaladejackson on 2007-12-02
Greeting all,

I am running the 64 bit version of Gutsy and have been on the 64 bit platform since I first starting using Ubuntu almost a year ago.  When I first started, someone walked me through force installing the 32 bit version of Firefox because certain flash and java programs would not work.  This was fine as far as I was concerned until yesterday when most embedded media just stopped playing.  I was thinking of switching over to the 64 bit version anyway, so I did and have a few small, but infuriating problems.  First the controls on some embedded media like youtube are all screwed up (not really a big deal).  The other problem, which is a bid deal is that when I use my company's email from home (Novell Groupwise 7.0 WebAccess), anytime I try to forward or reply to an email, the browser crashes.

Right now my work around is that anytime I do "normal" surfing, I use the 64 bit.  Anytime I need to do any stuff for work, I close down the 64 bit and launch the 32 bit. 

Anybody have any suggestions?

Thanks!

-- UPDATE -- 

Ok after a little more experimentation, I don't think the browser is crashing in response to the reply or forward function from the WebAccess email, rather because a third window is being opened.  I just noticed I can surf with two windows open just fine, but once I try and open a third, it all crashes.  Does that help anybody?

Thanks.

---

### Post by swegner on 2007-12-09
Hi,

I am also running 64-bit gutsy, and have had my fair-share of trouble with firefox plugins.  I'm no expert, but here's what I can suggest:

-- 64-bit firefox got much better from feisty to gutsy.  There's now an emulation layer for 32-bit plugins (I believe it's called nspluginwrapper), so you shouldn't need to use 32-bit firefox anymore.

-- There's also better plugin detection that should do most of the setup for you the first time you visit a flash site.  If you don't see it, I would try uninstalling any flash plugins you currently have setup.  It might be one of the following:

flashplugin-nonfree
libflash-mozplugin
mozilla-plugin-gnash

Once you've removed these packages, restart firefox and go to a flash-enabled website.  A dialog should come up prompting you to install a flash plugin.  I would recommend the non-free plugin from Adobe, as it has very good youtube support.


Hope this help.  Once again, I'm not expert, but this has been my experience.

---

### Post by marmaladejackson on 2007-12-09
Thanks for the tip.  I was able to get firefox32 up and running ok again, so no worries.  I'll give the 64 bit version another try when 8.04 comes out.

Thanks again!

-B

---

