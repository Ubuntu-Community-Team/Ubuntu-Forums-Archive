---
title: "Internet connection OK with Live CD not with installed application"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by Phosphoric on 2006-06-28
This seems to be a common problem with the latest version of Ubuntu.  Live CD works fine, installed version will not connect to the internet.  How crazy is that?

It can't be anything fundamentally wrong with my hardware or the drivers otherwise Live CD wouldn't work.

I've been a week now wading through the forums and have found loads of suggestions, none of which have got me on line.  (this on a windows machine!)

I had no problem with my previous version of Ubuntu ( Breezy or something) but this Dapper Drake install (clean) will not go.  

I can't talk to my router and I've tried pppoeconf which cannot find a connection to my ISP.

If I can't talk even to my router then I'm assuming this must be a driver problem.  I've tried the adding "dmfe" trick but that didn't work either.

Any other suggestions?

Thanks. ;)

---

### Post by cara on 2006-06-28
that happened to me on gentoo.. but not ubuntu.
i dont think..... i could be wrong...

---

### Post by Phosphoric on 2006-06-29
Anybody help? :)

---

### Post by confused57 on 2006-06-29
I had sort of the same problem, built a new computer with an ABIT SG-80 mobo with integrated SiS chipsets for video and ethernet.  Tried the Dapper LiveCD, but couldn't connect to the internet...went into networking, the eth0 was active and my ISP was correctly identified.  I thought, well I don't have anything to lose, so I installed Ubuntu with the Dapper alternate CD...from which I had no problem connecting to the internet...Go figure.
About the only thing I had to do was select the "sis" video driver instead of "vesa", which was automatically selected during the installation.
If you haven't tried it already, maybe you can try the alternate install CD.

---

