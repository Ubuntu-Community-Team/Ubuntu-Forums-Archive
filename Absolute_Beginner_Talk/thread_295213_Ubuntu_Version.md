---
title: "Ubuntu Version"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by Endow on 2006-11-07
This might strike many as a naive question but in the end I can't really tell.I had 6.06 LTS and then when I heard about Edge Eft I updated.But I get messages all around my system concerning dapper and if i press Ctrl+Alt+F1 it says I'm rtunning dapper....


So how can I know for sure?

---

### Post by taurus on 2006-11-07
<Ctrl><Alt>F2

<Alt>F7 to get back...

---

### Post by GStubbs43 on 2006-11-07
If you just updated and never changed your sources.lis to edgy, you are running Dapper still.
Also, System>About Ubuntu should also tell you.

---

### Post by Fully216 on 2006-11-07
If you run grub, you can see the old kernel versions there as well.  The top entry should be edgy.

---

### Post by Endow on 2006-11-08
So how exactly do I fully update to Edgy?The other day a friend of mine said it would be best to do a clean install in order for me not to have problems....what was that all about?

---

### Post by taurus on 2006-11-08
If you are running Dapper right now and would like to upgrade to Edgy, **_backup_** your personal files first and follow this guide to upgrade it...

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

However, the best way is to do a fresh install of Edgy, avoiding problems like some people have when they upgraded from Dapper to Edgy.

---

### Post by Rui Pais on 2006-11-08
> **Endow said:**
> This might strike many as a naive question but in the end I can't really tell.I had 6.06 LTS and then when I heard about Edge Eft I updated.But I get messages all around my system concerning dapper and if i press Ctrl+Alt+F1 it says I'm rtunning dapper....


So how can I know for sure?

uname -a  ->  tells you the kernel in use. Edgy default should be 2.6.17-Generic

lsb_release -a  -> tells you which base system you have.

---

