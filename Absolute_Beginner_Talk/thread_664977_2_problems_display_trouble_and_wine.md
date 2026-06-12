---
title: "2 problems: display trouble and wine"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by bighomer on 2008-01-11
Wow there are a lot of people here. 

OK first off...
I posted this problem earlier. I just read the 'zero reply post' post. I don't feel ignored. At least fifteen people took the time to read my post. To these people I am grateful...unfortunately, there's still a problem. Tried googling it, found very little. 
OK...my monitor's only showing most of the desktop screen. Most, but the bottom and right sides are cut off. Ubuntu looks great...maybe better than Fedora Core...but I'm afraid I just won't be able to use it like this. 
What little I learned suggests that there may be a problem with my rather pathetic ATI graphics card (Mobility). Any help would be appreciated as I don't know what to do at this point besides wipe ubuntu from my system and forget about it. 

Second, there's this issue with wine. I double-clicked the package file and a box pops up with details. In red, it says: dependency is not satisfiable: binfmt-support
I haven't googled it yet. I was hoping someone could point me to a good site with up-to-date information addressing issues like this. Any recommendations?

---

### Post by nikoPSK on 2008-01-11
> **bighomer said:**
> Wow there are a lot of people here. 

OK first off...
I posted this problem earlier. I just read the 'zero reply post' post. I don't feel ignored. At least fifteen people took the time to read my post. To these people I am grateful...unfortunately, there's still a problem. Tried googling it, found very little. 
OK...my monitor's only showing most of the desktop screen. Most, but the bottom and right sides are cut off. Ubuntu looks great...maybe better than Fedora Core...but I'm afraid I just won't be able to use it like this. 
What little I learned suggests that there may be a problem with my rather pathetic ATI graphics card (Mobility). Any help would be appreciated as I don't know what to do at this point besides wipe ubuntu from my system and forget about it. 

Second, there's this issue with wine. I double-clicked the package file and a box pops up with details. In red, it says: dependency is not satisfiable: binfmt-support
I haven't googled it yet. I was hoping someone could point me to a good site with up-to-date information addressing issues like this. Any recommendations?

for screen issues run this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

We have responded to your thread, just take time to read. :KS

Best,
nikoPSK

---

### Post by Martin Witte on 2008-01-11
> **bighomer said:**
> OK...my monitor's only showing most of the desktop screen. Most, but the bottom and right sides are cut off.
Can you please post the make and type as detailed as possible of your video card and of your screen?

---

### Post by bighomer on 2008-01-11
Yeah, I just noticed. I can be slow at times. Sorry.

---

### Post by nikoPSK on 2008-01-11
> **bighomer said:**
> Yeah, I just noticed. I can be slow at times. Sorry.

no need to be sorry, perfectly fine.

best,
nikoPSK

---

