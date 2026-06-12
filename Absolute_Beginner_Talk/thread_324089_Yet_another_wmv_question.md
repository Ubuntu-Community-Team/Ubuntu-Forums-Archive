---
title: "Yet another wmv question"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-12-23
Searched the forum but so far I have not come across anything that seemed similar to my case.

Im using Dapper, I have Automatix2 installed, and I installed various players and various codecs. I remember being able to view wmv files some weeks ago.

However a day or two ago I tried to view a wmv file and I get the following message in Totem:

> Video codec 'MS WMV 9 (win32)' is not handled. You might need to install additional plugins to be able to play some types of movies

In gxine: 

> Error loading library:

wmvdmod.dll

In VLC it plays audio only

The point it is, it worked before and now it doesn't. I don't consider installing yet another application to be a 'solution', anyone know how I could get the already installed applications to work again?

Thanks a lot in advance.

---

### Post by kd7swh on 2006-12-23
what version of VLC are you running? 0.8.6 has full wmv 9 support.

---

### Post by PartisanEntity on 2006-12-23
0.8.4

what version does automatix install, or can i get it from the repository?

---

### Post by kd7swh on 2006-12-23
it should be in the repos. I installed it. 

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by PartisanEntity on 2006-12-24
For Dapper only 0.8.4 is in the repos as far as I can tell. Now if I download a linux version of vlc from the videolan.org site and install, will be installed without integrating into Dapper? And if yes what does that exactly mean? (For example that it wont update automatically?)

hmm just checked the videolan.org site, as far as dapper is concerned you can't actually download vlc from their site, it merely explains how to download vlc through the repos.

---

### Post by MkfIbK7a on 2006-12-24
did you upgrade from breezy lately if so try to upgrade totem if not 
<apt-get install mplayer>
mplayer has the codecs to play wmvs i beleive i think i used it yesterday:D

---

### Post by PriceChild on 2006-12-24
Please read [uwiki]RestrictedFormats[/uwiki]and install things properly instead of using automatix.

---

### Post by PartisanEntity on 2006-12-27
@PriceChild: Thank you for the advice, I bought a new hard disk for my notebook and reinstalled Dapper, and this time I followed the wiki you linked to and all is working, wmv included.

---

### Post by GaryAndersonMissed on 2006-12-30
Thank you for the direction to the restricted formats wiki.

---

