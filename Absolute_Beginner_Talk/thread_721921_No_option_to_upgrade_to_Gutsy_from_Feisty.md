---
title: "No option to upgrade to Gutsy from Feisty"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by silverace99 on 2008-03-11
Hi got a bit of a problem....I wanted to upgrade from feisty to gutsy. I remembered seeing such an option in the update manager but now it's gone! Anybody run into this problem?

---

### Post by Oldsoldier2003 on 2008-03-11
> **silverace99 said:**
> Hi got a bit of a problem....I wanted to upgrade from feisty to gutsy. I remembered seeing such an option in the update manager but now it's gone! Anybody run into this problem?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by silverace99 on 2008-03-11
gave that a try. All i got was this: 
> Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by glennric on 2008-03-11
See [Gutsy Upgrades]("https://help.ubuntu.com/community/GutsyUpgrades") to learn how to upgrade to Gutsy.

---

### Post by Oldsoldier2003 on 2008-03-11
> **silverace99 said:**
> gave that a try. All i got was this:

if that didn't workout this should work

```
gksu update-manager -c 
```
or```
 
gksu update-manage  --dist-upgrade
```

---

### Post by silverace99 on 2008-03-11
Well see that's the problem. There SHOULD be a notification in the update manager to upgrade to gutsy (and there WAS, i remember seeing it before)........but now it's gone.

edit: Ok i did the gksudo thing and it worked! Thanks! I wonder what caused it to disappear in the first place though...

---

### Post by glennric on 2008-03-11
By the way you may need to click "Check" for the dist-upgrade option to appear.  An alternative method that is not on the link I gave, as it is not recommended, is to edit the file /etc/apt/sources.list and change all occurrences of feisty to gutsy.  You should probably also disable any third party repositories you have enabled.  Then run
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Oldsoldier2003 on 2008-03-11
> **glennric said:**
> By the way you may need to click "Check" for the dist-upgrade option to appear.  An alternative method that is not on the link I gave, as it is not recommended, is to edit the file /etc/apt/sources.list and change all occurrences of feisty to gutsy.  You should probably also disable any third party repositories you have enabled.  Then run
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Yes if that doesn't work i would probably just burn the alt installer for gutsy and upgrade that way, rather than edit the sources.list

---

