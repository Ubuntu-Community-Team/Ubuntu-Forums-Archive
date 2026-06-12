---
title: "Anyone else having trouble getting pangomm ?"
date: 2008-12-26
forum: Arch and derivatives
---

### Post by handy on 2008-12-26
Anyone else having trouble accessing pangomm ?

I have been timing out on multiple mirrors for over two days as of this writing.

---

### Post by smartboyathome on 2008-12-26
Have you updated pacman before updating everything else? I had the same problem, and had to update pacman only first, then when the new mirrorlist was pulled in, I set my repo in it and it worked.

---

### Post by handy on 2008-12-26
> **smartboyathome said:**
> Have you updated pacman before updating everything else? I had the same problem, and had to update pacman only first, then when the new mirrorlist was pulled in, I set my repo in it and it worked.

Pacman is up to date.

I have included extra mirrors, even put the slow Arch mirror in the list in last place.

I'm having another go atmo, it looks funny, saying download size 18Mb install size 530Mb, it looks like great compression, though in reality I just have all these packages downloaded that are ready to install but fail at each attempt due to pangomm having a problem.

At least my machine is (apart from this minor problem) running perfectly.

The cursed pangomm is currently going through the list of servers & timing out on each one of them.

***[Edit:]** I just posted the question in the Arch forum, so sooner or later the simple solution will arrive I'm sure.*

---

### Post by smartboyathome on 2008-12-26
Does it even time out on Arch's main site? If so, I think you should contact the maintainers and see if they know whats going on, it could have been a problem that spread to all the mirrors via rsync.

---

### Post by handy on 2008-12-26
> **smartboyathome said:**
> Does it even time out on Arch's main site? If so, I think you should contact the maintainers and see if they know whats going on, it could have been a problem that spread to all the mirrors via rsync.

When I searched the Arch forums there wasn't any other posts relating to pangomm ?

I would have thought that after some days of my experiencing this problem, that if it was global there would have been a flood of queries.

Anyway, I'll give it some time on the Arch forum & then take it where it needs to go after that.

---

### Post by smartboyathome on 2008-12-26
> **handy said:**
> When I searched the Arch forums there wasn't any other posts relating to pangomm ?

I would have thought that after some days of my experiencing this problem, that if it was global there would have been a flood of queries.

Anyway, I'll give it some time on the Arch forum & then take it where it needs to go after that.

No, I meant does it happen on the repo hosted on Arch's site. It is throttled to 30KB/s, but its better than nothing if it works here.

---

### Post by handy on 2008-12-26
> **smartboyathome said:**
> No, I meant does it happen on the repo hosted on Arch's site. It is throttled to 30KB/s, but its better than nothing if it works here.

Yes, I mentioned that in post_3.

---

### Post by handy on 2008-12-27
I'm having no luck in the Arch forum or here, which is a bit of a pain.  I have nearly 600Mb of files downloaded that fail to install because pangomm can't be downloaded.

---

### Post by smartboyathome on 2008-12-28
> **handy said:**
> I'm having no luck in the Arch forum or here, which is a bit of a pain.  I have nearly 600Mb of files downloaded that fail to install because pangomm can't be downloaded.

Handy, I am attaching my copy here. Perhaps you can download that and it will work for you. :)

---

### Post by handy on 2008-12-28
> **smartboyathome said:**
> Handy, I am attaching my copy here. Perhaps you can download that and it will work for you. :)

Thanks man, I'll give it a go & see what happens. :-D

[I]**[Edit:]** Bugger! I just noticed, I'm using 64bit Arch.
Thanks so much for going to the trouble anyway smartboyathome.[/I]

---

### Post by smartboyathome on 2008-12-28
I replaced the file in my last post with the 64 bit version. Happy to help. :KS

---

### Post by handy on 2008-12-28
> **smartboyathome said:**
> I replaced the file in my last post with the 64 bit version. Happy to help. :KS

You are a champion, thanks, I'll give it a go now.

---

### Post by handy on 2008-12-28
Thank you so much smartboyathome, the file you attached did the job.  

The process led me down a short path of meeting dependencies before I could actually install that pangomm file, but it installed perfectly :-) which then allowed me to at last complete the -Syu --aur I started about a week ago. :D

I am still mystified as to why that particular file could not be downloaded from any of the 13 servers including the official (slow) Arch one, onto my machine?

I'll update my thread on the Arch forums, which last post earlier today was full of my questions on the subject. :-)

---

