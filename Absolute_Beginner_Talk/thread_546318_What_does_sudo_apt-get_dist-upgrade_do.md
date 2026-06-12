---
title: "What does sudo apt-get dist-upgrade do?"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-09-08
Is this the correct way to upgrade your distro from, say, ALPHA 5 to BETA? Or from BETA to stable?

If not, what do I type to properly upgrade? I remember there was another command for upgrading but can't remember any letter of it now...

---

### Post by El Rogueo on 2007-09-08
> **Majorix said:**
> Is this the correct way to upgrade your distro from, say, ALPHA 5 to BETA? Or from BETA to stable?

The command ```
sudo apt-get dist-upgrade
``` I think is for upgrading between stable distros, like Edgy to Feisty. Don't you have to upgrade between sub-stable releases manually?

---

### Post by Majorix on 2007-09-08
How do you mean manually? Well I want to upgrade from ALPHA 5 to BETA when it comes out in the following days. And when I am on BETA, I will upgrade to the stable release when it comes out too.

---

### Post by aysiu on 2007-09-08
As long as you have the proper metapackage installed (*ubuntu-desktop*, *kubuntu-desktop*, *xubuntu-desktop*, or *edubuntu-desktop*), the command ```
sudo apt-get update && sudo apt-get dist-upgrade
``` is **always** the proper way to upgrade your Ubuntu system, whether you are in alpha, beta, release candidate, or official release.

---

### Post by Majorix on 2007-09-08
Ok thanks a lot.

I do have the ubuntu-desktop metapackage installed, but some programs want to remove it when they are being installed. And some people say that its safe to let them remove it. What if I allow them to do so? How can I update then?

---

### Post by aysiu on 2007-09-08
Especially if you're using a testing version of Ubuntu, upgrades will often involve the removal of some packages and the addition of other packages. That's the whole point of having the metapackage installed.

---

