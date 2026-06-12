---
title: "Old version of Xubuntu??"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-03
Hello, I have a version of Xubuntu 6.0.6 beta flight 7 that I downloaded and burn to disk a few months back in late May. So, my question is about updates for Xubuntu. If I dual boot this Xubuntu 6.0.6 flight 7 that wasn't completely stable back then, is there a way to update to the "Long Term Support" for Xubuntu 6.10 Knot 3?

I could easily go through the same steps that I did in the past to download a new release of the Xubuntu 6.0.6 LTS and burn it to ISO, but if I am able to update through an update manager, it would save a little time.

Also, is Xubuntu 6.0.6 LTS "Dapper Drake" the same as Xubuntu 6.10 Knot 3? 

thanks,
-c.

...Also, can anybody tell me what the difference between a "Knot" and a "Beta" is?? I saw a version of Xubuntu 6.10 Beta 1 "Edgy Eft" on Softpedia and am wondering if I download that, is it like the Xubuntu 6.0.6 LTS with a few add-ons, or is completely different and possibly unstable?

....and last, will I have to check the Softpedia 386 ISO image for corruption with the md5summer?

---

### Post by pay on 2006-10-03
Xubuntu 6.06 Dapper drake is not the same as Xubuntu 6.10 knot. Xubuntu 6,06 flight 7 can be updated to Xubuntu 6.06.1 by using the command```
sudo aptitude update && sudo aptitude dist-upgrade
```To update to edgy (6.10), you need to change your /etc/apt/sources.list with edgy's sources list, though I wouldn't recommend this if you are new to Linux.

The difference between knot and beta is that knot is pre beta/alpha and beta is beta. The development goes Alpha (knot), Beta, Release candidate. Final release.

And its not a bad idea to check the md5sum for corruption but not essential.

---

