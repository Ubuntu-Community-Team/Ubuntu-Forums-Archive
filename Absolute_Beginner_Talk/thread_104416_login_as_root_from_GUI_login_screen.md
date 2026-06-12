---
title: "login as root from GUI login screen"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by joecheriross on 2005-12-16
How to login as root from the GUI login screen ?
How can I get the root password?

---

### Post by fog on 2005-12-16
[http://easylinux.info/index.php/Ubuntuguide#How_to_set.2Fchange.2Fenable_root_user_password.3F](http://easylinux.info/index.php/Ubuntuguide#How_to_set.2Fchange.2Fenable_root_user_password.3F)
[http://easylinux.info/index.php/Ubuntuguide#How_to_allow_root_user_to_login_into_GNOME.3F](http://easylinux.info/index.php/Ubuntuguide#How_to_allow_root_user_to_login_into_GNOME.3F)

---

### Post by Perfect Storm on 2005-12-16
It's not adviseble to do it, just as a warning. If you want to do adminstration work use the command **sudo** in front of the commands that do the work, like eg.:
```

sudo mv /home/<username>/myfilefile.txt /usr/share/blah/blah

```

or

```

sudo gedit /blah/blah/blah/mytextfile.txt

```

If you want to make a root terminal, create launcher and in the command box write:
```

gksudo /usr/bin/x-terminal-emulator

```

---

