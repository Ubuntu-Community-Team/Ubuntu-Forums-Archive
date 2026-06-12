---
title: "installing flash"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by jackss on 2006-03-26
i readed the wiki for installig flash , but when i do 
sudo apt-get install flashplayer-mozilla
i get this error:
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  flashplayer-mozilla: Depends: gsfonts-x11 but it is not installable

please help me

---

### Post by Perfect Storm on 2006-03-26
How's your sourcelist looks like?

```
gedit /etc/apt/sources.list
```

---

