---
title: "trivial beryl problem"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-02
I have installed and configured Beryl properly. Also my nvidia drivers. It worked well for some time, until i messed up the settings with beryl manager. So know when i run beryl-manager the system freezes so i can only restart my computer.
So i can't return the settings to default without running beryl-manager.

I have tryed those two methods :

1. deleting and installing beryl
```

sudo apt-get remove beryl emerald-themes
sudo apt-get install beryl emerald-themes

```
hasn't worked

2. deleting all the settings files of beryl, and installing beryl again. Hasn't worked

So help me please:(

---

### Post by moma on 2007-01-02
You can also use the --purge option when you remove packages. 
$ sudo apt-get remove --purge  ....
--purge instructs apt to clear and delete all configuration files related to the packages.

--reinstall option is also handy.
$ sudo apt-get install --reinstall ....

Anyway.
Edit your .beryl-managerrc file and set the active_wm to something else than 0 ( and maybe [COLOR="Red"]use_fallback_wm=true.[/COLOR] )

$ [COLOR="SeaGreen"]cat .beryl-managerrc[/COLOR]

[wm-settings]
active_wm=3
fallback_wm=0
active_dm=0
use_fallback_wm=true

---

### Post by Sasa_Ivanovic on 2007-01-02
ok, still doesn't work.
I sucsseded in running beryl-manager, and restored all settings to default.
Then when i swiched to beryl window manager, it freezed.
Can someone help?

---

