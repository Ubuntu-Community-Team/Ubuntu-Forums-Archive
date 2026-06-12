---
title: "Where do files deleted as su go?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by ajmoncrief on 2006-01-20
I had a couple of files that I mistakingly deleted while I had a root-nautilus window open.  Of course they didnt go to the ~/.trash folder, but I believe that they still reside on my computer somewhere.  Because the disk space is still being occupied (according to nautilus).  Any idea on how to find these files? (more importantly, how to completely remove them?) TIA

---

### Post by Kimm on 2006-01-20
as root, navigate to /root/.Trash

---

### Post by MartinG on 2006-01-20
I find two possible places on my KDE machine:
/home/.Trash-0 and /root/.local/share/Trash

Why sometimes one and sometimes the other I don't know, and Gnome might be different, but if you make hidden files visible and dig around you should find something.

---

### Post by Jucato on 2006-01-21
Guys I can't thank you enough for these answers! I was almost going crazy trying to find out why I only had 4GB (out of 19GB) space left on my / partition. Seems that some of the files I deleted went to root's trash.

Btw, on Kubuntu, I found it in /root/.local/.share/.Trash

Thanks guys! I owe you big!

(Wee my first post here! :p )

---

### Post by Koobi on 2006-01-21
some people might find it easier to go to location:
```

trash://

```

via nautilus as root and empty trash there

---

### Post by ajmoncrief on 2006-01-27
Thanks for all the posts, I guess I forgot that to subscribe when I posted and was wondering why no one responded back.  I'll go try this now, and if I cant find anything I'll post back.  If not, all's well.  Thanks again.

---

