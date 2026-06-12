---
title: "Beryl Auto-Update"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2007-02-19
Hi,

I just installed Beryl using the auto-script.  It messed up my Nvidia driver, so I used Envy to reinstall to the correct Nvidia driver.  Beryl is working great.

Will Beryl auto-update with the rest of ubuntu now that it is installed, or do I have to update it manually?

---

### Post by mcduck on 2007-02-19
I have no idea about any automatic install script, but if it's made with any common sense then yes, it added Beryl repositories to your /etc/apt/sources.list and from this on the updates for Beryl will be handles automatically by Ubuntu's package management.

---

### Post by jvc26 on 2007-02-19
If you want to check whether it added Beryl repos to your sources.list you could just do a:
```

cat etc/apt/sources.list

```
If beryls in there on the end then it did, otherwise you'll have to add it yourself.
Il

---

### Post by Waappu on 2007-02-19
> **mcduck said:**
> I have no idea about any automatic install script
Hi

Here is examples of scripts. There is also others posted in this forum.
[http://ubuntuforums.org/showthread.php?t=338771](http://ubuntuforums.org/showthread.php?t=338771)
[http://ubuntuforums.org/showthread.php?t=311925&highlight=beryl+script](http://ubuntuforums.org/showthread.php?t=311925&highlight=beryl+script)

---

### Post by mcduck on 2007-02-19
thanks, but I've been running Compiz/Beryl since first Ubuntu-compatible packages came available.. I just meant that I don't know how that script does the job (as in does it download the packages with wget or add the entry to sources.list and use apt-get)..

I prefer to do things by hand without automatic scripts. It's the only way to learn how things work.  It makes fixing possible problems much easier.

---

