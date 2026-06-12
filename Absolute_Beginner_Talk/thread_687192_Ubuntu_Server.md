---
title: "Ubuntu Server"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by SIlvio77 on 2008-02-04
Hi,

I'm currently running Feisty, and would like to update Ubuntu Server 7.10. Does anyone the repository so that I can update without having to reinstall the all thing. Or maybe there is another way

Thanx

---

### Post by Rocket2DMn on 2008-02-04
I think this is what you're looking for: [https://help.ubuntu.com/community/GutsyUpgrades#head-f2435a45758bb5836f8e5b87e90045463f8c6ec7](https://help.ubuntu.com/community/GutsyUpgrades#head-f2435a45758bb5836f8e5b87e90045463f8c6ec7)
This is assuming your Feisty is also the server edition.

---

### Post by jordanmthomas on 2008-02-04
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup # in case something goes wrong
sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update 
sudo apt-get dist-upgrade
```

If you have a bunch of third-party repos you may want to disable them in case they don't have gutsy repos.


EDIT
use the post above's method.  It seems nicer and cleaner.

---

### Post by Rocket2DMn on 2008-02-04
> **jordanmthomas said:**
> ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup # in case something goes wrong
sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update 
sudo apt-get dist-upgrade
```

If you have a bunch of third-party repos you may want to disable them in case they don't have gutsy repos.


EDIT
use the post above's method.  It seems nicer and cleaner.

That method is actually NOT recommended and has caused breakage on a lot of people's systems.  Just changing the sources.list file is not the way to upgrade, that's why there are built in methods :)
It seems like it should work, but unfortunately it doesn't :(

---

### Post by jordanmthomas on 2008-02-04
> **Rocket2DMn said:**
> That method is actually NOT recommended and has caused breakage on a lot of people's systems.  Just changing the sources.list file is not the way to upgrade, that's why there are built in methods :)
It seems like it should work, but unfortunately it doesn't :(

Thanks, note taken.  I probably should have set this question out since it's Ubuntu-specific and I haven't used Ubuntu in quite some time.

My apologies to OP by the way.

---

