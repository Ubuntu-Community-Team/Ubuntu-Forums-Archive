---
title: "Startup Problem"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by tad13 on 2008-03-05
Hey 
I ran Wubi instal on my windows XP Professional pc and installed Linux ´Ubuntu properly.
But:
When i restart my pc and choose the ubuntu software it loads Linux but i get a black screen .

I tried everything to start ubuntu but it won't start how can i fix this?:(:confused::(

---

### Post by explicitly ambiguous on 2008-03-05
It may be that your display is not loading correctly...?

Next time you log in, maybe you could try
```
Ctrl-Alt F1
```
this will open up a terminal window from which you can login to your system and run commands.

```
Ctrl-Alt F7
```
Should get you back to the black screen if you want ;-)

If this works enter the commands 
```
dmesg
```
(will show system error messages)
```
lspci
```
(will list what pci hardware you system can see)
and post back the results.

Andy

---

