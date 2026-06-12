---
title: "Is it safe to dist-upgrade from synaptic?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by hito1 on 2007-06-01
Can I upgrade from Edgy to Feisty using synaptic? Does it works? Is it better to make a clean install?

Thanks. :)

---

### Post by taurus on 2007-06-01
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by DaDave on 2007-06-01
I did a dist upgrade edgy to fiesty using the update manager with no problems. Everything works fine. Some have warned against it, but the cd install wouldn't work on my G3 so I gave it a try. 

If it doesn't work for you you can always do a clean install later.

---

### Post by starcraft.man on 2007-06-01
> **hito1 said:**
> Can I upgrade from Edgy to Feisty using synaptic? Does it works? Is it better to make a clean install?

Thanks. :)

The nature of software, hardware and user relationship dictates that no two people are likely to have the same experience, so sayeth the philosophic Protoss Zealot :p. (I like that line now that I wrote and posted it :D)

Uh, I'd back up important stuff (or put it on home drive if you already have). Things can always go wrong with an upgrade. That said, long as you didn't use Automatix (yes, I said it, I've seen problems with it, if its installed uninstall it) and if you did install 3d drivers/beryl/compiz, I'd turn them all off (lowers chance of something going wrong, heard a few people having trouble with graphics after upgrade). Then go ahead and upgrade. Do have live CD/Alt handy in case of failure (has happened to some people).

I'm a clean install man though, I always do a fresh install of any OS, thats my way and my preferred recommendation. Do whatever you think best though.

---

### Post by ncappel1 on 2007-06-01
I updated to feisty from edgy with synaptic, i didn't have any problems at all!

---

### Post by zvacet on 2007-06-02
Why don´t you upgrade with alternate CD?That way you will allways have Cd if you need it(or maybe give it to your friends)and you wil do the upgrade.Just suggestion.

---

### Post by hito1 on 2007-06-02
> **starcraft.man said:**
> The nature of software, hardware and user relationship dictates that no two people are likely to have the same experience, so sayeth the philosophic Protoss Zealot :p. (I like that line now that I wrote and posted it :D)

Uh, I'd back up important stuff (or put it on home drive if you already have). Things can always go wrong with an upgrade. That said, long as you didn't use Automatix (yes, I said it, I've seen problems with it, **if its installed uninstall it**) and if you did install 3d drivers/**beryl**/compiz, I'd turn them all off (lowers chance of something going wrong, heard a few people having trouble with graphics after upgrade). Then go ahead and upgrade. Do have live CD/Alt handy in case of failure (has happened to some people).

I'm a clean install man though, I always do a fresh install of any OS, thats my way and my preferred recommendation. Do whatever you think best though.

So you recommend uninstalling automatix and disabling beryl? Just **disabling**, not uninstalling, right?

Thank you, all.

---

### Post by arnieboy on 2007-06-02
> **hito1 said:**
> So you recommend uninstalling automatix and disabling beryl? Just **disabling**, not uninstalling, right?

Thank you, all.
remove the automatix edgy repository from your /etc/apt/sources.list
> deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
do a 
```
sudo apt-get update

```and then proceed to upgrade to Feisty.
You can remove the edgy version of automatix once you are done upgrading and install the feisty version. 
The automatix repo is just like any other repo.. you **cannot have** an edgy repo in your sources.list when you are upgrading to feisty.

---

### Post by hito1 on 2007-06-02
> **arnieboy said:**
> remove the automatix edgy repository from your /etc/apt/sources.list

do a 
```
sudo apt-get update

```and then proceed to upgrade to Feisty.
You can remove the edgy version of automatix once you are done upgrading and install the feisty version. 
The automatix repo is just like any other repo.. you **cannot have** an edgy repo in your sources.list when you are upgrading to feisty.
I see, thanks. :)

---

