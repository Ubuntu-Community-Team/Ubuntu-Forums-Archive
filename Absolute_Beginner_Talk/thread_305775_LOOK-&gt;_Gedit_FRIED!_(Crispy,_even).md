---
title: "LOOK-&gt; Gedit FRIED! (Crispy, even)"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-11-23
I just tried to run gedit, and it wouldn't run. Then I tried gksudo gedit, and it wouldn't run. Then I tried sudo nano and it eventually ran but the file string was messed up: There was an extra directory, it seems:/john/home/'/etc/samba/smb.conf

I re-installed gedit, and this is what I got upon attempting to run it
```
john@ubuntu:~$ sudo gedit /etc/samba/smb.conf 
** (gedit:8525): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi) ' failed

(gedit:8525): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in  cast to `BonoboMDI'

** (gedit:8525): CRITICAL **: bonobo_mdi_get_active_child: assertion `BONOBO_IS_ MDI (mdi)' failed

(gedit:8525): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in  cast to `BonoboMDI'

** (gedit:8525): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS _MDI (mdi)' failed

** (gedit:8525): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDO W (win)' failed

** (gedit:8525): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

** (gedit:8525): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:8525): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:8525): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

(gedit:8525): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>'  in cast to `GObject'

(gedit:8525): GLib-GObject-WARNING **: instance of invalid non-instantiatable ty pe `<invalid>'

(gedit:8525): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TY PE_CHECK_INSTANCE (instance)' failed
john@ubuntu:~$

```
Man... I broke it REAL good! lol
Anyone have any ideas as to how to fix it?

---

