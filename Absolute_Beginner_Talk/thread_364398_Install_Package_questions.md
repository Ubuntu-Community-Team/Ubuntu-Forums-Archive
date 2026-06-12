---
title: "Install Package questions"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Pete89 on 2007-02-18
Hello,

I am following an install doc that calls for this command:

```
$ sudo aptitude install ruby1.9 ruby esvn
```

And here is the output afterward:

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "ruby1.9"
Couldn't find any package whose name or description matched "esvn"
The following NEW packages will be automatically installed:
  libruby1.8 ruby1.8
The following NEW packages will be installed:
  libruby1.8 ruby ruby1.8
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1627kB of archives. After unpacking 6058kB will be used.
Do you want to continue? [Y/n/?] n

```

In my very short experience with LINUX if I dont get the exact packages that this install doc is saying I need, then things might not work. 


1. Is there a possible typo in the original command?
2. I know there is a ruby1.9 package how else could I install it?
3. Does esvn exist?

Thanks,

Pete

---

### Post by v8YKxgHe on 2007-02-18
You may need to enable extra repositories, there is a good guide in the official documentation on the Wiki, [Software Repositories]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/extra-repositories.html")

---

### Post by Pete89 on 2007-02-18
That did it. I was able to download and install everything.

Thanks a million

---

