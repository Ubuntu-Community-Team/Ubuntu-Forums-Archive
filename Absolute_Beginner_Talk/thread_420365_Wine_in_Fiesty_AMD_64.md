---
title: "Wine in Fiesty AMD 64 ?"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-04-23
I have the universe and multiverse repositories checked in Fiesty AMD 64.  I ran this command:

```
sudo apt-get install wine
```

It tells me that there is no app called Wine, but there is something similar.  I looked in Synaptic and didn't see Wine listed in there either.

I also didn't find anything about Wine in this guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Is running Wine possible with Fiesty AMD64?

---

### Post by snake1130 on 2007-04-23
You need to add the Wine Repos.

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by kc5hwb on 2007-04-23
That same link you put there says...

> **64-bit Users:**

Note that, at this time, the entries above are for i386 users only. Attempting to use these repositories with a different architecture (eg amd64), will result in 404 errors as APT will be looking for files not in the repository.

While there is currently no Wine package explicitly designed for the 64-bit version of Ubuntu, there is an easy hack that can be used to install the 32-bit package into the 64-bit distribution and have it function normally. See this page on the Wine wiki for more details.

---

