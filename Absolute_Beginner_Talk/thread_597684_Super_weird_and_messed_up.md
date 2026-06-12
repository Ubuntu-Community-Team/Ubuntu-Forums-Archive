---
title: "Super weird and messed up"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by infamous16 on 2007-10-30
ever since I just started up ubuntu everything is messed up. The desktop effects dont work, I had to start in low graphic mode, the screen resolution is off, everything!

And whenever I try to do something about it in terminal it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

how do i fix that? I dont even remember how to get the run command thing up!

I didnt even do anything the last time I shutdown to it, I just shut it down not restart because I wanted to get some file or program to work.

Thanks!

---

### Post by Crafty Kisses on 2007-10-30
You might want to enter the following command in the Terminal:
```
dpkg --configure -a
```
To get to your Terminal do the following, **Applications>Accessories>Terminal**.
Hope this helps. :)

---

### Post by OldTimeTech on 2007-10-30
Applications ->Accesseries->Terminal

type in terminal: dpkg --configure -a

It will give you more commands if this doesn't work

Keep asking questions as needed ;)

---

### Post by infamous16 on 2007-10-30
Ha, I'm not that new of a user...And I have already tried that and this comes up

dpkg: requested operation requires superuser privilege

but thanks for the advice so fast.

I may just reinstall or something...unless I can get this to work out now.

---

### Post by rudeboyskunk on 2007-10-30
As for your graphics problem, can you post specifications on your computer, especially in regards to your graphics card?  It might not be supported for Compiz.

---

### Post by Crafty Kisses on 2007-10-30
> **infamous16 said:**
> Ha, I'm not that new of a user...And I have already tried that and this comes up

dpkg: requested operation requires superuser privilege

but thanks for the advice so fast.

I may just reinstall or something...unless I can get this to work out now.

Before you type the command, type the following in the Terminal:
```
sudo -i
```
Then try the "dpkg" command again.

---

### Post by infamous16 on 2007-10-30
Well, it has worked for compiz for about a week, and thanks for the other thing, it seems to be working...but im not sure.

system specs
radeon 9600 pro
1gb ram
300gb seagate barracuda
a old hp crt monitor
amd 3200+

---

### Post by Crafty Kisses on 2007-10-30
> **infamous16 said:**
> Well, it has worked for compiz for about a week, and thanks for the other thing, it seems to be working...but im not sure.

system specs
radeon 9600 pro
1gb ram
300gb seagate barracuda
a old hp crt monitor
amd 3200+

No problem man.

---

### Post by rudeboyskunk on 2007-10-30
> **infamous16 said:**
> Well, it has worked for compiz for about a week, and thanks for the other thing, it seems to be working...but im not sure.

system specs
radeon 9600 pro
1gb ram
300gb seagate barracuda
a old hp crt monitor
amd 3200+

Ha, yeah, somehow I think you should have no problem running Compiz.

---

### Post by infamous16 on 2007-10-30
well, now its working again....except compiz wont let met enable it! lol

it says desktop effects could not be enabled...and they have worked before.

anything that could help this out? Maybe I'll try to restart with the ati drivers enabled, but that usually made compiz NOT work before.

---

