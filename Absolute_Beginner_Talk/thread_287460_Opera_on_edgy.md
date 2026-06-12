---
title: "Opera on edgy?"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Dual Cortex on 2006-10-28
I'm on Kubuntu, and I don't seem to find Opera on the repos.
I could download the deb package and install it but I wonder if it is compatible with edgy AND there are no problems with it.

---

### Post by TheRingmaster on 2006-10-28
opera is in the commercial repository. you should find Opera in the "add and remove programs" program. It will ask you to enable the commercial respositry and you can install it from there.
 
please don't mind my spellings.
 
ps. there should not be a problem running that program on edgy.

---

### Post by veli on 2006-10-28
Opera does work on Edgy. Install the .deb file, you might get an error at the end, ignore it. I'm using Opera now, because of the FF crash issue.

---

### Post by Oki on 2006-10-28
You can install latest Opera if you download Automatic2.

---

### Post by Dual Cortex on 2006-10-28
I usually try to avoid automatix... if I had known of automatix and used it before, I probably would know a fourth of what I do know...
Well... anyway, good to see OPera works on Edgy, for some reason I just don't feel comfortable on FF. I prefer IE7 over firefox... but after trying out Opera, I simply love it.

---

### Post by Dual Cortex on 2006-10-28
> **TheRingmaster said:**
> opera is in the commercial repository. you should find Opera in the "add and remove programs" program. It will ask you to enable the commercial respositry and you can install it from there.
 
please don't mind my spellings.
 
ps. there should not be a problem running that program on edgy.

lol... wow... :rolleyes: :mrgreen:  I just noticed the ADD/REMOVE programs. I was using 'Adept Manager Manage Package" before (to install FF, etc.).
I was wondering why it didn't look as friendly as the ADD/REMOVE Programs function on gnome ;) !

---

### Post by Asham on 2006-10-28
I couldn't find Opera on my Edgy installation so I added a repository to Synaptic found on the Opera forums: 
```
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free
```
More info here: [http://my.opera.com/community/forums/topic.dml?id=156741](http://my.opera.com/community/forums/topic.dml?id=156741)


This may not be the best way but since I couldn't find it there wasn't much else to do.

---

### Post by Dual Cortex on 2006-10-28
Yeah it isn't in the 'original' repos.
I'm just going to install the deb package though.

---

### Post by Aranel on 2006-10-28
Yeah, it's in the Canonical Commercial repository, along with RealPlayer and some antivirus client. You can add it by putting the following line in your /etc/apt/sources.list file:

```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Yes, that says "dapper." I wasted two hours of my life this morning trying to figure out why the heck Edgy's version wasn't working there - turns out the Packages.gz for Edgy is blank. I suspect the reason for this may have something to do with the fact that no version of Opera for Edgy is out on opera.com yet (although naturally the Dapper version works just fine). I've added the Packages.gz file to my bookmarks to see when it will finally be updated, so until then, I'm just gonna go with the Dapper version.

---

### Post by Dual Cortex on 2006-10-28
Ok, so I learned much in the past 3 weeks... but I'm fairly new to **K__**ubuntu and Ark doesn't have the big Install button as gnome "de-packager" does. Is ther a GUI tool do dpkg deb files (if it doesn't come pre-installed on KDE, I prefer to just use the dpgk command)?

---

