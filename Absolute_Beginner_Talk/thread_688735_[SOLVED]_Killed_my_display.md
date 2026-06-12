---
title: "[SOLVED] Killed my display"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by ultraloveninja on 2008-02-05
So, I've been grinding it out the past couple of days to get my display drivers to function right and when I got them to install correctly, I goofed and changed a setting and now when I boot, it's blank.
I have a Gateway laptop with an ATI radeon xpress 200M.
Is there any way that i can configure it in recovery mode to roll back to the regular display from the command line in recovery mode?


Also, while I am at it, as I mentioned before, I've been having a HELL of a time to get my display to function correctly.  It wasn't until I enabled all 3rd party downloads to take place in the update manager I was able to make some headway.  But if anyone know what I can do in order to configure my ATI xpress 200M to run optimally I would greatly appreciate it.
Thanks!

---

### Post by jan quark on 2008-02-05
try this command in recovery mode
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ultraloveninja on 2008-02-05
Awesome.
Looks like it reloaded the last config.
Back to normal for now.

I am gonna search the threads to see what i need to do to configure the ATI drivers to make them run optimally.

Thanks again.

---

