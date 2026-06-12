---
title: "Gnome-Panel applications (Elementary OS)"
date: 2014-07-03
forum: Any Other OS
---

### Post by andres11 on 2014-07-03
Hi everyone i have some questions :/

i've installed Gnome-panel and it came with a lot of applications i dont want any of them ( i dont know why i installed lol ), but i try with apt-get --purge remove gnome-panel but is doesnt dissapear. so what can i do to unistall all the package?

thank you

---

### Post by ibjsb4 on 2014-07-03
You must of installed gnome-panel with the recommended packages and this inturn installed a lot of extra stuff, including gnome-session-flashback (a complete desktop environment).

[http://packages.ubuntu.com/trusty/gnome-panel](http://packages.ubuntu.com/trusty/gnome-panel)
[http://packages.ubuntu.com/trusty/gnome-session-flashback](http://packages.ubuntu.com/trusty/gnome-session-flashback)

I do not know of a easy way to back out of this.
This could of been avoided with the proper command.
```
sudo apt-get install --no-install-recommends gnome-panel
```
If you would use Synaptic-package-manager to install packages, it will list all packages you are about to download before you commit.
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
[http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html](http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html)

---

