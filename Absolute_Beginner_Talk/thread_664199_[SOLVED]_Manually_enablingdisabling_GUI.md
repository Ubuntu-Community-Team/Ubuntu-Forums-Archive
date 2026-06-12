---
title: "[SOLVED] Manually enabling/disabling GUI"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by MoonStomper on 2008-01-10
hi all,

i've just installed gutsy and would like to know how to manually enable/disable the GUI. this is so i can allot resources to an application that doesn't require GUI. apologies if i may have posted on the wrong section and if this is such a noob question but any advice would be much appreciated. thanks!

---

### Post by PeterJS on 2008-01-10
The easist way is to open a terminal
```

sudo /etc/init.d/gdm stop

```
And then ctrl+alt+backspace to end your current session
Then to restart the gui
```

sudo /etc/init.d/gdm start

```

---

### Post by MoonStomper on 2008-01-10
Thanks for the promt reply Peter. That did the trick. How do make the machine boot directly into terminal by default without the GUI? This way, I only run the 'start' command whenever needed and then stop it afterwards. Appreciate the help!!!

---

### Post by PeterJS on 2008-01-11
To stop gdm from loading on when the machine starts up run:
```

sudo update-rc.d gdm remove

```
You can then manually stop gdm, as above, and when you reboot gdm won't load.
More importantly to set gdm to automatically start again
```

sudo update-rc.d gdm defaults 13 01

```
The important part here is the numbers on the end, which tell the system where gdm goes in the boot up and shutdown order. It's 13th to start up, and 1st to shut down. And the leading 0 on 01 is important, because update-rc.d only works with two digit numbers.

---

### Post by MoonStomper on 2008-01-11
Got that. Will definitely check that out & post the outcome. I think I've seen some threads on 'update-rc.d' recently. I guess that's also worth reading + google. Anyways, many thanks again for your help & input. Much appreciated indeed!

Cheers! :KS

---

### Post by MoonStomper on 2008-01-18
yup..that did work :D. thanks again for your help!

---

