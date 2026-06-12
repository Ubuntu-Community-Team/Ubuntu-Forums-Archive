---
title: "Can't install things, still running Breezy Badger"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Arndt on 2007-09-26
I don't know if this makes me the slowest Ubuntu user in history, but I'm still using Breezy Badger, mainly because I was new to Ubuntu and worried that something would break when I upgraded, and because I saw no compelling reason to.

Now it seems I left it too long to upgrade, becase Synaptic doesn't seem to find the download sites any longer, now that I need a new package for the first time in six months.

What's the best way to proceed? Should I upgrade to the latest version, or one step at a time (if that's even possible)? Are there any particular problems I should be prepared for?
(And how I even do it, when Synaptic isn't happy?)

---

### Post by Lord Illidan on 2007-09-26
Personally, I'd just do a backup, grab the Feisty cds and make a new installation.

Upgrading will be a very very long process (if it is even possible, and you might get plenty of errors along the way, as I recall the transition from Breezy to Dapper wasn't exactly super smooth)

---

### Post by nvteighen on 2007-09-26
Breezy's support ended in April 2007, that's why Synaptic doesn't find anything.

You can upgrade to Dapper (6.06) typing this at Terminal if I remember well:
```

sudo apt-get dist-upgrade

```

From Dapper you can then upgrade to Edgy (6.10). And from Edgy to Feisty (7.04).

---

### Post by Lord Illidan on 2007-09-26
> **nvteighen said:**
> Breezy's support ended in April 2007, that's why Synaptic doesn't find anything.

You can upgrade to Dapper (6.06) typing this at Terminal if I remember well:
```

sudo apt-get dist-upgrade

```From Dapper you can then upgrade to Edgy (6.10). And from Edgy to Feisty (7.04).

If you're on dialup that will take a nice long time to do it...

---

### Post by mcduck on 2007-09-26
> **nvteighen said:**
> Breezy's support ended in April 2007, that's why Synaptic doesn't find anything.

You can upgrade to Dapper (6.06) typing this at Terminal if I remember well:
```

sudo apt-get dist-upgrade

```

From Dapper you can then upgrade to Edgy (6.10). And from Edgy to Feisty (7.04).

I don't thing Breezy had the ability to upgrade with a GUI. And even then simple dist-upgrade alone wouldn't start the upgrade.

It would require editing the sources.list to point to Dapper repositories and after that runing 'sudo apt-get update' and 'sudo apt-get upgrade'.

I'd recommend just downloading Feisty or Gutsy CD and doing a new install.

---

### Post by Arndt on 2007-09-26
> **nvteighen said:**
> Breezy's support ended in April 2007, that's why Synaptic doesn't find anything.



Where should I have been looking to find that out?

I'm not on dial-up, by the way, the Internet connection is quite fast.

---

### Post by Bothered on 2007-09-26
It's on the [ubuntu Wikipedia page]("http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29")

---

### Post by Lord Illidan on 2007-09-26
I'd get Ubuntu gutsy or Feisty. You only need to download 700 Mb that way, and it's safer, I think.

---

### Post by Kilz on 2007-09-26
The earlier versions did not always upgrade smoothly from one to the other the Dapper -Edgy one is a disaster for a lot of people. 
Its better to do a clan install, but some people have a lot of files so that isnt a good option for them. But if you have a lot of hard drive room you can install to another partition, then mount the old install to a folder and copy over the files. Then delete the old one when everything is working.
But I would stick to Feisty or put off until Gutsy is released if you want Gutsy. Development versions can have issues even this close to release.

---

