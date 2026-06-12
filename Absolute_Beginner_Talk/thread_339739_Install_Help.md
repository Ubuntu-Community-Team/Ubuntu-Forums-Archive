---
title: "Install Help"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by willbur on 2007-01-16
Hi all

Another silly newbie question, I'm afraid :) 

When I install via either of the package managers, I'm told that the 'packages will be cached locally prior to installation'. Does Ubuntu remove these zipped or tarred packages once the software is successfully installed after a set time? They seem to be left on my system if I uninstall a package using the same package managers. Should I manually remove these files (if so - how?), or is it best not to worry, and just enjoy Ubuntu?

Many thanks in advance....

---

### Post by Qrk on 2007-01-16
They are cached, in /var/cache/apt/archives

To remove the cached files, use the command,

```
sudo apt-get clean
```

---

### Post by willbur on 2007-01-16
Many thanks, qrk - I really appreciate the help :)

---

