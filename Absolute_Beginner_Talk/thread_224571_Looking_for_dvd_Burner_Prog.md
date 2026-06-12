---
title: "Looking for dvd Burner Prog"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-07-28
Just got Ubuntu Dapper 6.06 up and running and am online on Dial Up (Ripper) ,looking to locate :D good program to burn/backup the system to a blank dvd. Can someone please assist with some advice for a suitable prog. Tried GnomeBurner but it bombs out tring to load the DEV folder in and appears to have a load limit of 200Megs

---

### Post by AndyCooll on 2006-07-28
Your next alternative might be to try K3b

:cool:

---

### Post by bojzi on 2006-07-28
I do it like this...

There's a great tutorial on backing up a whole partition on this page -> [http://psychocats.net/ubuntu/partimage.html](http://psychocats.net/ubuntu/partimage.html) written by aysiu from these forums.
Using that tutorial you can break the backup in little parts (if your partition is larger than a DVD).
After that you can burn it with whatever you want (Bonfire seems like a damn fine app), I'm using NeroLINUX because I have a license from Windows and something ain't working with DVD burning in Dapper for me.

---

### Post by MrHorus on 2006-07-28
k3d, gnome-toast, xcdroast... take your pick :)

---

### Post by abowman on 2006-07-28
I use partimage to back up my data and then k3b to burn it to dvd.

---

### Post by Gerry Atric on 2006-07-28
> **AndyCooll said:**
> Your next alternative might be to try K3b

:cool:K3B sounds like it might be the go. Do you know if it is compatible with Dapper. Thanks to all for the quick response, brilliant.

---

### Post by OU812 on 2006-07-28
1. To use k3b you would have to install a lot of aditional kde packages, although probably not a full desktop. 
2. I think partimage only works with certain file structures: ext2, ext3, and reiserfs.
3. I've heard some people prefer ghost for linux - any opinions?
4. A good alternative burning app is bashburn. No "extra" dependencies since they are present in a base ubuntu install. You have to install from source, but it's not complicated. Try it
[http://bashburn.sourceforge.net/](http://bashburn.sourceforge.net/)
5. An alternative to partimage and g4l may be Mondo Rescue.
[http://www.mondorescue.org/](http://www.mondorescue.org/)

Note: I haven't tried any of these suggestions (except for bashburn which I like a lot). I am also in the process of looking at my options and seeing which ones work best for me.

john

---

