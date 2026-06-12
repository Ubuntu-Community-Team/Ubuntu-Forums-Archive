---
title: "Example procedures for manually downloading/installing packages from binary/source"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by sulien on 2006-04-10
Could someone present a hypothetical example from start to finish how one would manually download, install, configure a package and all its dependencies from start to finish. I am a complete newbie to this and I am curious how to do it without apt-get update, apt-get upgrade or the synaptic package manager.

For example for package A with dependencies B,C and D how does one do it? What, Where, How and When? thanks!!!! ](*,) :confused: :-k

---

### Post by trent dillman on 2006-04-10
Go to packages.ubuntu.com, and search for what you want. Download all the dependencies that go with it, as well as the dependencies for the dependencies. About 3 levels should cover it. Then, open a terminal to the directory they've been saved to, and do

```
dpkg -i *.deb
```

If it errors for more dependencies, go find those and do it again.

---

