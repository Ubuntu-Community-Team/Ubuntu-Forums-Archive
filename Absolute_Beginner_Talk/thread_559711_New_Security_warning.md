---
title: "New Security warning"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by greybeard12us on 2007-09-25
'E:Type '://security.ubuntu.com/ubuntu' is not known on line 40 in source list /etc/apt/sources.list, E:The list of sources could not be read.'
This one showed up this mornig upon boot up and trying to run package manager, I am very new to this type of operating system and need HELP.

---

### Post by bodhi.zazen on 2007-09-25
Post the content of /etc/apt/sources.list or the output of :

```
sudo cat -n /etc/apt/sources.list | grep 40
```

---

