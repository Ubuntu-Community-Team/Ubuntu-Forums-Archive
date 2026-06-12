---
title: "XP/Vista/Ubuntu Boot problem please help!"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Kdawkins on 2008-04-13
Hey,

Well I always tri-booted XP, Vista, and Ubuntu 7.10. Last night I decided I haven't used XP in months and that I wanted to try to KDE desktop and see how I like that against Gnome. To make a long story short, I can boot into Ubuntu but NOT Vista. Apparently the vista boot record was written in the XP boot loader thing so once I deleted XP, my vista booter went with it. :-(   Also, all the OSes are on their own hard-drives so that things are easier for me.

Is there any way to fix this? I have a lot of important stuff on Vista and I really  need to get back in..

I have supergrub but I cant figure out how to make that help me. Also when I try to repair the boot from the Vista CD, it fails. 

Thanks for any help,
Kevin

---

### Post by zvacet on 2008-04-13
Can [this](http://ubuntuforums.org/showthread.php?t=740221&highlight=vista) be of any help to you?

---

### Post by Kdawkins on 2008-04-13
Ok I tried that link:

```

bootrec /fixmbr
bootrec /fixboot

```

The first of the two (/fixmbr) worked just fine. The second one errored out. Some error about an un-recognized file system or something of the sort. Are there any other ways of recovering my Vista boot or should I re-install XP?

--kevin

---

### Post by lswest on 2008-04-13
there's a link in my thread (second line) with a bit of info on it, have a look, might give you an idea of what you could do to fix it...but if bootrec /fixboot errored out...not sure

---

