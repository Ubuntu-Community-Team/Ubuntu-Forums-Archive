---
title: "Trouble with printing, job-hold-until-specified"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by dberg on 2007-05-05
I am trying to install my Canon PIXMA iP-4200 following the howto posted [here.]("http://ubuntuforums.org/showthread.php?t=204853") It worked fine when I did this in Dapper, but since installing Feisty it no longer works. I get the status ```
Paused: job-hold-until-specified
``` in my printing window.

I tried replacing all occurrences of ATTRS with SYSFS in /etc/udev/rules.d/45-libgphoto2.rules as suggested [here.]("http://ubuntuforums.org/showthread.php?p=2270082#post2270082") But this did not work.

Does anybody have any ideas?

Thanks.

---

### Post by dberg on 2007-05-05
I just noticed this while looking around at settings and such.

In the properties for my printer the status says```
Ready: Unable to open USB port device file: No such file or directory
```

I assume that this would mean it is actually not ready...

I have read other places that there is a problem with cupsys and udev or something like that but I don't really know what that means, can anyone help with this? Thanks.

---

### Post by dberg on 2007-05-06
bump

---

### Post by nquinnathome1 on 2008-05-10
It's definitely a problem with your printer and/or cupsys; might be worth entering CUPS directly ([http://localhost:631](http://localhost:631)) and checking the configuration of your printer, or checking that CUPS has the printer, it's 'ready' and seeing if you can print a test page.

---

