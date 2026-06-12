---
title: "Which NVIDIA driver?"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by baracuda68 on 2007-08-04
Hi.
I am using a GeForce2 MX/MX400 card.
Everything I read, and I think it installs by default, says to use the_ nvidia-legacy_ driver.
I am _currently using the -glx driver_.
It seems to work fine.
Would I notice a difference-improvement or decline- in performance using the legacy driver?
Should I revert back? Should I try the -glx-new driver?

I don't like to mess too much with the vid drivers, because when I do, I have to set up the xorg conf file, when I lose my X. I am not really use to terminal commands yet...still a noob...

---

### Post by overdrank on 2007-08-04
> **baracuda68 said:**
> Hi.
I am using a GeForce2 MX/MX400 card.
Everything I read, and I think it installs by default, says to use the_ nvidia-legacy_ driver.
I am _currently using the -glx driver_.
It seems to work fine.
Would I notice a difference-improvement or decline- in performance using the legacy driver?
Should I revert back? Should I try the -glx-new driver?

I don't like to mess too much with the vid drivers, because when I do, I have to set up the xorg conf file, when I lose my X. I am not really use to terminal commands yet...still a noob...

Hi all I can say is that if you have no problems the don't worry but if you wan to search and see then do that, and research and see if you want to change and try something new. I did a quick search of the forums on that video card and that may help
[http://ubuntuforums.org/search.php?searchid=24829433](http://ubuntuforums.org/search.php?searchid=24829433)
Good luck and remember to back up your xorg and them try what you find. Each computer is different and it may not work for you and then it may work. Good luck !!!:popcorn:

---

### Post by asmoore82 on 2007-08-04
run this command in  a term and post the output ...

```
~ $ grep Driver /etc/X11/xorg.conf
```

---

