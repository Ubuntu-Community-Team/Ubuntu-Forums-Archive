---
title: "latest Ubuntu"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by srtraveler on 2007-04-05
[FONT="Courier New"][SIZE="3"][/SIZE][/FONT]Moving from XP. I just installed Ubuntu from a DVD. I think it is 6x. Is the 7x already out? How do I set my system up so I will be automatically notified of updates? Thanks.

---

### Post by halitech on 2007-04-05
7.04 will be released sometime in April (April 19 from what I've seen) as far as updates, it won't automatically update you to the next version as not everyone wants to update as the releases come out but security and other updates will notify you as they come out with a orange star shaped icon up by your clock.

---

### Post by bobplano on 2007-04-05
your system automatically checks for updates or if you want to check yourself open up update manager or type into a terminal

```
sudo apt-get update
```

fiesty is due to come out sometime this month, and when it does it will show up in the update manager for you to click on

---

### Post by halitech on 2007-04-05
thought the update manager would only do the ssytem updates? thought you had to run a different command to get the system to do a distro update?

---

### Post by bobplano on 2007-04-05
well im not too sure about it because i just installed dapper and havent done any major upgrade to edgy

---

### Post by halitech on 2007-04-05
I think to update you would either have to do a 
```

sudo apt-get dist-upgrade
```

or run

```

gksu "update-manager -c"

```

---

### Post by chalex on 2007-04-05
Ubuntu makes a program called "update-manager" that lets you most easily upgrade to the next release.  Here's a random link from Google: [http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html)

Also, to the OP, the Ubuntu version numbers are actually dates.  6.10 as in 2006-10 and 7.04 as in April 2007.

---

### Post by Maestro23 on 2007-04-05
Feisty Upgrade: [https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

---

