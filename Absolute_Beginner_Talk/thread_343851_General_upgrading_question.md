---
title: "General upgrading question"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by SolaceAvatar on 2007-01-22
I'm pretty sure I have Ubuntu 2.6 ... which is apparently really old. XD I've also heard that the newest version is kinda unstable, so... what do the newer versions do that the old ones don't, and what one do you think I should get? I don't have any files on it right now, so I'm not worried about messing it up... also, how would I go about making it whatever new version I should get?

---

### Post by housam on 2007-01-22
If you have Dapper ,it is a very stable os and has the option of LTS (3 years). Edgy is the new version but with less stability and more features. You can download the Edgy iso and burn it to a blank CD to create a live CD. then you can boot through the CD and figure it out before installing.

---

### Post by Tux Aubrey on 2007-01-22
Two ways (I know of) to find out what version of Ubuntu you are using:

From the "system" menu, select "About Ubuntu" - the document that opens will welcome you to your version of Ubuntu (Dapper Drake was 6.6, Edgy Eft is 6.10)

Second method - open a terminal and type:

```
cat /etc/*release
```

Your version will be displayed on the screen, something like this:

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"


You should only use the automated upgrade to go "up" by one release at a time - so it is OK to upgrade from 6.6 to 6.10, but not directly from 5.10 to 6.10.

Before you consider upgrading, read up on it - including the sticky post at the top of the forum and, if you do decide to go ahead,  read [this guide]("https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrades%29%7C%28edgy%29#head-737da121a6b07c40acb3fb6855f52830e1cfe6db").

Remember that this method only works on a high speed internet connection (not dial up).

You can also do a "fresh install" of edgy (6.10) from a new live CD.

Either way, backup all your important files first.

---

### Post by carverj on 2007-01-22
Am on my 4th or so version of Ubuntu and recommend the current version.
Everything has worked with little fuss.
The appearance is very appealing nowadays to!!
The way I see it is it's best to upgrade every 6 months to a year with a fresh install.
It's definately worth the time and effort and  you become much quicker at using and installing with this aproach.

---

