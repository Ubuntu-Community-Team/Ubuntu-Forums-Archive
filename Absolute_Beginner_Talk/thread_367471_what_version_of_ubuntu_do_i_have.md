---
title: "what version of ubuntu do i have"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by hempa on 2007-02-22
Hello! i want to find out what version of ubuntu i have and how to upgrade if it is an old version.

---

### Post by 23meg on 2007-02-22
Type```
lsb_release -a
```in a terminal to find out.

---

### Post by Archmage on 2007-02-22
Start firefox. The Welcome screen should read "Welcome to [your Ubuntu-Version]".

Dapper ist the LTS-Version. It will be supportet till 2010.

Edgy is a little newer, but it might be not that rock-stalbe - although it works great for 99%.

Feisty will come out in April.

---

### Post by hempa on 2007-02-22
thanks! i have ubuntu 6.06 Dapper. how do i upgrade to the latest version?

---

### Post by xpod on 2007-02-22
Personally i would just download the Edgy iso and do a complete fresh install but thats just me:)

---

### Post by hempa on 2007-02-22
> **xpod said:**
> Personally i would just download the Edgy iso and do a complete fresh install but thats just me:)

Thanks. if i do a clean install will all my apps and programs that i have no dissapear!

---

### Post by xyz on 2007-02-22
> **hempa said:**
> Thanks. if i do a clean install will all my apps and programs that i have no dissapear!
Hi,
I have not tried this myself but there is a howTo completely reinstalling while keeping your packages on the French Ubuntu forum. You may be interested in having a look at it. In case of language pbm, I can help.
[the author: "Luckynow"]("http://forum.ubuntu-fr.org/viewtopic.php?id=64855")

---

### Post by xpod on 2007-02-22
They will if you just do a fresh install from cd but you can upgrade whilst keeping all your stuff although again i`ve never done so myself,Mabey this might help you

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by bob-aptllc on 2007-02-22
Another method of finding your version is to click System/About Ubuntu. A window will open that, below the chapter links, displays a message similar to the following:

"Thank you for your interest in Ubuntu 6.10 - the Edgy Eft - released in October 2006."

This is useful if you have already changed your browser's home page.

---

### Post by Ben Sprinkle on 2007-02-22
> **hempa said:**
> thanks! i have ubuntu 6.06 Dapper. how do i upgrade to the latest version?

```

sudo apt-get upgrade

```
Expect problems. :)

---

### Post by mk04 on 2007-02-22
```
gksu "update-manager -c"
```

Then it will show you the next available distro version you can upgrade to.

---

### Post by jvc26 on 2007-02-22
You will need to update your sources.list to an edgy sources list before running sudo apt-get upgrade as otherwise it just updates you to the latest packages on dapper, not the whole OS. Its probably better the do a vanilla install as often the upgrades have issues.
Il

---

### Post by Ben Sprinkle on 2007-02-22
> **Illuvator said:**
> You will need to update your sources.list to an edgy sources list before running sudo apt-get upgrade as otherwise it just updates you to the latest packages on dapper, not the whole OS. Its probably better the do a vanilla install as often the upgrades have issues.
Il


Ah right, forgot to mention that.

---

### Post by bob-aptllc on 2007-02-22
I read that if you do a fresh install rather than an upgrade, you can preserve your personal data (but not packages) by placing it in the /home partition.  Of course, to be safe, back it up before installing the new OS.

To retain your packages, see "Create backup of all packages using APTonCD in Ubuntu" at [http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html](http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html).

---

### Post by Ben Sprinkle on 2007-02-22
> **bob-aptllc said:**
> I read that if you do a fresh install rather than an upgrade, you can preserve your personal data (but not packages) by placing it in the /home partition. 

To retain your packages, see "Create backup of all packages using APTonCD in Ubuntu" at [http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html](http://www.debianadmin.com/create-backup-of-all-packages-using-aptoncd-in-ubuntu.html).

Yes you can do this, along with any other drive/partition you buy/make. That's just common sense. ;)

---

