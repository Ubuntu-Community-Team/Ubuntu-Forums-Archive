---
title: "Load nvidia-settings at startup?"
date: 2009-02-13
forum: Arch and derivatives
---

### Post by Open-SuSe-A-Me on 2009-02-13
From the Arch Nvidia wiki:

Nvidia-Settings Autostart: You might like to apply the settings chosen using nvidia-settings at startup, firstly run nvidia-settings at least once in order for settings to be restored. The settings file is stored in ~/.nvidia-settings-rc. Then add the following to the auto-startup method of your DE:

nvidia-settings --load-config-only


I know in gnome its as simple as adding that line to "sessions" which worked for me but now i am using kde3 and I am unsure of how to do this.

I know about the /.kde/.Autostart folder but i'm assuming i would have to write some kind of script to get that to work.  Anyone know how i can do this or an alternative method for kde?

Thanks

---

### Post by justsomedude on 2009-02-13
```
#!/bin/bash
nvidia-settings -l
```

This should do it. Make sure it's executable and save it as nvidia-start.sh or something in your autostart folder. :)

---

### Post by Open-SuSe-A-Me on 2009-02-14
Thanks Dude, that worked beautifully!

---

