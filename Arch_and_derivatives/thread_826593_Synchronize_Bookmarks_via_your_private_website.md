---
title: "Synchronize Bookmarks via your private website?"
date: 2008-06-12
forum: Arch and derivatives
---

### Post by handy on 2008-06-12
I run multiple distro's & Leopard, using Firefox on all of them as my web browser.

My question is, is there a software package or another way, in which I can synchronize my various implementations of Firefox's Bookmarks using the free space provided by my ISP for my account?

I have had basic web skills, though I haven't used them for years, I can build myself a web site.

I need both Arch/Linux & Leopard to be able to use whatever method, so one would think that it would need to be a Firefox add-on at the client side.

Obviously it would be very convenient to synchronize my Bookmarks in this fashion, though I will not use any of the Firefox Add-ons that do this because I consider all that I have seen to be spyware in the service of the evil marketroids!

---

### Post by lisati on 2008-06-12
> **handy said:**
> I will not use any of the Firefox Add-ons that do this because I consider them to be spyware & have so, done with out their superficial benefits.

If there wasn't this objection, I'd suggest Foxmarks.

---

### Post by handy on 2008-06-12
> **lisati said:**
> If there wasn't this objection, I'd suggest Foxmarks.

Boy, you were quick, I was still (obviously) creating the final release of the post & there was a reply! :-)

I am thinking that someone must have written something for the private user who desires/needs to be protected from the marketroids.

---

### Post by fwojciec on 2008-06-12
> **handy said:**
> Boy, you were quick, I was still (obviously) creating the final release of the post & there was a reply! :-)

I am thinking that someone must have written something for the private user who desires/needs to be protected from the marketroids.

I've never tried it myself, but foxmarks actually lets you specify an url to use "your own server" (Settings -> Advanced tab).

---

### Post by handy on 2008-06-13
> **lisati said:**
> If there wasn't this objection, I'd suggest Foxmarks.

> **fwojciec said:**
> I've never tried it myself, but foxmarks actually lets you specify an url to use "your own server" (Settings -> Advanced tab).

Thank you both, I will check it out, if foxmarks can be prevented from *phoning home* it sounds perfect.

---

### Post by handy on 2008-06-16
I am using foxmarks on both my Leopard & Arch systems to synch' my Firefox Bookmarks.  It works very well, gives me the option (which I use) to encrypt both my password & my data.  There are a few cookies involved, I'll play around with them though I expect I will need to keep at least one of them.

So, I am not using my own server, foxmarks looks (at this stage anyway), as though it is not invasive regarding privacy.  Which is a refreshing change. :-)

---

### Post by niksun on 2008-07-22
Actually, Google has discontinued their great BrowserSync and released the client-side code free.  I'm thinking of checking it out to see if I could use it to do the same thing.

Oh, I've recently taken to basically using sshfs (allows mounting file systems over ssh) to mount my main Firefox profile (on my server) to all of the computers I use Firefox on (laptop, work, etc).  So basically, every time I fire up Firefox on some computer, it just uses the profile on my main server machine--remotely.  Adding bookmarks and stuff is great because the main profile is the only one ever modified.  Of course, you'll have to edit the profiles.ini (typically in ~/.mozilla/firefox) to point to the mount point.

I must mention that there may be some slight problems with simultaneous open Firefox windows (I've done some testing, but nothing thorough), but I haven't noticed anything yet.

If you need help with all of this, let me know and I'll post a reply in the form of a simple tutorial.

--Niksun

---

### Post by handy on 2008-07-23
Your solution sounds very interesting, (though it is not suitable for my situation). I'm sure there are others who would be interested in details. 

If you made a how-to & posted it in the ***Tutorials & Tips*** sub-forum, it would then be seen by many more users?

---

### Post by johnlvs2run on 2008-07-30
> **handy said:**
> I will not use any of the Firefox Add-ons that do this because I consider all that I have seen to be spyware in the service of the evil marketroids!

I use [http://del.icio.us/](http://del.icio.us/) and haven't been bothered by any marketroids.

This is sure a much better and easier way to keep track of things.

I got rid of all of my bookmarks the first day of using it.

---

