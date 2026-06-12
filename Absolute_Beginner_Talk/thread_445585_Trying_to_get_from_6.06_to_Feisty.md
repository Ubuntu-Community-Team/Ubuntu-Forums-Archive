---
title: "Trying to get from 6.06 to Feisty"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by slickhare on 2007-05-16
So after my attempts at making a Xubuntu Feisty Live CD failed and I reverted back to my Ubuntu 6.06 disc. i've heard that you can upgrade your buntu without making a whole new install. i tried "gksu update-manager -c" but it doesn't recognize the "-c". Is there even a way to get from Dapper to Edgy to Feisty?

---

### Post by Kobalt on 2007-05-16
Yes there is : [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by SomethingCronic on 2007-05-16
In my experience I've always had some problems when upgrading. Upgrading from dapper to edgy to feisty wouldn't be worth it for me personally. I would just do a clean install.

You should do a backup of you data anyway because the upgrade can go wrong, so you might as well do a clean install as you'll be backing up your data. :)

As their is no direct path from dapper to feisty, you would need to update your /etc/apt/sources.list and replace all mention of dapper with edgy - then run apt-get dist-upgrade. Once complete edit sources.list again and replace edgy with feisty. Run dist-upgrade again.

Again, I personally wouldn't recommend it (although I'm sure many here have had no problems with 2 version upgrades). give it a try. Worst case is reinstalling it anyway. :)

---

### Post by slickhare on 2007-05-16
actually i think the question i mean to ask is: since this is 6.06 LTS, is there any advantage in switching to feisty? the ubuntu counter website suggests that a substantial amount still use it interestingly enough.

---

### Post by mahy on 2007-05-16
It depends on whether or not you need some new features. I general, you don't need it.

---

### Post by zvacet on 2007-05-16
Cheking for errors and burning are out of question (you did it right).If you want to try Feisty download alternate CD.For upgrading.Are your Dapper up-to-date,because if it is not you can do upgrade.Command you used is official command for upgrade,so I belive it works.

```
sudo apttude update
```

and after that 

```
gksu "update-manager -c" 
```

---

### Post by slickhare on 2007-05-16
> **zvacet said:**
> Cheking for errors and burning are out of question (you did it right).If you want to try Feisty download alternate CD.For upgrading.Are your Dapper up-to-date,because if it is not you can do upgrade.Command you used is official command for upgrade,so I belive it works.

```
sudo apttude update
```

and after that 

```
gksu "update-manager -c" 
```

I tried "sudo aptitude update" and then tried the gksu command again, but it still doesn't recognize -c.

---

### Post by Zero Prime on 2007-05-16
This may be the long way around, but if the Feisty live CD isn't working for you then you could try using an Edgy live CD.  Download all the updates and then install Feisty from the update manager.

---

