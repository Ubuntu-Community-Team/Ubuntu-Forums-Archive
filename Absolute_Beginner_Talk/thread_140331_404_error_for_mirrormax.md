---
title: "404 error for mirrormax"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by Xaviar on 2006-03-06
I am trying to add extra repositories and have used the Unofficial Ubuntu 5.04 guide to assist. 

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

 The problem I have is that the backports given

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

 returns an error of 404  when I run it in a  terminal as if the adress is no longer valid
I'm  little lost - is the website hosting them down? are they no longer valid?  should I go somewhere else?

I must note that I am using hoary hedgehog whilst waiting for my breezy badger to arrive.

---

### Post by Madpilot on 2006-03-06
ubuntuguide.org is very, very out of date. Avoid it in favour of wiki.ubuntu.com or help.ubuntu.com.

The Mirrormax backports closed months ago; to get Hoary Backports, use
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main restricted universe multiverse
instead.

(The backports are now an official Ubuntu project)

---

### Post by aysiu on 2006-03-06
Mirrormax is dead.

Follow these instructions:
[http://www.psychocats.net/linux/sources](http://www.psychocats.net/linux/sources)

---

### Post by Xaviar on 2006-03-09
Sorry for taking so long to thank you (computer crash).  I am following your advice.  Thankyou both.

---

