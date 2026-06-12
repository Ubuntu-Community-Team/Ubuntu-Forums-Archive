---
title: "Optimization?"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by pipin on 2007-01-07
Hello. Does Ubuntu need optimization? I mean does program uninstalling or any other application leave any remnant that might slow down system ? Do I need optimization programs such as Tune-up 2007 used for Windows and is there any equivalent for Ubuntu?
Thanks in advance.

---

### Post by meng on 2007-01-07
IMO, Ubuntu does not need that sort of maintenance. Application installing and uninstalling is much cleaner than in Windows.

---

### Post by madmetal on 2007-01-07
> **meng said:**
> IMO, Ubuntu does not need that sort of maintenance. Application installing and uninstalling is much cleaner than in Windows.

+1 
if you dont mess things up , then ubuntu wont need optimization..
;)

---

### Post by bodhi.zazen on 2007-01-07
> **pipin said:**
> Hello. Does Ubuntu need optimization? I mean does program uninstalling or any other application leave any remnant that might slow down system ? Do I need optimization programs such as Tune-up 2007 used for Windows and is there any equivalent for Ubuntu?
Thanks in advance.

Optimization is rather open-ended ...

As far as you question, see if these links help:

[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

[http://doc.gwos.org/index.php/RemoveJunkFiles](http://doc.gwos.org/index.php/RemoveJunkFiles)

---

### Post by aysiu on 2007-01-07
I would install BUM and disable any unneeded services. Paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install bum gksu
gksudo bum &
```

---

