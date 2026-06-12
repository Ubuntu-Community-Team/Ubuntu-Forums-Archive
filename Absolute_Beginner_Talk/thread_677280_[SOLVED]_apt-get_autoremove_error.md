---
title: "[SOLVED] apt-get autoremove error"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by y-lee on 2008-01-24
I was trying to clean my system up and got the following error: 

```
sudo apt-get autoremove
E: Invalid operation autoremove
```

By the way I use Dapper is apt-get autoremove not supported?

---

### Post by nikoPSK on 2008-01-24
dapper should be fine, was it working before?

---

### Post by y-lee on 2008-01-24
I don't know if it was working before. Today was the first time I tried it. It is no big deal, just confuses me :confused: Kinda new to linux so things sometimes confuse me.

---

### Post by nikoPSK on 2008-01-24
autoremove just deletes unnecessary packages.:)

---

### Post by y-lee on 2008-01-24
Yep. I know what it does. 

Just now tried marking it for reinstallation in Synaptic. After reinstalling still get the same error. Hmmm....

I would like to know how to fix it tho :(

BTW apt-get everything else works, at least the stuff I use.

---

### Post by ThrobbingBrain66 on 2008-01-24
I don't think autoremove is supported in Dapper.  I think it showed up in either Edgy or Feisty.

---

### Post by y-lee on 2008-01-24
> **ThrobbingBrain66 said:**
> I don't think autoremove is supported in Dapper.  I think it showed up in either Edgy or Feisty.

Certainly doesn't appear to be supported. :lolflag:

---

### Post by y-lee on 2008-01-24
You are right It is not supported, just found this

> Important Update

Apparently the new version of apt-get in Edgy Eft (Ubuntu 6.10) has a function that allows you to remove unused dependencies when removing an application:
sudo apt-get autoremove applicationname

See [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

Thanks to both of you. I marking this as solved. Maybe it will help other Dapper users. :)

---

### Post by Butthead on 2008-01-24
Isn't the command "autoclean" in Dapper? :confused:

---

### Post by ThrobbingBrain66 on 2008-01-24
autoclean and autoremove are two different commands.  Autoclean removes downloaded packages from the apt archive.  Autoremove  removes dependencies that are no longer needed.

---

### Post by y-lee on 2008-01-24
Nope!

> autoclean: removes all stored archives in your cache for packages that can not be downloaded anymore (thus packages that are no longer in the repo or that have a newer version in the repo).

clean: removes all stored archives in your cache.

autoremove:  this option makes apt look for packages that are installed as dependency of an already uninstalled package and removes them. This is used to clean up unused dependencies that remain on your system.

see [What is the difference...]("http://ubuntuforums.org/showthread.php?t=394952")

---

