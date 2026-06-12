---
title: "Gedit Problem"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by hardfire_avk on 2006-06-25
In a terminal whenever i type a gedit command using the sudo or su or gksudo I get the following message...

```

avinash@avinash:~$ gksudo gedit /etc/modprobe.d/aliases
(gedit:7867): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
avinash@avinash:~$
```

What should I do??

---

### Post by taurus on 2006-06-25
How about
```

sudo gedit /etc/modprobe.d/aliases

```

---

### Post by adam.tropics on 2006-06-25
But does it open the file? I get the same message, but it opens the file ok.

---

### Post by hardfire_avk on 2006-06-25
No. The window also doesn't open?

Sudo also didin't work.

---

### Post by hardfire_avk on 2006-06-25
If i type **sudo Gedit** then this error comes

```

avinash@avinash:~$ sudo gedit /etc/hosts

** (gedit:7856): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi) ' failed

(gedit:7856): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in  cast to `BonoboMDI'

** (gedit:7856): CRITICAL **: bonobo_mdi_get_active_child: assertion `BONOBO_IS_ MDI (mdi)' failed

(gedit:7856): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in  cast to `BonoboMDI'

** (gedit:7856): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS _MDI (mdi)' failed

** (gedit:7856): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDO W (win)' failed

** (gedit:7856): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

** (gedit:7856): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:7856): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:7856): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

(gedit:7856): GLib-GObject-WARNING **: invalid uninstantiatable type `void' in c ast to `GObject'

(gedit:7856): GLib-GObject-WARNING **: instance of invalid non-instantiatable ty pe `void'

(gedit:7856): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TY PE_CHECK_INSTANCE (instance)' failed


```


If i use the **su** thing then this comes

```


avinash@avinash:~$ su
Password:
root@avinash:/home/avinash# gedit /etc/hosts

(gedit:7926): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

*nothing comes here *

```

---

