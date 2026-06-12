---
title: "Upgrade from 7.04 to 7.10"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by D|F on 2008-04-20
Hello,
I was installed Ubuntu 7.04 in my desktop, and i want to upgrade from 7.04 to 7.10. 
My question is how can i upgrade it?
Is it possible if i upgrade with 7.10 installation CD?
Or there is other way to upgrade from 7.04 to 7.10?
There anyone can help me?

---

### Post by skymera on 2008-04-20
You can upgrade through a CD

or go to the terminal and type

```
 update-manager -d 
```

that will offer to upgrade to 7.10

---

### Post by Oldsoldier2003 on 2008-04-20
> **D|F said:**
> Hello,
I was installed Ubuntu 7.04 in my desktop, and i want to upgrade from 7.04 to 7.10. 
My question is how can i upgrade it?
Is it possible if i upgrade with 7.10 installation CD?
Or there is other way to upgrade from 7.04 to 7.10?
There anyone can help me?

yes you can upgrade from the 7.10 installation cd.

you can also upgrade by doing this
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

or see [here]("http://www.ubuntu.com/getubuntu/upgrading") for Gui instructions

---

### Post by bschleusner on 2008-04-20
```
sudo apt-get dist-upgrade
```
This should upgrade it to the next version of Ubuntu, but I am not sure if it will upgrade to 7.10, or upgrade straight to 8.04

---

### Post by Oldsoldier2003 on 2008-04-20
> **bschleusner said:**
> ```
sudo apt-get dist-upgrade
```
This should upgrade it to the next version of Ubuntu, but I am not sure if it will upgrade to 7.10, or upgrade straight to 8.04

 7.04s upgrade path is to 7.10,  you would need to upgrade again to get 8.04

Dapper users have a direct upgrade path since LTS->LTS upgrades are supported. Not sure if its live now or will only be live on the release version of Hardy, since i long ago switched from dapper...

---

### Post by D|F on 2008-04-20
Thanks for the help guys, but there is 3 ways.
Which one i have to use?

I'll try to upgrade. Thanks

---

### Post by Oldsoldier2003 on 2008-04-20
> **D|F said:**
> Thanks for the help guys, but there is 3 ways.
Which one i have to use?

I'll try to upgrade. Thanks
they should all work, but the way i showed you is the officially supported method.

---

### Post by Smudger on 2008-04-20
I upgraded from 7.4 to 7.10 earlier.

I went like this:  system/administration/update manager

It worked fine for me, no problems at all.

---

