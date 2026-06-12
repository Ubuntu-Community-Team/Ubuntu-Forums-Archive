---
title: "Problem upgrading to Fawn"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by weaver4 on 2007-04-21
I am using 6.06 and wanted to upgrade to 7.04  Downloaded the Iso, burned the CD.  And then ran gksu "sh /cdrom/cdromupgrade" and it says the file does not exist.  So I look on the CD and sure enough no file called cdromupgrade exist, what gives?

---

### Post by DougieFresh4U on 2007-04-21
I am no expert but let me ask, if you wanted to upgrade why are you bothering with cd? Why not upgrade to Edgy then to Feisty. They say it's not recommended to jump/upgrade between releases. Just asking:confused:

---

### Post by weaver4 on 2007-04-21
I did not relize that, I will upgrade to 6.10 first.  But it does not explain why the cdromupgrde file is not on my cd.

---

### Post by Patrick K on 2007-04-21
For an upgrade you cannot skip releases. You can only upgrade from Edgy to Feisty. You can, of course, do a fresh install. 

cdromupgrade is only on the Alternate CD.

---

### Post by DougieFresh4U on 2007-04-21
> **weaver4 said:**
> I did not relize that, I will upgrade to 6.10 first.  But it does not explain why the cdromupgrde file is not on my cd.

Sorry, I am not familiar with how cd; work. But I see some one has posted that only Alt cd has the option you were looking for. . I prefer the upgrade method through the terminal, this way I feel more control over what is happenig

---

### Post by Pobega on 2007-04-21
```
sed -i "s/dapper/edgy/g" /etc/apt/sources.list
aptitude update && aptitude dist-upgrade
sed -i "s/edgy/feisty/g" /etc/apt/sources.list
aptitude update && aptitude dist-upgrade
```

I'm not promising that everything will run 100%, but it should be fine. dist-upgrade is basically the same as upgrade, except it handles library updates and dependencies much better than update does.

---

