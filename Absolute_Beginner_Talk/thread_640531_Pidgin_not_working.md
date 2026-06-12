---
title: "Pidgin not working"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by killertomato94 on 2007-12-14
When I try to start pidgin it will say that it's starting and then nothing ever happens. I removed and re-added it but it still doesn't work. Here's the code


dixie@dixie-desktop:~$ pidgin -d
(10:35:16) prefs: Reading /home/dixie/.purple/prefs.xml
(10:35:16) prefs: Finished reading /home/dixie/.purple/prefs.xml
(10:35:16) dbus: okkk
(10:35:16) plugins: probing /usr/lib/pidgin/history.so
(10:35:16) plugins: probing /usr/lib/pidgin/musicmessaging.so
(10:35:16) plugins: probing /usr/lib/pidgin/iconaway.so
(10:35:16) plugins: probing /usr/lib/pidgin/spellchk.so
(10:35:16) plugins: probing /usr/lib/pidgin/extplacement.so
(10:35:16) plugins: probing /usr/lib/pidgin/timestamp_format.so
(10:35:16) plugins: probing /usr/lib/pidgin/timestamp.so
(10:35:16) plugins: probing /usr/lib/pidgin/pidginrc.so
(10:35:16) plugins: probing /usr/lib/pidgin/gevolution.so
(10:35:16) plugins: probing /usr/lib/pidgin/notify.so
(10:35:16) plugins: probing /usr/lib/pidgin/xmppconsole.so
(10:35:16) plugins: probing /usr/lib/pidgin/markerline.so
(10:35:16) plugins: probing /usr/lib/pidgin/nautilus.so
(10:35:16) plugins: probing /usr/lib/pidgin/ticker.so
(10:35:16) plugins: probing /usr/lib/pidgin/cap.so
(10:35:16) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(10:35:16) plugins: probing /usr/lib/pidgin/gestures.so
(10:35:16) plugins: probing /usr/lib/pidgin/convcolors.so
(10:35:16) plugins: probing /usr/lib/purple-2/newline.so
(10:35:16) plugins: probing /usr/lib/purple-2/idle.so
(10:35:16) plugins: probing /usr/lib/purple-2/buddynote.so
(10:35:16) plugins: probing /usr/lib/purple-2/autoaccept.so
(10:35:16) plugins: probing /usr/lib/purple-2/libqq.so
(10:35:16) plugins: probing /usr/lib/purple-2/statenotify.so
(10:35:16) plugins: probing /usr/lib/purple-2/perl.so
(10:35:16) plugins: probing /usr/lib/purple-2/joinpart.so
(10:35:16) plugins: probing /usr/lib/purple-2/libirc.so
(10:35:16) plugins: probing /usr/lib/purple-2/libmsn.so
(10:35:16) plugins: probing /usr/lib/purple-2/ssl.so
(10:35:16) plugins: probing /usr/lib/purple-2/log_reader.so
(10:35:16) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(10:35:16) plugins: probing /usr/lib/purple-2/libgg.so
(10:35:16) plugins: probing /usr/lib/purple-2/libzephyr.so
(10:35:17) plugins: probing /usr/lib/purple-2/tcl.so
(10:35:17) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(10:35:17) plugins: probing /usr/lib/purple-2/libicq.so
(10:35:17) plugins: probing /usr/lib/purple-2/libmyspace.so
(10:35:17) plugins: probing /usr/lib/purple-2/libsimple.so
(10:35:17) plugins: probing /usr/lib/purple-2/liboscar.so
(10:35:17) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(10:35:17) plugins: probing /usr/lib/purple-2/libyahoo.so
(10:35:17) plugins: probing /usr/lib/purple-2/libsametime.so
(10:35:17) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(10:35:17) plugins: probing /usr/lib/purple-2/ssl-nss.so
(10:35:17) plugins: probing /usr/lib/purple-2/libnovell.so
(10:35:17) plugins: probing /usr/lib/purple-2/libjabber.so
(10:35:17) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(10:35:17) plugins: probing /usr/lib/purple-2/libaim.so
(10:35:17) plugins: probing /usr/lib/purple-2/psychic.so
(10:35:17) plugins: probing /usr/lib/purple-2/dbus-example.so
(10:35:17) plugins: probing /usr/lib/purple-2/libbonjour.so
(10:35:17) plugins: probing /usr/lib/purple-2/libxmpp.so
(10:35:17) util: Reading file xmpp-caps.xml from directory /home/dixie/.purple
(10:35:17) util: File /home/dixie/.purple/xmpp-caps.xml does not exist (this is not necessarily an error)
(10:35:17) plugins: probing /usr/lib/purple-2/offlinemsg.so
(10:35:17) prefs: /purple/status/scores/offline changed, scheduling save.
(10:35:17) prefs: /purple/status/scores/available changed, scheduling save.
(10:35:17) prefs: /purple/status/scores/invisible changed, scheduling save.
(10:35:17) prefs: /purple/status/scores/away changed, scheduling save.
(10:35:17) prefs: /purple/status/scores/extended_away changed, scheduling save.
(10:35:17) prefs: /purple/status/scores/idle changed, scheduling save.
(10:35:17) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(10:35:17) util: Reading file accounts.xml from directory /home/dixie/.purple
(10:35:17) util: Reading file status.xml from directory /home/dixie/.purple
(10:35:17) certificate: CertificateVerifier x509, singleuse requested but not found.
(10:35:17) certificate: CertificateVerifier singleuse registered
(10:35:17) certificate: CertificatePool x509, ca requested but not found.
(10:35:17) certificate: CertificateScheme x509 requested but not found.
(10:35:17) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(10:35:17) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(10:35:17) certificate: CertificatePool ca registered
(10:35:17) certificate: CertificatePool x509, tls_peers requested but not found.
(10:35:17) certificate: CertificatePool tls_peers registered
(10:35:17) certificate: CertificateVerifier x509, tls_cached requested but not found.
(10:35:17) certificate: CertificateVerifier tls_cached registered
(10:35:17) prefs: /purple/logging/format changed, scheduling save.
(10:35:17) prefs: /purple/logging/format changed, scheduling save.
(10:35:17) prefs: /purple/proxy/type changed, scheduling save.
(10:35:17) prefs: /purple/proxy/host changed, scheduling save.
(10:35:17) prefs: /purple/proxy/port changed, scheduling save.
(10:35:17) prefs: /purple/proxy/username changed, scheduling save.
(10:35:17) prefs: /purple/proxy/password changed, scheduling save.
(10:35:17) certificate: CertificateScheme x509 requested but not found.
(10:35:17) certificate: CertificateScheme x509 registered
(10:35:17) stun: using server 
(10:35:17) sound: Initializing sound output drivers.
(10:35:17) prefs: /pidgin/conversations/placement changed, scheduling save.
(10:35:17) prefs: purple_prefs_connect_callback: Unknown pref /pidgin/conversations/im/show_protocol_icons
(10:35:17) gtkblist: added visibility manager: 1
(10:35:17) docklet: created
(10:35:17) blist: Attempted to save buddy list before it was read!
(10:35:17) certificate: CertificateScheme x509 unregistered
(10:35:17) certificate: CertificateVerifier tls_cached unregistered
(10:35:17) certificate: CertificateVerifier singleuse unregistered
(10:35:17) certificate: CertificatePool tls_peers unregistered
(10:35:17) certificate: CertificatePool ca unregistered
(10:35:17) util: Writing file accounts.xml to directory /home/dixie/.purple
(10:35:17) util: Writing file /home/dixie/.purple/accounts.xml
(10:35:17) util: Writing file prefs.xml to directory /home/dixie/.purple
(10:35:17) util: Writing file /home/dixie/.purple/prefs.xml
(10:35:17) main: Unloading all plugins
(10:35:17) plugins: Unloading plugin QQ
(10:35:17) plugins: Unloading plugin Perl Plugin Loader
(10:35:17) plugins: Unloading plugin IRC
(10:35:17) plugins: Unloading plugin MSN
(10:35:17) plugins: Unloading plugin SSL
(10:35:17) plugins: Unloading plugin NSS
(10:35:17) certificate: CertificateScheme x509 unregistered
(10:35:17) plugins: Unloading plugin Gadu-Gadu
(10:35:17) plugins: Unloading plugin Zephyr
(10:35:17) plugins: Unloading plugin ICQ
(10:35:17) plugins: Unloading plugin MySpaceIM
(10:35:17) plugins: Unloading plugin SIMPLE
(10:35:17) plugins: Unloading plugin Yahoo
(10:35:17) plugins: Unloading plugin Sametime
(10:35:17) plugins: Unloading plugin GroupWise
(10:35:17) plugins: Unloading plugin AIM
(10:35:17) plugins: Unloading plugin Bonjour
(10:35:17) plugins: Unloading plugin XMPP
(10:35:17) accels: accel changed, scheduling save.
(10:35:17) accels: accel changed, scheduling save.
(10:35:17) accels: accel changed, scheduling save.
(10:35:17) accels: accel changed, scheduling save.
(10:35:17) accels: accel changed, scheduling save.
(10:35:17) accels: accel changed, scheduling save.
(10:35:17) gtkblist: removed visibility manager: 0
(10:35:17) docklet: destroyed
(10:35:17) Gtk: gtk_main_quit: assertion `main_loops != NULL' failed
dixie@dixie-desktop:~$


Another user had the same post and he said that he deleted the xml files and I have no idea how or where to do that. I've tried searching for the .purple file and it never comes up. Please help!

---

### Post by hfranco on 2007-12-14
Remove pidgin and install it from source.

[http://www.pidgin.im/download/]("http://www.pidgin.im/download/")

---

### Post by killertomato94 on 2007-12-14
i've tried that and it doesn't work. How do I delete the xml files?

---

### Post by trentlarson on 2008-01-03
You should see a ~/.purple directory containing the Pidgin files, so you can delete all that:
rm -rf ~/.purple

I had this same problem, but I missed one detail after trying these fixes: I actually had a pidgin process running, and I finally noticed that there was already an icon in my toolbar, and so it would always exit immediately.  Once I shut that down it now works great... at least it starts great, and I have to figure out how to import my Gaim settings.

---

