---
title: "Fedora 19 startup-appliactaions"
date: 2013-11-10
forum: Any Other OS
---

### Post by monkeybrain20122 on 2013-11-10
Hi, 

Tried to manage my startup applications in Fedora 19 (gnome-shell) and ran

```
sudo yum install gnome-session-properties
```

But it says the package gnome-session-propertie does not exist.

Any idea?

Thanks.

---

### Post by vasa1 on 2013-11-10
> **monkeybrain20122 said:**
> ...
Any idea?...

In case you don't get an answer here, you could see if you like [https://ask.fedoraproject.org/questions/](https://ask.fedoraproject.org/questions/)

---

### Post by buzzingrobot on 2013-11-11
Try "sudo yum provides gnome-session-properties" or "sudo yum search gnome-session-properties" in case it's in a differently named package.

However, it's always been there by default in my Fedora installs. What happens when you do an Alt-F2 and enter "gnome-session-properties"?

---

### Post by monkeybrain20122 on 2013-11-11
Ok, figured it out. The package is already installed as a part of gnome-session. But for some inexplicable reasons  in the .desktop file (in /usr/share/applications) there is a line NoDisplay=True so the launcher doesn't show up, changing it to NoDisplay=False it now appears. 

Sorry I can't mark this as solved, went to Edit > Advanced didn't find the option.

---

### Post by vasa1 on 2013-11-11
> **monkeybrain20122 said:**
> ...
Sorry I can't mark this as solved, went to Edit > Advanced didn't find the option.
See if [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) helps.

---

