---
title: "Pidgin Won't Open"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-11-19
Hey guys. I tried opening Pidgin several times today (and I've  rebooted) but it won't open. Does anyone know why? Thanks.

---

### Post by Darkade on 2007-11-19
Could you run it in a terminal and copy-paste the error message you get?

---

### Post by DutyDuty on 2007-11-19
Try updating and\or reinstalling it.

---

### Post by TimHeckman on 2008-01-07
I get the same problem, but get this...

When I run Pidgin in terminal, it works fine.  Yet, when I run pidgin through the gnome applications menu, it doesn't.  

And I really don't feel like showing my little sisters how to use terminal.

Anyone have any ideas on what the cause is?

Thanks for your help, beforehand!

Edit:

Correction:  It works as root, but not my username.  Let me look through the debug to find out what's causing it.  Man, it was just working too.  Argh!

[QUOTE=Debug]
(01:52:41) prefs: Reading /home/element/.purple/prefs.xml
(01:52:41) prefs: Finished reading /home/element/.purple/prefs.xml
(01:52:41) dbus: okkk
(01:52:41) plugins: probing /usr/lib/pidgin/nautilus.so
(01:52:41) plugins: probing /usr/lib/pidgin/history.so
(01:52:41) plugins: probing /usr/lib/pidgin/cap.so
(01:52:41) plugins: probing /usr/lib/pidgin/timestamp.so
(01:52:41) plugins: probing /usr/lib/pidgin/musicmessaging.so
(01:52:41) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(01:52:41) plugins: probing /usr/lib/pidgin/spellchk.so
(01:52:41) plugins: probing /usr/lib/pidgin/timestamp_format.so
(01:52:41) plugins: probing /usr/lib/pidgin/notify.so
(01:52:41) plugins: probing /usr/lib/pidgin/xmppconsole.so
(01:52:41) plugins: probing /usr/lib/pidgin/gevolution.so
(01:52:42) plugins: probing /usr/lib/pidgin/markerline.so
(01:52:42) plugins: probing /usr/lib/pidgin/ticker.so
(01:52:42) plugins: probing /usr/lib/pidgin/pidginrc.so
(01:52:42) plugins: probing /usr/lib/pidgin/iconaway.so
(01:52:42) plugins: probing /usr/lib/pidgin/gestures.so
(01:52:42) plugins: probing /usr/lib/pidgin/convcolors.so
(01:52:42) plugins: probing /usr/lib/pidgin/extplacement.so
(01:52:42) plugins: probing /usr/lib/purple-2/libnovell.so
(01:52:42) plugins: probing /usr/lib/purple-2/tcl.so
(01:52:42) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtk8.4.so.0: cannot open shared object file: No such file or directory
(01:52:42) plugins: probing /usr/lib/purple-2/newline.so
(01:52:42) plugins: probing /usr/lib/purple-2/libirc.so
(01:52:42) plugins: probing /usr/lib/purple-2/libbonjour.so
(01:52:42) plugins: probing /usr/lib/purple-2/dbus-example.so
(01:52:42) plugins: probing /usr/lib/purple-2/joinpart.so
(01:52:42) plugins: probing /usr/lib/purple-2/libmyspace.so
(01:52:42) plugins: probing /usr/lib/purple-2/libgg.so
(01:52:42) plugins: probing /usr/lib/purple-2/buddynote.so
(01:52:42) plugins: probing /usr/lib/purple-2/psychic.so
(01:52:42) plugins: probing /usr/lib/purple-2/liboscar.so
(01:52:42) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(01:52:42) plugins: probing /usr/lib/purple-2/perl.so
(01:52:42) plugins: probing /usr/lib/purple-2/libsametime.so
(01:52:42) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(01:52:42) plugins: probing /usr/lib/purple-2/libxmpp.so
(01:52:42) util: Reading file xmpp-caps.xml from directory /home/element/.purple
(01:52:42) util: File /home/element/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(01:52:42) plugins: probing /usr/lib/purple-2/libjabber.so
(01:52:42) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(01:52:42) plugins: probing /usr/lib/purple-2/libqq.so
(01:52:42) plugins: probing /usr/lib/purple-2/libsimple.so
(01:52:42) plugins: probing /usr/lib/purple-2/idle.so
(01:52:42) plugins: probing /usr/lib/purple-2/libmsn.so
(01:52:42) plugins: probing /usr/lib/purple-2/offlinemsg.so
(01:52:42) plugins: probing /usr/lib/purple-2/libicq.so
(01:52:42) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(01:52:42) plugins: probing /usr/lib/purple-2/statenotify.so
(01:52:42) plugins: probing /usr/lib/purple-2/libyahoo.so
(01:52:42) plugins: probing /usr/lib/purple-2/log_reader.so
(01:52:42) plugins: probing /usr/lib/purple-2/autoaccept.so
(01:52:42) plugins: probing /usr/lib/purple-2/ssl.so
(01:52:42) plugins: probing /usr/lib/purple-2/libaim.so
(01:52:42) plugins: probing /usr/lib/purple-2/libzephyr.so
(01:52:42) plugins: probing /usr/lib/purple-2/ssl-nss.so
(01:52:42) prefs: /purple/status/scores/offline changed, scheduling save.
(01:52:42) prefs: /purple/status/scores/available changed, scheduling save.
(01:52:42) prefs: /purple/status/scores/invisible changed, scheduling save.
(01:52:42) prefs: /purple/status/scores/away changed, scheduling save.
(01:52:42) prefs: /purple/status/scores/extended_away changed, scheduling save.
(01:52:42) prefs: /purple/status/scores/idle changed, scheduling save.
(01:52:42) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(01:52:42) util: Reading file accounts.xml from directory /home/element/.purple
(01:52:42) util: File /home/element/.purple/accounts.xml does not exist (this is not necessarily an error)
(01:52:42) util: Reading file status.xml from directory /home/element/.purple
(01:52:42) certificate: CertificateVerifier x509, singleuse requested but not found.
(01:52:42) certificate: CertificateVerifier singleuse registered
(01:52:42) certificate: CertificatePool x509, ca requested but not found.
(01:52:42) certificate: CertificateScheme x509 requested but not found.
(01:52:42) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(01:52:42) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(01:52:42) certificate: CertificatePool ca registered
(01:52:42) certificate: CertificatePool x509, tls_peers requested but not found.
(01:52:42) certificate: CertificatePool tls_peers registered
(01:52:42) certificate: CertificateVerifier x509, tls_cached requested but not found.
(01:52:42) certificate: CertificateVerifier tls_cached registered
(01:52:42) prefs: /purple/logging/format changed, scheduling save.
(01:52:42) prefs: /purple/logging/format changed, scheduling save.
(01:52:42) prefs: /purple/proxy/type changed, scheduling save.
(01:52:42) prefs: /purple/proxy/host changed, scheduling save.
(01:52:42) prefs: /purple/proxy/port changed, scheduling save.
(01:52:42) prefs: /purple/proxy/username changed, scheduling save.
(01:52:42) prefs: /purple/proxy/password changed, scheduling save.
(01:52:42) certificate: CertificateScheme x509 requested but not found.
(01:52:42) certificate: CertificateScheme x509 registered
(01:52:42) stun: using server 
(01:52:42) sound: Initializing sound output drivers.
(01:52:42) prefs: /pidgin/conversations/placement changed, scheduling save.
(01:52:42) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(01:52:42) gtkblist: added visibility manager: 1
(01:52:42) docklet: created
(01:52:42) certificate: CertificateScheme x509 unregistered
(01:52:42) certificate: CertificateVerifier tls_cached unregistered
(01:52:42) certificate: CertificateVerifier singleuse unregistered
(01:52:42) certificate: CertificatePool tls_peers unregistered
(01:52:42) certificate: CertificatePool ca unregistered
(01:52:42) util: Writing file prefs.xml to directory /home/element/.purple
(01:52:42) util: Writing file /home/element/.purple/prefs.xml
(01:52:42) main: Unloading all plugins
(01:52:42) plugins: Unloading plugin GroupWise
(01:52:42) plugins: Unloading plugin IRC
(01:52:42) plugins: Unloading plugin Bonjour
(01:52:42) plugins: Unloading plugin MySpaceIM
(01:52:42) plugins: Unloading plugin Gadu-Gadu
(01:52:42) plugins: Unloading plugin Perl Plugin Loader
(01:52:42) plugins: Unloading plugin Sametime
(01:52:42) plugins: Unloading plugin XMPP
(01:52:42) plugins: Unloading plugin QQ
(01:52:42) plugins: Unloading plugin SIMPLE
(01:52:42) plugins: Unloading plugin MSN
(01:52:42) plugins: Unloading plugin ICQ
(01:52:42) plugins: Unloading plugin Yahoo
(01:52:42) plugins: Unloading plugin SSL
(01:52:42) plugins: Unloading plugin NSS
(01:52:42) certificate: CertificateScheme x509 unregistered
(01:52:42) plugins: Unloading plugin AIM
(01:52:42) plugins: Unloading plugin Zephyr
(01:52:42) accels: accel changed, scheduling save.
(01:52:42) accels: accel changed, scheduling save.
(01:52:42) accels: accel changed, scheduling save.
(01:52:42) accels: accel changed, scheduling save.
(01:52:42) accels: accel changed, scheduling save.
(01:52:42) accels: accel changed, scheduling save.
(01:52:42) gtkblist: removed visibility manager: 0
(01:52:42) docklet: destroyed
(01:52:42) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed
[/QUOTE]

---

### Post by click170 on 2008-01-12
I'm having the same problem.

Pidgin won't open as the regular user.  It will work if you run it as root with `sudo pidgin` but as was said, you'll have to enter your account info again.  And keep in mind, this could mean anybody else who uses the machine could use your accounts too if they use `sudo pidgin` as well?

I'm using Ubuntu 7.10, practically a fresh install as of a month.

Here is my debug output from pidgin, fetched with `pidgin -d > pidgin_debug.txt`


(17:23:32) prefs: Reading /home/user/.purple/prefs.xml
(17:23:32) prefs: Finished reading /home/user/.purple/prefs.xml
(17:23:32) dbus: okkk
(17:23:32) plugins: probing /usr/lib/pidgin/ticker.so
(17:23:32) plugins: probing /usr/lib/pidgin/musicmessaging.so
(17:23:32) plugins: probing /usr/lib/pidgin/iconaway.so
(17:23:32) plugins: probing /usr/lib/pidgin/markerline.so
(17:23:32) plugins: probing /usr/lib/pidgin/xmppconsole.so
(17:23:32) plugins: probing /usr/lib/pidgin/gestures.so
(17:23:32) plugins: probing /usr/lib/pidgin/nautilus.so
(17:23:32) plugins: probing /usr/lib/pidgin/timestamp_format.so
(17:23:32) plugins: probing /usr/lib/pidgin/extplacement.so
(17:23:32) plugins: probing /usr/lib/pidgin/notify.so
(17:23:32) plugins: probing /usr/lib/pidgin/spellchk.so
(17:23:32) plugins: probing /usr/lib/pidgin/timestamp.so
(17:23:32) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(17:23:32) plugins: probing /usr/lib/pidgin/gevolution.so
(17:23:32) plugins: probing /usr/lib/pidgin/history.so
(17:23:32) plugins: probing /usr/lib/pidgin/pidginrc.so
(17:23:32) plugins: probing /usr/lib/pidgin/convcolors.so
(17:23:32) plugins: probing /usr/lib/pidgin/cap.so
(17:23:32) plugins: probing /usr/lib/purple-2/libsimple.so
(17:23:32) plugins: probing /usr/lib/purple-2/log_reader.so
(17:23:32) plugins: probing /usr/lib/purple-2/libxmpp.so
(17:23:32) util: Reading file xmpp-caps.xml from directory /home/user/.purple
(17:23:32) util: File /home/user/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(17:23:32) plugins: probing /usr/lib/purple-2/joinpart.so
(17:23:32) plugins: probing /usr/lib/purple-2/newline.so
(17:23:32) plugins: probing /usr/lib/purple-2/ssl-nss.so
(17:23:32) plugins: probing /usr/lib/purple-2/libicq.so
(17:23:32) plugins: probing /usr/lib/purple-2/libirc.so
(17:23:32) plugins: probing /usr/lib/purple-2/libjabber.so
(17:23:32) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(17:23:32) plugins: probing /usr/lib/purple-2/libbonjour.so
(17:23:32) plugins: probing /usr/lib/purple-2/idle.so
(17:23:32) plugins: probing /usr/lib/purple-2/psychic.so
(17:23:32) plugins: probing /usr/lib/purple-2/buddynote.so
(17:23:32) plugins: probing /usr/lib/purple-2/perl.so
(17:23:32) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(17:23:32) plugins: probing /usr/lib/purple-2/libaim.so
(17:23:32) plugins: probing /usr/lib/purple-2/libgg.so
(17:23:32) plugins: probing /usr/lib/purple-2/autoaccept.so
(17:23:32) plugins: probing /usr/lib/purple-2/ssl.so
(17:23:32) plugins: probing /usr/lib/purple-2/libmsn.so
(17:23:32) plugins: probing /usr/lib/purple-2/tcl.so
(17:23:32) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(17:23:32) plugins: probing /usr/lib/purple-2/libqq.so
(17:23:32) plugins: probing /usr/lib/purple-2/offlinemsg.so
(17:23:32) plugins: probing /usr/lib/purple-2/libmyspace.so
(17:23:32) plugins: probing /usr/lib/purple-2/libnovell.so
(17:23:32) plugins: probing /usr/lib/purple-2/libzephyr.so
(17:23:32) plugins: probing /usr/lib/purple-2/libyahoo.so
(17:23:32) plugins: probing /usr/lib/purple-2/liboscar.so
(17:23:32) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(17:23:32) plugins: probing /usr/lib/purple-2/libsametime.so
(17:23:32) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(17:23:32) plugins: probing /usr/lib/purple-2/dbus-example.so
(17:23:32) plugins: probing /usr/lib/purple-2/statenotify.so
(17:23:32) prefs: /purple/status/scores/offline changed, scheduling save.
(17:23:32) prefs: /purple/status/scores/available changed, scheduling save.
(17:23:32) prefs: /purple/status/scores/invisible changed, scheduling save.
(17:23:32) prefs: /purple/status/scores/away changed, scheduling save.
(17:23:32) prefs: /purple/status/scores/extended_away changed, scheduling save.
(17:23:32) prefs: /purple/status/scores/idle changed, scheduling save.
(17:23:32) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(17:23:32) util: Reading file accounts.xml from directory /home/user/.purple
(17:23:32) util: Reading file status.xml from directory /home/user/.purple
(17:23:32) certificate: CertificateVerifier x509, singleuse requested but not found.
(17:23:32) certificate: CertificateVerifier singleuse registered
(17:23:32) certificate: CertificatePool x509, ca requested but not found.
(17:23:32) certificate: CertificateScheme x509 requested but not found.
(17:23:32) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(17:23:32) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(17:23:32) certificate: CertificatePool ca registered
(17:23:32) certificate: CertificatePool x509, tls_peers requested but not found.
(17:23:32) certificate: CertificatePool tls_peers registered
(17:23:32) certificate: CertificateVerifier x509, tls_cached requested but not found.
(17:23:32) certificate: CertificateVerifier tls_cached registered
(17:23:32) prefs: /purple/logging/format changed, scheduling save.
(17:23:32) prefs: /purple/logging/format changed, scheduling save.
(17:23:32) prefs: /purple/proxy/type changed, scheduling save.
(17:23:32) prefs: /purple/proxy/host changed, scheduling save.
(17:23:32) prefs: /purple/proxy/port changed, scheduling save.
(17:23:32) prefs: /purple/proxy/username changed, scheduling save.
(17:23:32) prefs: /purple/proxy/password changed, scheduling save.
(17:23:32) certificate: CertificateScheme x509 requested but not found.
(17:23:32) certificate: CertificateScheme x509 registered
(17:23:32) stun: using server 
(17:23:32) sound: Initializing sound output drivers.
(17:23:32) prefs: /pidgin/conversations/placement changed, scheduling save.
(17:23:32) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(17:23:32) gtkblist: added visibility manager: 1
(17:23:32) docklet: created
(17:23:32) blist: Attempted to save buddy list before it was read!
(17:23:32) certificate: CertificateScheme x509 unregistered
(17:23:32) certificate: CertificateVerifier tls_cached unregistered
(17:23:32) certificate: CertificateVerifier singleuse unregistered
(17:23:32) certificate: CertificatePool tls_peers unregistered
(17:23:32) certificate: CertificatePool ca unregistered
(17:23:32) util: Writing file accounts.xml to directory /home/user/.purple
(17:23:32) util: Writing file /home/user/.purple/accounts.xml
(17:23:32) util: Writing file prefs.xml to directory /home/user/.purple
(17:23:32) util: Writing file /home/user/.purple/prefs.xml
(17:23:32) main: Unloading all plugins
(17:23:32) plugins: Unloading plugin SIMPLE
(17:23:32) plugins: Unloading plugin XMPP
(17:23:32) plugins: Unloading plugin NSS
(17:23:32) certificate: CertificateScheme x509 unregistered
(17:23:32) plugins: Unloading plugin ICQ
(17:23:32) plugins: Unloading plugin IRC
(17:23:32) plugins: Unloading plugin Bonjour
(17:23:32) plugins: Unloading plugin Perl Plugin Loader
(17:23:32) plugins: Unloading plugin AIM
(17:23:32) plugins: Unloading plugin Gadu-Gadu
(17:23:32) plugins: Unloading plugin SSL
(17:23:32) plugins: Unloading plugin MSN
(17:23:32) plugins: Unloading plugin QQ
(17:23:32) plugins: Unloading plugin MySpaceIM
(17:23:32) plugins: Unloading plugin GroupWise
(17:23:32) plugins: Unloading plugin Zephyr
(17:23:32) plugins: Unloading plugin Yahoo
(17:23:32) plugins: Unloading plugin Sametime
(17:23:32) accels: accel changed, scheduling save.
(17:23:32) accels: accel changed, scheduling save.
(17:23:32) accels: accel changed, scheduling save.
(17:23:32) accels: accel changed, scheduling save.
(17:23:32) accels: accel changed, scheduling save.
(17:23:32) accels: accel changed, scheduling save.
(17:23:32) gtkblist: removed visibility manager: 0
(17:23:32) docklet: destroyed
(17:23:32) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed

Edit -   I've tried completely removing, and then reinstalling pidgin and it doesn't seem to have had any affect.

---

### Post by windyclark on 2008-01-17
I also am having the same problem.  It seemed to stop working after an update. And I also did
a reinstall with no success.  I am running an up-to-date 7.10.
Here is my output from an attempt to launch from a terminal:

$ pidgin --debug
(21:17:39) prefs: Reading /home/mclark/.purple/prefs.xml
(21:17:39) prefs: Finished reading /home/mclark/.purple/prefs.xml
(21:17:39) dbus: okkk
(21:17:39) plugins: probing /usr/lib/pidgin/gevolution.so
(21:17:39) plugins: probing /usr/lib/pidgin/nautilus.so
(21:17:39) plugins: probing /usr/lib/pidgin/cap.so
(21:17:39) plugins: probing /usr/lib/pidgin/gestures.so
(21:17:39) plugins: probing /usr/lib/pidgin/musicmessaging.so
(21:17:39) plugins: probing /usr/lib/pidgin/ticker.so
(21:17:39) plugins: probing /usr/lib/pidgin/convcolors.so
(21:17:39) plugins: probing /usr/lib/pidgin/extplacement.so
(21:17:39) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(21:17:39) plugins: probing /usr/lib/pidgin/history.so
(21:17:39) plugins: probing /usr/lib/pidgin/iconaway.so
(21:17:39) plugins: probing /usr/lib/pidgin/markerline.so
(21:17:39) plugins: probing /usr/lib/pidgin/notify.so
(21:17:39) plugins: probing /usr/lib/pidgin/pidginrc.so
(21:17:39) plugins: probing /usr/lib/pidgin/spellchk.so
(21:17:39) plugins: probing /usr/lib/pidgin/timestamp.so
(21:17:39) plugins: probing /usr/lib/pidgin/timestamp_format.so
(21:17:39) plugins: probing /usr/lib/pidgin/xmppconsole.so
(21:17:39) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(21:17:39) plugins: probing /usr/lib/purple-2/perl.so
(21:17:39) plugins: probing /usr/lib/purple-2/ssl.so
(21:17:39) plugins: probing /usr/lib/purple-2/autoaccept.so
(21:17:39) plugins: probing /usr/lib/purple-2/ssl-nss.so
(21:17:39) plugins: probing /usr/lib/purple-2/tcl.so
(21:17:39) plugins: probing /usr/lib/purple-2/buddynote.so
(21:17:39) plugins: probing /usr/lib/purple-2/idle.so
(21:17:39) plugins: probing /usr/lib/purple-2/joinpart.so
(21:17:39) plugins: probing /usr/lib/purple-2/log_reader.so
(21:17:39) plugins: probing /usr/lib/purple-2/newline.so
(21:17:39) plugins: probing /usr/lib/purple-2/offlinemsg.so
(21:17:39) plugins: probing /usr/lib/purple-2/psychic.so
(21:17:39) plugins: probing /usr/lib/purple-2/statenotify.so
(21:17:39) plugins: probing /usr/lib/purple-2/dbus-example.so
(21:17:39) plugins: probing /usr/lib/purple-2/libbonjour.so
(21:17:39) plugins: probing /usr/lib/purple-2/libgg.so
(21:17:39) plugins: probing /usr/lib/purple-2/libirc.so
(21:17:39) plugins: probing /usr/lib/purple-2/libmyspace.so
(21:17:39) plugins: probing /usr/lib/purple-2/libxmpp.so
(21:17:39) util: Reading file xmpp-caps.xml from directory /home/mclark/.purple
(21:17:39) util: File /home/mclark/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(21:17:39) plugins: probing /usr/lib/purple-2/libmsn.so
(21:17:39) plugins: probing /usr/lib/purple-2/libnovell.so
(21:17:39) plugins: probing /usr/lib/purple-2/libsametime.so
(21:17:39) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(21:17:39) plugins: probing /usr/lib/purple-2/libaim.so
(21:17:39) plugins: probing /usr/lib/purple-2/libicq.so
(21:17:39) plugins: probing /usr/lib/purple-2/libqq.so
(21:17:39) plugins: probing /usr/lib/purple-2/libsimple.so
(21:17:39) plugins: probing /usr/lib/purple-2/libyahoo.so
(21:17:39) plugins: probing /usr/lib/purple-2/libzephyr.so
(21:17:39) plugins: probing /usr/lib/purple-2/libjabber.so
(21:17:39) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(21:17:39) plugins: probing /usr/lib/purple-2/liboscar.so
(21:17:39) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(21:17:39) prefs: /purple/status/scores/offline changed, scheduling save.
(21:17:39) prefs: /purple/status/scores/available changed, scheduling save.
(21:17:39) prefs: /purple/status/scores/invisible changed, scheduling save.
(21:17:39) prefs: /purple/status/scores/away changed, scheduling save.
(21:17:39) prefs: /purple/status/scores/extended_away changed, scheduling save.
(21:17:39) prefs: /purple/status/scores/idle changed, scheduling save.
(21:17:39) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(21:17:39) util: Reading file accounts.xml from directory /home/mclark/.purple
(21:17:39) util: Reading file status.xml from directory /home/mclark/.purple
(21:17:39) certificate: CertificateVerifier x509, singleuse requested but not found.
(21:17:39) certificate: CertificateVerifier singleuse registered
(21:17:39) certificate: CertificatePool x509, ca requested but not found.
(21:17:39) certificate: CertificateScheme x509 requested but not found.
(21:17:39) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(21:17:39) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(21:17:39) certificate: CertificatePool ca registered
(21:17:39) certificate: CertificatePool x509, tls_peers requested but not found.
(21:17:39) certificate: CertificatePool tls_peers registered
(21:17:39) certificate: CertificateVerifier x509, tls_cached requested but not found.
(21:17:39) certificate: CertificateVerifier tls_cached registered
(21:17:39) prefs: /purple/logging/format changed, scheduling save.
(21:17:39) prefs: /purple/logging/format changed, scheduling save.
(21:17:39) prefs: /purple/proxy/type changed, scheduling save.
(21:17:39) prefs: /purple/proxy/host changed, scheduling save.
(21:17:39) prefs: /purple/proxy/port changed, scheduling save.
(21:17:39) prefs: /purple/proxy/username changed, scheduling save.
(21:17:39) prefs: /purple/proxy/password changed, scheduling save.
(21:17:39) certificate: CertificateScheme x509 requested but not found.
(21:17:39) certificate: CertificateScheme x509 registered
(21:17:39) stun: using server 
(21:17:39) sound: Initializing sound output drivers.
(21:17:40) prefs: /pidgin/conversations/placement changed, scheduling save.
(21:17:40) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(21:17:40) gtkblist: added visibility manager: 1
(21:17:40) docklet: created
(21:17:40) blist: Attempted to save buddy list before it was read!
(21:17:40) certificate: CertificateScheme x509 unregistered
(21:17:40) certificate: CertificateVerifier tls_cached unregistered
(21:17:40) certificate: CertificateVerifier singleuse unregistered
(21:17:40) certificate: CertificatePool tls_peers unregistered
(21:17:40) certificate: CertificatePool ca unregistered
(21:17:40) util: Writing file accounts.xml to directory /home/mclark/.purple
(21:17:40) util: Writing file /home/mclark/.purple/accounts.xml
(21:17:40) util: Writing file status.xml to directory /home/mclark/.purple
(21:17:40) util: Writing file /home/mclark/.purple/status.xml
(21:17:40) util: Writing file prefs.xml to directory /home/mclark/.purple
(21:17:40) util: Writing file /home/mclark/.purple/prefs.xml
(21:17:40) main: Unloading all plugins
(21:17:40) plugins: Unloading plugin Perl Plugin Loader
(21:17:40) plugins: Unloading plugin SSL
(21:17:40) plugins: Unloading plugin NSS
(21:17:40) certificate: CertificateScheme x509 unregistered
(21:17:40) plugins: Unloading plugin Tcl Plugin Loader
(21:17:40) plugins: Unloading plugin Bonjour
(21:17:40) plugins: Unloading plugin Gadu-Gadu
(21:17:40) plugins: Unloading plugin IRC
(21:17:40) plugins: Unloading plugin MySpaceIM
(21:17:40) plugins: Unloading plugin XMPP
(21:17:40) plugins: Unloading plugin MSN
(21:17:40) plugins: Unloading plugin GroupWise
(21:17:40) plugins: Unloading plugin Sametime
(21:17:40) plugins: Unloading plugin AIM
(21:17:40) plugins: Unloading plugin ICQ
(21:17:40) plugins: Unloading plugin QQ
(21:17:40) plugins: Unloading plugin SIMPLE
(21:17:40) plugins: Unloading plugin Yahoo
(21:17:40) plugins: Unloading plugin Zephyr
(21:17:40) accels: accel changed, scheduling save.
(21:17:40) accels: accel changed, scheduling save.
(21:17:40) accels: accel changed, scheduling save.
(21:17:40) accels: accel changed, scheduling save.
(21:17:40) accels: accel changed, scheduling save.
(21:17:40) accels: accel changed, scheduling save.
(21:17:40) gtkblist: removed visibility manager: 0
(21:17:40) docklet: destroyed
(21:17:40) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed
$ 

Has anybody solved this?

---

### Post by nikoPSK on 2008-01-17
Well, try reinstalling it. :)

---

### Post by coolbrook on 2008-01-17
> **DutyDuty said:**
> Try updating

I agree with this and recommended upgrading to 2.3.1 especially if you were experiencing timeouts and sent messages bouncing back to you.  The upgrade seems to have resolved my problem.

---

### Post by windyclark on 2008-01-18
Ummm, I previously reinstalled with no luck and now i have downloaded source (2.3.1) and rebuilt
and I get essentially the same behavior (I will not include the debug output this time unless someone
out there can interpret it, but I believe it is the same as what I go with the earlier verson of pidgin).
I might add I am a little disappointed the solutions had to do with downloading non-ubuntu packages
since that is the reason I switched over to ubuntu.  Anyway, fun and games, any of the others
experiencing this behavior had any luck?

---

### Post by aBitLater on 2008-01-18
see if it's "minimized" on your menu panel (by the clock).

---

### Post by windyclark on 2008-01-19
In regards to it may have worked, but is minimized:
No, because I can run it in a terminal with the debug flag on and see it fail
(also see my earlier posts),, i.e.,

$ which pidgin
/usr/local/bin/pidgin
$ pidgin -v
Pidgin 2.3.1
$ pidgin --debug
(08:25:37) prefs: Reading /home/mclark/.purple/prefs.xml
(08:25:37) prefs: Finished reading /home/mclark/.purple/prefs.xml
(08:25:37) dbus: okkk

etc

(08:25:38) accels: accel changed, scheduling save.
(08:25:38) gtkblist: removed visibility manager: 0
(08:25:38) docklet: destroyed
(08:25:38) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed
$ 


The outputs from the debug that look like trouble are:

(08:25:37) plugins: /usr/local/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?

(08:25:37) plugins: /usr/local/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?

(08:25:37) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.

(08:25:38) main: exiting because another libpurple client is already running


Am I on the wrong forum for someone to interpret this, is there somewhere else I
should be bringing this up.?  I am getting pressure from my family to go to
Windows and this is my first foray into the community, am I approaching this
wrong?

Thanks in advance.

---

### Post by windyclark on 2008-01-19
Wow, egg on my face, it WAS minimized on the tool bar.  Don't know how I missed that.
Many thanks, to all that helped.  Please ignore my last reply.  Thanks again.

---

### Post by nikoPSK on 2008-01-19
no problem, hehe. :p Glad you got it fixed.

---

### Post by click170 on 2008-01-19
Hey all,

after leaving the problem alone for awhile and then eventually doing a `sudo apt-get dist-upgrade` it finally worked.

No idea what caused it, if it will happen again, or anything, but hey at least it's fixed!

Thanks all.


Edit - Also, note that I did a dist-upgrade prior to waiting as well and that did not solve the problem at the time.  Something must have been changed/released/upgraded within that time frame to fix it.

---

### Post by nikoPSK on 2008-01-20
no problem, please mark this thread as "SOLVED". :)
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

nikoPSK

---

### Post by makepeace2000 on 2008-01-21
To ABitLater- I never actually noticed that it was minimized next to the clock. Always wondered why it seemed to work intermittently. I'm now ( if I wasn't before) officially an idiot.   :)

Thanks-

John

---

### Post by aBitLater on 2008-01-22
> **makepeace2000 said:**
> To ABitLater- I never actually noticed that it was minimized next to the clock. Always wondered why it seemed to work intermittently. I'm now ( if I wasn't before) officially an idiot.   :)

Thanks-

John

your welcome John :)

---

