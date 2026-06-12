---
title: "can updates be downloaded from a different location"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by tobmeister on 2006-09-02
I have a dial up connection at my home but I have access to a T1 at work.  Is it possible to download all the updates for 6.06 from a site and then update my computer when I get home from work?

Thanks

Tobmeister

:confused:

---

### Post by ciscosurfer on 2006-09-02
I believe you can do this.  What I would do is download all updates and burn them to a cdrom.  When you get home, in GNOME, goto [COLOR=Purple]System > Administration > Software Properties[/COLOR] (or from within [COLOR=Purple]Synaptic Package Manager, click Settings, then Repositories[/COLOR].)  Then click the button that says [COLOR=Red]Add CD-ROM[/COLOR], and follow the prompts from there.  If you don't want any of the other repositories enabled, *uncheck* their repsective boxes (or go into your sources.list file [[COLOR=DarkRed]sudo gedit /etc/apt/sources.list[/COLOR]] and comment in all the repos you don't want to use with a pound sign ([COLOR=Red]# -- just a pound sign, no other marks[/COLOR])).  Then update your machine as usual either through Synaptic (remember to click Update first in order for your new CD-ROM line to take effect) or via the terminal, like so```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

