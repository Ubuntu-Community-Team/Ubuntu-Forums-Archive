---
title: "How long does it take a upaded program to show up in the repos?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by pentax on 2007-06-24
DigiKam has been updated to 0.9.2, the version the comes with kubuntu is 0.9.1 and there are some important changes in the latest version.
So I'm wondering about how long will it take for the updated program to show up in the repos?
And no I don't want to compile the thing my self, I read the directions, and that looks like a complicated one:(:

---

### Post by anon32 on 2007-06-24
Packages in the repositories are typically not updated to newer versions for compatibility/stability reasons. However, some are available in backports (see [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)). Digikam doesn't seem to be available anywhere, so I guess you'll have to wait until version 7.10 of Ubuntu is released.

---

### Post by cogadh on 2007-06-24
Add the following to your /etc/apt/sources.list:

deb [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./

Then run this in a terminal:
```
sudo apt-get update
sudo apt-get install digikam
```
You will get the latest version.

---

### Post by pentax on 2007-06-25
Thanks for the suggestion, I just tried that, no joy:( I'm guessing that he doesn't have a 64-bit version ready to go yet.

> **cogadh said:**
> Add the following to your /etc/apt/sources.list:

deb [http://www.mpe.mpg.de/~ach/kubuntu/feisty](http://www.mpe.mpg.de/~ach/kubuntu/feisty) ./

Then run this in a terminal:
```
sudo apt-get update
sudo apt-get install digikam
```
You will get the latest version.

---

### Post by cogadh on 2007-06-25
Install the 32 bit library support and you can use it in 64 bit Ubuntu.

---

