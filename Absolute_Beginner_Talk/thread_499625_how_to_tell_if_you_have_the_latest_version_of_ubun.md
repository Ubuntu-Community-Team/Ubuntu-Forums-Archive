---
title: "how to tell if you have the latest version of ubuntu"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by tennvolsmb on 2007-07-12
how can i tell if i have the latest version of ubuntu?

---

### Post by KyleBrandt on 2007-07-12
In the commandline:

sudo lsb_release -a

---

### Post by tennvolsmb on 2007-07-12
ok thanks

---

### Post by Hendrixski on 2007-07-12
:-) don't even need the sudo in there

---

### Post by tennvolsmb on 2007-07-12
ok i have version 6.06.1. How can i upgrade it?

---

### Post by KyleBrandt on 2007-07-12
I guess so :-)  My hands just seem to typo sudo now no matter what I do...installed Bastille

---

### Post by tennvolsmb on 2007-07-12
so how do i update?

---

### Post by KyleBrandt on 2007-07-12
What version do you have?  Do you want to get the version you have up to date, or update to a different version?

---

### Post by Seisen on 2007-07-12
[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html]("http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html")

---

### Post by Hendrixski on 2007-07-12
if you want to update to feisty just go Synaptic Package manager ... it's under System-->administrator-->synaptic

and synaptic should tell you that there are updates available.  it's as easy as pie.

---

### Post by djchandler on 2007-07-12
> **tennvolsmb said:**
> so how do i update?

You can't skip versions to get to the current stable release, Feisty Fawn, 7.04.
Upgrade to Edgy, 6.10 first, then you can get Feisty. 

Hit the key combination "alt-F2", and enter

gksu "update-manager -c"

which will allow the next version upgrade to Edgy.
Once you have Edgy installed, do the same thing to update to Feisty.

DJ

---

### Post by djchandler on 2007-07-12
As far as I know, there is no Ubuntu full version upgrade via Synaptic. Use the solution above. I had not seen the post prior to mine when I posted, and we contradict each other.

Where's the guy with the most beans to set op straight?

DJ

---

### Post by testube_babies on 2007-07-12
> **djchandler said:**
> As far as I know, there is no Ubuntu full version upgrade via Synaptic. Use the solution above. I had not seen the post prior to mine when I posted, and we contradict each other.

Where's the guy with the most beans to set op straight?

DJ

Beans don't mean anything....your method is right.

Although I would advocate just downloading the new version and doing a fresh install, I've run into a few snags during upgrades.

---

### Post by djchandler on 2007-07-12
> **testube_babies said:**
> Beans don't mean anything....your method is right.

I guess I don't know beans, but it's nice to be validated.

Thanks,
DJ

---

### Post by Seisen on 2007-07-12
Actually there are about a few ways to upgrade some are recommended and some are not. Your solution is one way to upgrade.

---

### Post by user1397 on 2007-07-12
Here's the official ubuntu page on upgrading: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

I, however, recommend doing a fresh install of feisty, but remember to backup any important files you may have.

It is safer to upgrade if automatix is **not** installed.  There have been cases where automatix has broken an upgrade.

**lsb_release -a** shows you what version of ubuntu you are running, while **uname -a** shows you other things, such as your computer name and kernel version.

---

