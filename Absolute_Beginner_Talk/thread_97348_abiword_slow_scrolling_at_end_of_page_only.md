---
title: "abiword slow scrolling at end of page only???"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by rancam on 2005-11-30
Hi, I was hoping someone might have an idea on this.  My system is prettly old but should be able to run abiword fairly quick.  Paging up and down on a document that is open is fast but when I just press enter and scroll down just one line when I am at the end of the page it takes 20 seconds. press down again it takes another 20 seconds moving pixel to pixel.  So it looks like it has to do with the scolling.  Openoffice 2 runs faster.

I have installed it multiple ways, through the package manager, from the source at the website and the autoinstaller.

I have the current version on ubuntu on my machine, I had a different distro called Vectolinux and Abiword worked fine in that.  

I googled it and thought that if I could disable smooth scrolling it might help, I tried to edit hte Abiword.Profile but it seems that it gets overwritten whenever I boot it up.

Thanks in advance for any help.

rancam

---

### Post by underpope on 2006-11-04
I know this is an old thread, but did you ever find a solution to this issue?

---

### Post by BarakNaveh on 2007-03-09
well, after a rather long search i found how to turn off smooth scrolling. i'm posting it here as this post is ranked high on google.

all you need is to edit your  ~/.AbiSuite/AbiWord.Profile and add:
```

EnableSmoothScrolling="0"

```
to the scheme named custom.

AbiWord has a bug that is manifested as a slow scrolling following a quick sequence of pgup of pgdn keystrokes. On an old machine it makes AbiWord unusable. It's still exists but largely less disturbing when smooth scroll is off.

more details at:
[http://www.vectorlinux.com/forum1/index.php?PHPSESSID=04038af46a14de1cf53efb86e3a33ad4&topic=10110.0](http://www.vectorlinux.com/forum1/index.php?PHPSESSID=04038af46a14de1cf53efb86e3a33ad4&topic=10110.0)

---

