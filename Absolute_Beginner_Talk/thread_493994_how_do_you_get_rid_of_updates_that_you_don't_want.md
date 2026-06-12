---
title: "how do you get rid of updates that you don't want"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-07-06
ok, how do i clear my update manager of updates i do not want?

---

### Post by k33bz on 2007-07-06
come on i really could use the help on this one

---

### Post by Lolicon on 2007-07-06
Do you mean you installed it already? What is it?

---

### Post by k33bz on 2007-07-06
no, its not items that are installed, I have two updates waiting to be installed sitting in my Update Manager, that i simple just dont want. there has been a few that came across that i didnt want, but gave in and just installed them. But these two updates i do not want at all. so was wondering if there is a way to clear it from my update manager with out having to install them.

---

### Post by AllenGG on 2007-07-06
Did you try to "uncheck" them and they reappeared ?

---

### Post by k33bz on 2007-07-06
ya i have tried that, if i uncheck them, they just stay there, not reappear, cause they never disappear.

---

### Post by AllenGG on 2007-07-06
Perhaps you should consider removing the Update Manager, and updating, say weekly, using Synaptic. After you check "mark all upgrades", then open "Custom Filters" and it will highlight the upgrades, to existing programs, and that may clear up a mystery. Note how many installed programs are shown.

---

### Post by k33bz on 2007-07-06
> **AllenGG said:**
> Perhaps you should consider removing the Update Manager, and updating, say weekly, using Synaptic. After you check "mark all upgrades", then open "Custom Filters" and it will highlight the upgrades, to existing programs, and that may clear up a mystery. Note how many installed programs are shown.

im still pretty much a noobie, gained alot of intelligence, but alas, not this extent. so:

1st: how do i remove update manager?

2nd: I know there is a command to run in the terminal that tells me how many programs i have installed, but i forgot what that command is.

---

### Post by Eddy Dean on 2007-08-04
Is this seriously the only way of skipping updates?

I want to use the AMD64 Wine, but the update manager wants me to install the i386 binaries (which are indeed more recent).

I am not the only one using the computer, so I don't want to risk installing the package!

---

### Post by nitro_n2o on 2007-08-04
if you want to prevent some package from being updated try this 
```
sudo aptitude hold <package_name>
```
it comes handy when you want to make sure that you are working with the same version of software you want to work with

---

### Post by SirGrant on 2007-08-04
[[IMG]http://img329.imageshack.us/img329/2710/screenshotcf9.th.png[/IMG]](http://img329.imageshack.us/my.php?image=screenshotcf9.png)

See where it says lock version in your package manager.  So for example I was doing that with wine but you can do it with whatever program you want.  Try that I think it should work.

---

