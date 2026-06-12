---
title: "a script to mute the computer at start"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2007-01-26
Hi,
I need a script that mutes the computer when it is turned on. I may unmute it if neccesary. Could anyone help me.

Please also verify my following statement:

I need to put that script under .bashrc folder in order to run that script at the start automatically.
 

Thanks alot.

---

### Post by displague on 2007-01-26
/var/lib/alsa/asound.state controls volume across boots.  But, off the top of my head, I'm not sure how/when that is examined.

You can install aumix (it may already be installed).  It creates /etc/aumixrc with volume settings.

Check /etc/default/aumix to make sure it does not want to save the volume on each shutdown/startup.  You can then mute your sound and save the value by running "/etc/init.d/aumix save" as root.

---

