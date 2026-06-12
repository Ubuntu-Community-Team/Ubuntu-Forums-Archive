---
title: "Install new version of ubuntu?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Shane_linuxnewb on 2007-04-19
HI, Im on dapper drake and i was wondering how i can install fiesty fawn. can i do it in ubuntu or must i burn it as an image ect. and if the latter option how on ubuntu.

THanks
SHane:guitar: :guitar: :guitar: :guitar: :guitar: :guitar: :guitar: :guitar:

---

### Post by dpar on 2007-04-19
It's not really recommended.........[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Edit: Crap, wrong post.....sorry.:lolflag: Anyway, if you want to do an upgrade, you should probably do it from Edgy. Or get the ISO......download it as a torrent, it will be faster.

---

### Post by tbg58 on 2007-04-19
Since the direct route from Dapper to Feisty is not recommended, you may want to refer to the same page linked above then do one upgrade from Dapper to Edgy, then after your Edgy upgrade is complete, go from Edgy to Feisty.
I don't really like the sound of this, however, because there are many possibilities for problems.

Here's what I'd do -- back up any data you want to keep on another PC, USB drive, burned CDs or DVDs or whatever means you use to back up.
Download the Feisty ISO and burn it.

Then go ahead and do the Dapper to Edgy upgrade, and update.
Then do the Edgy to Feisty upgrade, and update.

Along the way have a second PC with a browser up so you can Google and use these forums to address any problems that come up.

After you've gone through both upgrades, you will have learned a lot.
Then you can boot using the Feisty CD, repartition the whole hard drive and install Feisty cleanly.  You will have the experience and knowledge you got on the double upgrade path, and this should be helpful for you. When you're done you can restore your backed up data.

And if things go sour along the way, you can always abort the upgrade and skip ahead to the CD boot.

That's what I'd do if I had the time.  Of course, if you have a wife and kids, you may just want to back up your data, install Feisty from CD and be done with it.  You might not learn as much along the way, but it will take loads less time, and your family will have more of you.
Speaking of family, I have to put my kids to bed.
Off to do Daddy stuff.
Hope this helps!  Good luck!
Rob

---

### Post by MikeBgts on 2007-04-19
This link might help: [https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

---

### Post by jjasonj on 2007-04-20
hey guys i just went fron dapper to edgy then edgy to fiesty with no probs at all!! and things like my nvidia drivers work even better^^:guitar:

---

### Post by Pobega on 2007-04-20
Run these commands and hope that everything works; Have a Feisty install CD ready just in case something gets messed up.

```
sed -i "s/dapper/edgy/g" /etc/apt/sources.list
apt-get update && apt-get dist-upgrade
REBOOT COMPUTER HERE
sed -i "s/edgy/feisty/g" /etc/apt/sources.list
apt-get update && apt-get dist-upgrade
```

If all goes well you'll be in a Feisty system with little to no trouble at all. But like I said, keep a Feisty CD ready just in case something does fail, dist-upgrade seems to be breaking a lot of systems with the Edgy => Feisty upgrade.

---

