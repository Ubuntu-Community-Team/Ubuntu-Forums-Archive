---
title: "the newest OS?"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Ob1 on 2006-04-07
When a new versoin of Ubuntu is realesed, will i than need to burn the newest version on a CD or will ubuntu update itself?

---

### Post by aysiu on 2006-04-07
Up to this point, to upgrade, you've had to manually change your sources.list and then do a dist-upgrade.

I believe with Dapper, this will be a little less involved, if not automated.

Either way, you do not need to burn the newest version on a CD.

---

### Post by taurus on 2006-04-07
It won't update itself.  You need to open a terminal and manually edit your /etc/apt/sources.list and change every line that has breezy to dapper.  Then, upgrade it to dapper...
```

sudo gedit /etc/apt/sources.list <-- to edit it.  Then run the next two commands to upgrade it...
sudo apt-get update
sudo apt-get dist-ugrade

```

---

### Post by xXx 0wn3d xXx on 2006-04-07
[QUOTE=Ob1]When a new versoin of Ubuntu is realesed, will i than need to burn the newest version on a CD or will ubuntu update itself?[/QUOTE]
No just replace your sources.list with the new os and then run:

sudo apt-get update

sudo apt-get dist-upgrade

But it is best if you do a clean install.

---

### Post by Qrk on 2006-04-07
Ubuntu will update itself.  You just need to edit /etc/apt/sources.list to tell it to go to the new release.

---

### Post by AdotB on 2006-04-07
You can download int and do a fresh install, of you can edit your sources.list ```
sudo gedit /etc/apt/sources.list
``` and change all the breezy to dapper. Then type ```
sudo apt-get update 
sudo apt-get dist-upgrade
``` to upgrade to Dapper.

---

### Post by Ob1 on 2006-04-08
Thanks, but what do i need to edit in "sources.list" in order to update it to the new versoin?

---

### Post by _simon_ on 2006-04-08
as someone mentioned, you need to replace all instances of "breezy" with "dapper"

---

