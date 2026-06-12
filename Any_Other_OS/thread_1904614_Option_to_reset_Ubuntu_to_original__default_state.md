---
title: "Option to reset Ubuntu to original / default state"
date: 2012-01-05
forum: Any Other OS
---

### Post by danieldbird on 2012-01-05
Just for general discussion, information, and to promote the idea originally posted by Liono in the [Ubuntu Brainstorm forum]("http://brainstorm.ubuntu.com/idea/28973/").

----------------------------------------

**Rationale**
Many novice Ubuntu users tend to fiddle with various configurations on Ubuntu and end up causing their machines to hardly boot or start the GUI. Common example are things like, changing graphics driver or modifying the display resolution, and so on... 

Usually the fix involves only having to run one command such as removing the xorg.conf file or running "dpkg-reconfigure gdm" to rebuild the defaults, but to the mainstream, this is too daunting. 

So rather than formatting, reinstalling Ubuntu, creating a new username to login with, or trying to decipher error messages and commands, I propose an easier way to reset the system into a like-new state. 

Add a system option that deletes all configuration files as if the system was freshly installed and all hardware/drivers and settings have been reset to their defaults.

Allow the user to select which aspects to reset: 

* Reset Graphics and Display Settings 
* Reset Desktop Environment and Unity (X11, input devices) 
* Reset Network (network manager and /etc/network/interfaces) 
* Reset Language/Localization 
* Reset Audio drivers/settings 
* etc...

----------------------------------------

Windows 8 will come with the option of resetting the operating to it's original / default state.
View the article [here]("http://blogs.msdn.com/b/b8/archive/2012/01/04/refresh-and-reset-your-pc.aspx"):
[http://blogs.msdn.com/b/b8/archive/2012/01/04/refresh-and-reset-your-pc.aspx](http://blogs.msdn.com/b/b8/archive/2012/01/04/refresh-and-reset-your-pc.aspx)

Regards,
Daniel.

---

### Post by kr651129 on 2012-01-05
It would be a pretty simple script to write that did an auto backup of the most important config files and when things go crazy you could boot into a shell and type something like

```
$>restore-default-configs
```

And then have the script remove all configs and replace them with config-whatever.config.old

---

