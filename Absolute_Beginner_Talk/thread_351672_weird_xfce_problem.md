---
title: "weird xfce problem"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by benner on 2007-02-02
i have xfce4 installed on what was an edubuntu system that also had kde.  i use this machine for messing around and learning.  when i log in with xfce, there is no toolbar at the bottom of the screen.  there is an xfce menu, but no bar across the bottom.  when i minimize anything that i am running, it vanishes.  i had xubuntu 6.06 installed a while ago and it wasn't like this.  i checked screenshots and i think it ought to be there.  i tried dpkg-reconfigure xubuntu-desktop and it finished in about a second and nothing happened.  the machine is a bit sluggish running kde and gnome so it is likely that i will stick with xubuntu once i get it on there.  currenly, my burner is not working, otherwise i would probably just reinstall it from scratch.  
any ideas?

btw, my wife needs chinese input and the chinese packages we have installed seem to make our browsers crash all the time.  i just installed everyithing that looked useful with the word 'chinese' when i was browsing repositories.  what is the best way to get real dual language functionality out of an xfce desktop?

thanks in advance for any suggestions.

---

### Post by pseudonym on 2007-02-02
> **benner said:**
> i have xfce4 installed on what was an edubuntu system that also had kde.  i use this machine for messing around and learning.  when i log in with xfce, there is no toolbar at the bottom of the screen.  there is an xfce menu, but no bar across the bottom.  when i minimize anything that i am running, it vanishes.  i had xubuntu 6.06 installed a while ago and it wasn't like this.  i checked screenshots and i think it ought to be there.  i tried dpkg-reconfigure xubuntu-desktop and it finished in about a second and nothing happened.  the machine is a bit sluggish running kde and gnome so it is likely that i will stick with xubuntu once i get it on there.  currenly, my burner is not working, otherwise i would probably just reinstall it from scratch.  
any ideas?
It sounds like Xfce's control over your desktop became unstuck temporarily (it happens from time to time. It's probably a bug in the Ubuntu version but I don't know). Go into your desktop settings (via the xfce menu or by right-clicking the desktop and choosing 'Background'). Then make sure to put a check mark in 'Let Xfce manage your desktop' (or similar - my system is in German). This should bring it back to normal.

> **benner said:**
> btw, my wife needs chinese input and the chinese packages we have installed seem to make our browsers crash all the time.  i just installed everyithing that looked useful with the word 'chinese' when i was browsing repositories.  what is the best way to get real dual language functionality out of an xfce desktop?

thanks in advance for any suggestions.
Don't know about problems related to Chinese input, but on my Xubuntu system I just ran the 'Language Support' utility in the Xfce menu, plus downloaded GNOME localisation packages to have the few GNOME apps I run appear in German.
You may also need to reset your system locales using 'sudo dpkg-reconfigure locales' from the terminal and answering the questions. [This wiki entry]("https://help.ubuntu.com/community/LocaleConf") may also be helpful to you in this regard.

HTH :)

---

### Post by benner on 2007-02-02
thanks.  i found the toolbar.  cool that you can resize and reshape it.  i minimize stuff and it disappears though.  i changed a setting so that minimized items change into desktop icons, but in that mode, i lost everything else on my desktop.  and i thought that xfce had multiple desktops like gnome and kde do.  i can't seem to find them yet.  i will keep digging around.  let me know if any of this rings a bell.  thanks for pointing me in the right direction though...

---

### Post by pseudonym on 2007-02-02
> **benner said:**
> thanks.  i found the toolbar.  cool that you can resize and reshape it.  i minimize stuff and it disappears though.  i changed a setting so that minimized items change into desktop icons, but in that mode, i lost everything else on my desktop.  and i thought that xfce had multiple desktops like gnome and kde do.  i can't seem to find them yet.  i will keep digging around.  let me know if any of this rings a bell.  thanks for pointing me in the right direction though...
All these settings should be in the settings menu on the xfce menu. For example, the 'multiple desktops' (or 'workspaces' as they are called) can be configured in the 'Workspaces Settings' menu. Just look at each menu and set the options how you want (which you are probably already doing now :) ).

---

