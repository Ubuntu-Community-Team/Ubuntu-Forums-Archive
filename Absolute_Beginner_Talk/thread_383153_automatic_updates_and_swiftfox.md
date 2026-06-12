---
title: "automatic updates and swiftfox"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by pesach on 2007-03-12
When ever I try to install the automatic updates, this comes up:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Intrestingly enough, this satrted happeneing righ tafter I installed swiftfox and its plu-ins via automatix2.  Swiftfox has seemed to have installed, but the plug -ins wewr not able to.  The terminalt would gibve an error message everytime auytomatix tried to.  The messaeg came and went to fats for me to get a good look on what it said.  And no matter how many times I click on the swift fox icon, nothing comes up.
So I have three problem:
1) No updates
2) No swiftfox
3) No swiftfox plugins
All help would be appreciated

---

### Post by pesach on 2007-03-12
hmmm. I put in
```
 dpkg --configure -a
```
and I got
```
dpkg: requested operation requires superuser privilege
```
I am the only user.

---

### Post by C-A on 2007-03-12
> **pesach said:**
> hmmm. I put in
```
 dpkg --configure -a
```
and I got
```
dpkg: requested operation requires superuser privilege
```
I am the only user.

You could try:

> sudo dpkg --configure -a

---

### Post by pesach on 2007-03-12
well, now updates work, bot swiftfox and swiftfox plug-ins dont.  
Actually, when I click on swiftfox, firefox comes up instead...
its kind of strange.

---

### Post by pesach on 2007-03-14
swiftfox still does not coem up, firefox comes up instead.

---

### Post by halitech on 2007-03-14
swiftfox is basically firefox but optimized for speed for AMD processors. I'm not sure if you would actually see any difference or not...

edit: just reread the page and it is optimized for both but you have to download the correct version. My mistake :(

---

### Post by pesach on 2007-03-14
teh only reason I like swiftfox was before, with 6.06, no plug-ins seemed to work on firefox, so I downloaded swiftfox and plug-ins.  Then, somehow, all graphics, games, and movies worked.
If you have a good way of installing working firefox plugins, im all ears

---

