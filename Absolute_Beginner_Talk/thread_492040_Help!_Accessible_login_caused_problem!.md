---
title: "Help! Accessible login caused problem!"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by ela04cz on 2007-07-04
I installed Xubuntu desktop on Ubuntu 7.04. Yesterday I checked the "enable asscessible login" option in login windows, which lead to a problem that I cannot log into the desktop! The cursor loads forever and does nothing at all, I searched for answer and it seems to be a bug of Ubuntu 7.04, the system enters a loop and never gets out. No suitable solution found so far yet. :(

I tried to reinstall the xubuntu desktop but it didin't work, and I tried several command lines in the recovery mode such as apt-get update, dpkg-reconfigure xserver-xorg, apt-get check, none of them worked.

I also wondered if there is anyway to recover the system, just as the windows restore point, but I know nothing about command lines so I do not know how. Also, is there anyway to turn off the asscessible login thingy through command lines in recovery mode?

Please someone give me some suggestion about this, I don't want to reinstall the whole thing again as I have been through it 5 times recently! Thanks a lot!!!:popcorn:

---

### Post by bapoumba on 2007-07-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/gdm/+bug/107383](https://bugs.launchpad.net/gdm/+bug/107383) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Please check this bug.

As an example, here is my gdm.conf-custom file (did not copy all the comments from the top of the file.
```
~$ cat /etc/gdm/gdm.conf-custom
[daemon]

[security]

[xdmcp]

[gui]

[greeter]
SoundOnLoginSuccess=true
SoundOnLoginSuccessFile=/usr/share/sounds/login.wav

[chooser]

[debug]

[servers]

```

---

