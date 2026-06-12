---
title: "where is gnome-power-manager?"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-01-14
I cannot find gnome power manager, on terminal i type
gnome-power-manager or sudo gnome-power-manager but nothing comes out (there is stg coming but get lost quickly). Before (with sudo) I could change settings such as lid closed, suspend, etec modes. I have it from ststem> power management but it has very limited options.

any idea why does not come up from a terminal???

thank you,

---

### Post by marx2k on 2007-01-14
gnome-power-manager is the backend.  You're thinking of 'gnome-power-preferences' ...type that from terminal... but I think it takes you to the program/gui you're unsatisfied with anyway :( 

gnome-power-manager:
```

       gnome-power-manager  is  the backend program of the GNOME power management
       infrastructure providing a complete and integrated solution to power  man&#8208;
       agement under the GNOME desktop environment.

       It supports features such as suspending, hibernating, screen blanking, cpu
       frequency switching and more in one small neat package.

```

gnome-power-preferences:
```

       gnome-power-preferences  is the gui program for the gnome power management
       infrastructure

```

---

### Post by findik1 on 2007-01-14
well I typed gnome-power-preferences, I did not get the gui that I was getting when I installed the ubuntu. And I also get the following errors. Stg wrong?
** (gnome-power-preferences:7840): CRITICAL **: dbus_g_proxy_new_for_name_owner: assertion `connection != NULL' failed

** (gnome-power-preferences:7840): CRITICAL **: dbus_g_proxy_add_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnome-power-preferences:7840): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (gnome-power-preferences:7840): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

---

### Post by findik1 on 2007-01-30
I found it: on the terminal type

gconf-editor 

then you can edit settings in power manager.

---

