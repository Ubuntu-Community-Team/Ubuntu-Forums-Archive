---
title: "Upgrading to Edgy"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by John E on 2007-01-25
I'm currently running Dapper. If I decide to upgrade to Edgy, can I simply install it on the same volume as Dapper (i.e. overwriting Dapper) or is it best to scrap my previous installation and start again? Also, assuming that I can "upgrade" (as opposed to a fresh install) will my previous device settings be retained? When I first tried Ubuntu, it was particularly difficult to install my graphics drivers and I'd rather not go there again!!

---

### Post by taurus on 2007-01-25
Here's a guide regarding upgrading from Dapper to Edgy.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

What kind of graphic card do you have on your machine?

---

### Post by ljpm on 2007-01-25
> **taurus said:**
> Here's a guide regarding upgrading from Dapper to Edgy.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)



I have tried repeatedly to use

```
gksu "update-manager -c" 
```

to upgrade and I keep getting a timed out error. Any Idea how to avoid this problem?

---

### Post by John E on 2007-01-25
Thanks - I have a Matrox Millennium G400 dual-head. It was setting up the dual ouput graphics that gave me so much grief.

According to that article, I should upgrade my version of 6.06 before upgrading to 6.10. However, the main reason I want to run 6.10 is that whenever I try to download any upgrade for 6.06, I end up with a non-bootable PC. I'm hoping that an upgrade to 6.10 might cure this. 6.10 seems to boot okay from a live CD.

---

### Post by John E on 2007-01-25
Well I backed up my 6.06 partition (hda6) and decided to try upgrading from my Live CD of 6.10. The upgrade gets to the stage of running QParted which then comes up with a liist of partitions. I selected my existing swap partition (hda5) as 'swap' and I selected hda6 as '/'. I deselected the options to reformat the partitions. When I press the 'Forward' button, a message pops up saying, "No root partition".

Any ideas anyone?

---

