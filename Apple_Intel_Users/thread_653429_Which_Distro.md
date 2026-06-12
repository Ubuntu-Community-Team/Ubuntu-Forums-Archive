---
title: "Which Distro?"
date: 2007-12-29
forum: Apple Intel Users
---

### Post by RelativelyQuantum on 2007-12-29
Hi all.

I've recently had some trouble trying to run various distributions of Ubuntu on my macbook. I started this thread to get feedback about the experience users have had with other versions, to see weather others have experienced the same problems I have, and how they can be solved.

I'm interested in running Edgy on said macbook (Intel Core 2 Duo) and wondered weather anyone has information as to how I might go about doing that. I've tried to install from live CD, but the entire thing freezes on the x server error page. I haven't gotten past it. Perhaps a textual installer...?

In any case, I would appreciate anything you have to say.

Thanks in advance.

---

### Post by keeper of the wheel on 2007-12-29
I would suggest using the alternate CD (or text version) since it will take less memory to install.
That has been my experience working with various machines... especially those that hang like you described.

---

### Post by RelativelyQuantum on 2007-12-30
That sounds good. Would it allow me to use the standard graphical interface once it's installed?

---

### Post by keeper of the wheel on 2007-12-30
to run programs? Absolutely.
The only distro that I found lacking a graphic interface after installation was Xubuntu, twice.

Hope that helps.

---

### Post by RelativelyQuantum on 2007-12-30
It definitely does! I'll download to new ISO right away. in the meantime, I tried installing Edgy using safe graphics mode on live CD, and that seemed to clear up the freezing problem. I couldn't seem to reconfigure the x server correctly, however. I followed the steps on this link, but to no avail:

[http://ubuntuforums.org/showthread.php?t=448809](http://ubuntuforums.org/showthread.php?t=448809)

Perhaps the settings only work for feisty. Though booting into safe graphics mode was a major improvement nonetheless.

Thanks again :)

---

### Post by cyberdork33 on 2008-01-02
Edgy is outdated. Many fixes specific to Mac have been made since that release. Download a newer release.

---

### Post by RelativelyQuantum on 2008-01-05
Just to wrap things up:

I attempted the alternate CD install, got everything set up, but once again got the x server error message. I then decided to take cyberdork33's suggestion and upgraded to Gutsy, which has out-of-the-box compatibility with at least my screen, if nothing else :). Now it's just a matter of patching the kernel for compatibility with graphics card, sound card, and wireless.

Thanks again to everyone who posted here; your advice was appreciated.

---

### Post by Rog-Mahal on 2008-01-05
Are you sure you need to do patches for sound and graphics cards? My 3rd gen. Macbook had everything except wireless work out of the box with Gutsy.

---

### Post by handy on 2008-01-05
My 24" iMac, took the 64bit alternate install of Ubuntu 7.10 very smoothly, I only had to fiddle to get the sound working, & I expect that problem to be solved in the next release - Ubuntu 8.04.

I had only used Kubuntu 7.10 previously, & I must say that the Ubuntu 7.10 Gnome version is a much more polished production.  Kubuntu had an array of bugs.  Thus far the only thing I'm missing is a way to dim my iMac screen in Ubuntu, (& the sound problem which I expect exists in Kubuntu as well).

---

### Post by RelativelyQuantum on 2008-01-06
> **Rog-Mahal said:**
> Are you sure you need to do patches for sound and graphics cards? My 3rd gen. Macbook had everything except wireless work out of the box with Gutsy.

That's strange. I'm using the amd64 Gutsy ISO, but, as mentioned previously, am having problems with my graphics/sound cards in addition to wireless. Here are my specs:

- OS X Leopard
- Core 3 Duo
- 160 GB HDD, with 32 GB available for Ubuntu
- 2 GB Ram

I can't figure out what's wrong. I've been trying to fix these problems, but nothing I do works. At the moment I'm attempting to get wireless working, by following the procedure I did before, but I'm not optimistic.

---

### Post by RelativelyQuantum on 2008-01-06
> **handy said:**
> My 24" iMac, took the 64bit alternate install of Ubuntu 7.10 very smoothly, I only had to fiddle to get the sound working.

How did you do that? Even sound would be a big improvement for me. I'm starting to feel as though I'm in the twilight zone...

---

### Post by handy on 2008-01-06
> **RelativelyQuantum said:**
> How did you do that? Even sound would be a big improvement for me. I'm starting to feel as though I'm in the twilight zone...

I followed the instructions from [***_this thread_***]("http://ubuntuforums.org/showthread.php?t=598725&highlight=imac+sound") Post 5.

The results aren't perfect but they will do until 8.04 is released, or someone produces a better fix.

---

### Post by cyberdork33 on 2008-01-07
here is a link directly to the post being referred to:
[http://ubuntuforums.org/showpost.php?p=3697702&postcount=5](http://ubuntuforums.org/showpost.php?p=3697702&postcount=5)

I also added this link in the FAQ.

---

