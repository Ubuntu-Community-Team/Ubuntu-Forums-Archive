---
title: "KDE 4 woes"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by Foxblood on 2008-01-14
HI,

I installed KDE 4 easily enough and I really want to like it but it's starting to drive me crazy. I started my pc and I've got no taskbar, And I can't figure out how to get it back. Compiz won't run. My memory usage is off the charts and Superkaramba barely works, continually advising me to install Kross or something similar. Worst of all, if I try to start any program that requires administrative priveleges my password is rejected. I can run Synaptic via the terminal, so there's hope. If I can get assistance.
So, please, I need help. Thanks in advance.

---

### Post by sports fan Matt on 2008-01-14
I couldnt even get it started, I had to reformat..However it seems like (at least to me it was prematurely released which is why i may hold off till 4.1 ..I dont really want to reformat again...

---

### Post by sumguy231 on 2008-01-14
How did you install it? WIth the packages listed on kubuntu.org?

---

### Post by Foxblood on 2008-01-14
> **sumguy231 said:**
> How did you install it? WIth the packages listed on kubuntu.org?

Yeah, I used Synaptic.

---

### Post by SunnyRabbiera on 2008-01-14
KDE4 is still young, really use something established until kde4 gets more pullin.
really there is nothing kde4 cant offer that you can do with kde3 with compiz

---

### Post by tgalati4 on 2008-01-14
Well since you set your machine up as dual-boot, then you can just go back to your old distro.

You did set it up as dual-boot didn't you? 

KDE4 has been under development for the past 2 years, but it's still bleeding edge.

And bleeding. . .

---

### Post by sumguy231 on 2008-01-14
By the way, the KDE4 packages in the regular repositories are kinda broken and not for the final version of KDE 4.0.0 (they're like 3.94 alpha or something). Working (to the extent that KDE4 "works") packages are here:
[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

---

### Post by Foxblood on 2008-01-15
> **sumguy231 said:**
> By the way, the KDE4 packages in the regular repositories are kinda broken and not for the final version of KDE 4.0.0 (they're like 3.94 alpha or something). Working (to the extent that KDE4 "works") packages are here:
[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

That's where I got it from. 
I'm going to persevere at this, for a while at least. What's the worst that can happen?

---

### Post by Steveway on 2008-01-15
This command:
```
rm ~/.kde4/share/config/plasma*
```
will give you your Panel back.
This happens here also sometimes, I'm not sure if there is allready a bugfix for this.

So you don't "freak out", oh my god a rm command!!11!, it will delete all files beginning with plasma in that directory.
Afaik since those are removed KDE4 recreates them.

---

### Post by Foxblood on 2008-01-15
> **Steveway said:**
> This command:
```
rm ~/.kde4/share/config/plasma*
```
will give you your Panel back.
This happens here also sometimes, I'm not sure if there is allready a bugfix for this.

So you don't "freak out", oh my god a rm command!!11!, it will delete all files beginning with plasma in that directory.
Afaik since those are removed KDE4 recreates them.

Thanks, Steveway, that's as good as gold.

---

### Post by Steveway on 2008-01-15
Oh, yes. Forgot that one.
It's advised to not do that command while Plasma is running. (It most propably wont work.)
So better go into another enviroment to do that command.

---

### Post by Foxblood on 2008-01-15
^^^^ Not only did that sort out my taskbar, it also brought my memory usage out of the red somehow. Thanks again.

---

### Post by KarateCowboy on 2008-02-05
So where does a man get the kross framework?

---

