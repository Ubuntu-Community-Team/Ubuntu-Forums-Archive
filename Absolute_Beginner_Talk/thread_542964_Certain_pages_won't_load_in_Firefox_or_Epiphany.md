---
title: "Certain pages won't load in Firefox or Epiphany"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by badmigraine on 2007-09-04
Using Feisty and the standard Firefox and Epiphany browser installs on both my laptop and desktop, and having this problem with both computers:

About two weeks ago I began having problems loading the Digg and BoingBoing sites. Digg loads the site's upper banner, but the content/rest of page takes ten minutes or more to load, and sometimes never loads at all. BoingBoing times out and never loads anything.

Other sites (CNN, PC Mag, newspaper sites, forums, Engadget, Gizmodo, etc.) load fine and quickly. I have a broadband connection which is configured properly.

When I boot into Windows, Digg and BoingBoing load fine and quickly, so it is not a firewall issue with my router. Also, Digg and BoingBoing worked fine in this Ubuntu install up until about 2 weeks ago. I didn't change anything, except allow system updates.

The pages also won't load through an anonymous proxy server or using Babelfish translation engine.

I tried disabling ipv6, but this did nothing.

I tried enabling pipelining, but that did nothing.

I disabled my add-ons, but this did nothing.

Any ideas what could be causing this?

---

### Post by sbassett on 2007-09-04
I would suggest giving [opendns]("http://www.opendns.com") a try. I have used it on many occasions and have been fairly impressed with the results.

---

### Post by alienexplorers on 2007-09-04
have you done any recent updates especially to Flash or Java recently?

---

### Post by badmigraine on 2007-09-04
> **sbassett said:**
> I would suggest giving [opendns]("http://www.opendns.com") a try. I have used it on many occasions and have been fairly impressed with the results.
I tried opendns, but the problem remains. Digg and BoingBoing do not load.

I like opendns though, and will keep using it, thanks!

---

### Post by badmigraine on 2007-09-04
> **alienexplorers said:**
> have you done any recent updates especially to Flash or Java recently?
No changes to Flash or Java, unless they came as part of a normal Ubuntu automatic update!

---

### Post by sbassett on 2007-09-04
I agree with alien, check for any flash updates. If need be, remove flash via synaptic, close your browser, open it back up and visit one of the offending sites, it should ask you to install flash automatically. Let us know...

---

### Post by backinthecity on 2007-09-04
just update and then give it a shot. I can't see why your running into that problem... 
it may be possiable you have something setup where it blocks content... I recall a past post and they had ad block type ordeal but def give the java/flash updates first. Good luck

---

### Post by badmigraine on 2007-09-04
Thanks for the support, when I get home I'll try uninstalling Flash and see what happens! 

Now trapped at work for the next 10 hrs. or so...yuck!

---

### Post by badmigraine on 2007-09-05
Uninstalling Flash made no difference in the problem. 

When I re-installed Flash, Digg loaded immediately the first time, but after that is back to never loading. BoingBoing continues to time out, without loading at all.

This is really weird! Any more ideas on what it could be?

---

