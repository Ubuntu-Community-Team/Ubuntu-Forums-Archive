---
title: "Firefox Crash Issue in Gutsy"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by CosmicFlux on 2007-12-06
Hey,

OK, I've recently started experiencing problems when using Firefox. I'll be online and suddenly the screen will Grey out and lock up. Eventually the option to force a quit will come up. 

Anyone got any suggestions? Is this a common issue?

---

### Post by lemmy999 on 2007-12-06
Unfortunately this is, I believe, a common problem. All it takes for me is to try and connect to a site that has been disabled and its grey-out time. 

Maybe I'll try gran-paradiso instead ( or even opera!)

---

### Post by rax_m on 2007-12-06
Or swiftfox .... which remembers all your firefox config and addons without the freezes!

---

### Post by justinmiller87 on 2007-12-20
Well, I am having the issue as well, so I went ahead and ran FireFox from a terminal. It happens whenever I use Yahoo! Mail to read a message. Here is my output:

```
(gecko:7165): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Times New Roman 12'
Segmentation fault (core dumped)
```

I installed Epiphany as a temporary workaround, but I love my Mozilla. Any suggestions? 

I submitted a [bug report.]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/177661")

---

