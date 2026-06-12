---
title: "[SOLVED] Pidgin, Gaim, AMSN and others; all unable to connect"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by very_japi on 2007-09-02
Reading some of the threads out there where similar problems are published was not very useful.

The problem is that i can't connect to MSN-messenger (or any Instant mesenger), using any client. i always get the error: > Connection error from Notification server

I tried eliminating my router's IP from my DNS list on my network settings (which worked for some people). And every other thread was about proxys, and i am not using a proxy.

I have a DSL connection, i connect using DHCP and a router and i am able to surf the web. The first week i used ubuntu i was able to connect using Gaim, For some reason i reinstalled Ubuntu, and now i cant connect. I tried reinstalling over and over,

I am able to connect Using Weendows using The official messenger client, but i am not so lucky in Ubuntu.  

So when im workng i have two laptops, one with my actual work (Ubuntu) and another one with Messenger (Weendows)


this is my debug from pdging:
```
(00:48:52) dbus: okkk
(00:48:52) plugins: probing /usr/lib/pidgin/gestures.so
(00:48:52) plugins: probing /usr/lib/pidgin/pidginrc.so
(00:48:52) plugins: probing /usr/lib/pidgin/timestamp.so
(00:48:52) plugins: probing /usr/lib/pidgin/convcolors.so
(00:48:52) plugins: probing /usr/lib/pidgin/history.so
(00:48:52) plugins: probing /usr/lib/pidgin/markerline.so
(00:48:52) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(00:48:52) plugins: probing /usr/lib/pidgin/timestamp_format.so
(00:48:52) plugins: probing /usr/lib/pidgin/gevolution.so
(00:48:52) plugins: probing /usr/lib/pidgin/spellchk.so
(00:48:52) plugins: probing /usr/lib/pidgin/notify.so
(00:48:53) plugins: probing /usr/lib/pidgin/musicmessaging.so
(00:48:53) plugins: probing /usr/lib/pidgin/extplacement.so
(00:48:53) plugins: probing /usr/lib/pidgin/iconaway.so
(00:48:53) plugins: probing /usr/lib/pidgin/xmppconsole.so
(00:48:53) plugins: probing /usr/lib/pidgin/ticker.so
(00:48:53) plugins: probing /usr/lib/purple-2/idle.so
(00:48:53) plugins: probing /usr/lib/purple-2/autoaccept.so
(00:48:53) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(00:48:53) plugins: probing /usr/lib/purple-2/libicq.so
(00:48:53) plugins: probing /usr/lib/purple-2/tcl.so
(00:48:53) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(00:48:53) plugins: probing /usr/lib/purple-2/libirc.so
(00:48:53) plugins: probing /usr/lib/purple-2/ssl.so
(00:48:53) plugins: probing /usr/lib/purple-2/ssl-nss.so
(00:48:53) plugins: probing /usr/lib/purple-2/dbus-example.so
(00:48:53) plugins: probing /usr/lib/purple-2/libbonjour.so
(00:48:53) plugins: probing /usr/lib/purple-2/joinpart.so
(00:48:53) plugins: probing /usr/lib/purple-2/statenotify.so
(00:48:53) plugins: probing /usr/lib/purple-2/libsametime.so
(00:48:53) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(00:48:53) plugins: probing /usr/lib/purple-2/libyahoo.so
(00:48:53) plugins: probing /usr/lib/purple-2/libmsn.so
(00:48:53) plugins: probing /usr/lib/purple-2/libsimple.so
(00:48:53) plugins: probing /usr/lib/purple-2/libaim.so
(00:48:53) plugins: probing /usr/lib/purple-2/buddynote.so
(00:48:53) plugins: probing /usr/lib/purple-2/newline.so
(00:48:53) plugins: probing /usr/lib/purple-2/perl.so
(00:48:53) plugins: probing /usr/lib/purple-2/libgg.so
(00:48:53) plugins: probing /usr/lib/purple-2/libqq.so
(00:48:53) plugins: probing /usr/lib/purple-2/offlinemsg.so
(00:48:53) plugins: probing /usr/lib/purple-2/liboscar.so
(00:48:53) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(00:48:53) plugins: probing /usr/lib/purple-2/psychic.so
(00:48:53) plugins: probing /usr/lib/purple-2/log_reader.so
(00:48:53) plugins: probing /usr/lib/purple-2/libxmpp.so
(00:48:53) plugins: probing /usr/lib/purple-2/libzephyr.so
(00:48:53) plugins: probing /usr/lib/purple-2/libjabber.so
(00:48:53) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(00:48:53) plugins: probing /usr/lib/purple-2/libnovell.so
(00:48:53) util: Reading file accounts.xml from directory /home/japi/.purple
(00:48:53) util: Reading file status.xml from directory /home/japi/.purple
(00:48:53) sound: Initializing sound output drivers.
(00:48:53) GdkPixbuf: gdk_pixbuf_get_has_alpha: assertion `pixbuf != NULL' failed
(00:48:53) Gtk: Useless empty GtkIconSource
(00:48:53) GLib-GObject: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(00:48:53) gtkblist: added visibility manager: 1
(00:48:53) docklet: created
(00:48:53) util: Reading file blist.xml from directory /home/japi/.purple
(00:48:53) prefs: Reading /home/japi/.purple/prefs.xml
(00:48:53) prefs: Finished reading /home/japi/.purple/prefs.xml
(00:48:53) plugins: Unable to find saved plugin /usr/lib/gaim/docklet.so
(00:48:53) plugins: Loading saved plugin /usr/lib/pidgin/notify.so
(00:48:53) pounce: Error reading pounces: Failed to open file '/home/japi/.purple/pounces.xml': No such file or directory
(00:48:53) stun: using server 
(00:48:53) Session Management: ICE initialized.
(00:48:53) Session Management: Connecting with no previous ID
(00:48:53) Session Management: Handling new ICE connection... (00:48:53) done.
(00:48:53) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000118871213300000057640018
(00:48:53) Session Management: Using pidgin as command
(00:48:53) gtkspell: Failed to setup GtkSpell: aspell: No word lists can be found for the language "en_US".
(00:48:53) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(00:48:53) dbus: The signal "gtkblist-hiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(00:48:53) account: Connecting to account uniguei@hotmail.com
(00:48:53) connection: Connecting. gc = 0xdd75a0
(00:48:53) msn: new httpconn (0xdf0740)
(00:48:53) dns: DNS query for 'messenger.hotmail.com' queued
(00:48:53) account: Connecting to account me.so.japi@gmail.com/Home
(00:48:53) connection: Connecting. gc = 0xdf0d40
(00:48:53) dns: DNS query for 'talk.google.com' queued
(00:48:53) account: Connecting to account kaworu_ta_happy@hotmail.com
(00:48:53) connection: Connecting. gc = 0xdf1580
(00:48:53) msn: new httpconn (0xdf1200)
(00:48:53) dns: DNS query for 'messenger.hotmail.com' queued
(00:48:53) Session Management: Received first save_yourself
(00:48:53) dns: Created new DNS child 7480, there are now 1 children.
(00:48:53) dns: Successfully sent DNS request to child 7480
(00:48:53) dns: Created new DNS child 7481, there are now 2 children.
(00:48:53) dns: Successfully sent DNS request to child 7481
(00:48:53) dns: Created new DNS child 7482, there are now 3 children.
(00:48:53) dns: Successfully sent DNS request to child 7482
(00:48:53) Session Management: Received save_complete
(00:48:53) docklet: embedded
(00:48:53) network: Entering nm_callback_func!
(00:48:53) dns: Got response for 'messenger.hotmail.com'
(00:48:53) dnsquery: IP resolved for messenger.hotmail.com
(00:48:53) proxy: Attempting connection to 65.54.239.80
(00:48:53) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(00:48:53) proxy: Connection in progress
(00:48:53) proxy: Connected to messenger.hotmail.com:1863.
(00:48:53) proxy: Error connecting to messenger.hotmail.com:1863 (Connection refused).
(00:48:53) proxy: Connection attempt failed: Connection refused
(00:48:53) msn: Connection error: Connection refused
(00:48:53) msn: Connection error from Notification server (messenger.hotmail.com): Unable to connect
(00:48:53) account: Disconnecting account 0x74ecb0
(00:48:53) connection: Disconnecting connection 0xdd75a0
(00:48:53) msn: destroy httpconn (0xdf0740)
(00:48:53) connection: Destroying connection 0xdd75a0
(00:48:58) util: Writing file accounts.xml to directory /home/japi/.purple
(00:48:58) util: Writing file blist.xml to directory /home/japi/.purple
(00:48:58) util: Writing file status.xml to directory /home/japi/.purple
dns[7481] Error: getaddrinfo returned -2
(00:49:03) dns: Got response for 'talk.google.com'
(00:49:03) dnsquery: Error resolving talk.google.com:
Name or service not known
(00:49:03) proxy: Connection attempt failed: Error resolving talk.google.com:
Name or service not known
(00:49:03) account: Disconnecting account 0x74aab0
(00:49:03) connection: Disconnecting connection 0xdf0d40
(00:49:03) connection: Destroying connection 0xdf0d40
dns[7482] Error: getaddrinfo returned -2
(00:49:03) dns: Got response for 'messenger.hotmail.com'
(00:49:03) dnsquery: Error resolving messenger.hotmail.com:
Name or service not known
(00:49:03) proxy: Connection attempt failed: Error resolving messenger.hotmail.com:
Name or service not known
(00:49:03) msn: Connection error: Error resolving messenger.hotmail.com:
Name or service not known
(00:49:03) msn: Connection error from Notification server (messenger.hotmail.com): Unable to connect
(00:49:03) account: Disconnecting account 0x74e030
(00:49:03) connection: Disconnecting connection 0xdf1580
(00:49:03) msn: destroy httpconn (0xdf1200)
(00:49:03) connection: Destroying connection 0xdf1580
(00:49:09) util: Writing file accounts.xml to directory /home/japi/.purple

```
Is there something that i am overlooking?

any suggestions?

---

### Post by Crafty Kisses on 2007-09-02
> **very_japi said:**
> Reading some of the threads out there where similar problems are published was not very useful.

The problem is that i can't connect to MSN-messenger (or any Instant mesenger), using any client. i always get the error: 

I tried eliminating my router's IP from my DNS list on my network settings (which worked for some people). And every other thread was about proxys, and i am not using a proxy.

I have a DSL connection, i connect using DHCP and a router and i am able to surf the web. The first week i used ubuntu i was able to connect using Gaim, For some reason i reinstalled Ubuntu, and now i cant connect. I tried reinstalling over and over,

I am able to connect Using Weendows using The official messenger client, but i am not so lucky in Ubuntu.  

So when im workng i have two laptops, one with my actual work (Ubuntu) and another one with Messenger (Weendows)


this is my debug from pdging:
```
(00:48:52) dbus: okkk
(00:48:52) plugins: probing /usr/lib/pidgin/gestures.so
(00:48:52) plugins: probing /usr/lib/pidgin/pidginrc.so
(00:48:52) plugins: probing /usr/lib/pidgin/timestamp.so
(00:48:52) plugins: probing /usr/lib/pidgin/convcolors.so
(00:48:52) plugins: probing /usr/lib/pidgin/history.so
(00:48:52) plugins: probing /usr/lib/pidgin/markerline.so
(00:48:52) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(00:48:52) plugins: probing /usr/lib/pidgin/timestamp_format.so
(00:48:52) plugins: probing /usr/lib/pidgin/gevolution.so
(00:48:52) plugins: probing /usr/lib/pidgin/spellchk.so
(00:48:52) plugins: probing /usr/lib/pidgin/notify.so
(00:48:53) plugins: probing /usr/lib/pidgin/musicmessaging.so
(00:48:53) plugins: probing /usr/lib/pidgin/extplacement.so
(00:48:53) plugins: probing /usr/lib/pidgin/iconaway.so
(00:48:53) plugins: probing /usr/lib/pidgin/xmppconsole.so
(00:48:53) plugins: probing /usr/lib/pidgin/ticker.so
(00:48:53) plugins: probing /usr/lib/purple-2/idle.so
(00:48:53) plugins: probing /usr/lib/purple-2/autoaccept.so
(00:48:53) plugins: probing /usr/lib/purple-2/ssl-gnutls.so
(00:48:53) plugins: probing /usr/lib/purple-2/libicq.so
(00:48:53) plugins: probing /usr/lib/purple-2/tcl.so
(00:48:53) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtcl8.4.so.0: cannot open shared object file: No such file or directory
(00:48:53) plugins: probing /usr/lib/purple-2/libirc.so
(00:48:53) plugins: probing /usr/lib/purple-2/ssl.so
(00:48:53) plugins: probing /usr/lib/purple-2/ssl-nss.so
(00:48:53) plugins: probing /usr/lib/purple-2/dbus-example.so
(00:48:53) plugins: probing /usr/lib/purple-2/libbonjour.so
(00:48:53) plugins: probing /usr/lib/purple-2/joinpart.so
(00:48:53) plugins: probing /usr/lib/purple-2/statenotify.so
(00:48:53) plugins: probing /usr/lib/purple-2/libsametime.so
(00:48:53) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(00:48:53) plugins: probing /usr/lib/purple-2/libyahoo.so
(00:48:53) plugins: probing /usr/lib/purple-2/libmsn.so
(00:48:53) plugins: probing /usr/lib/purple-2/libsimple.so
(00:48:53) plugins: probing /usr/lib/purple-2/libaim.so
(00:48:53) plugins: probing /usr/lib/purple-2/buddynote.so
(00:48:53) plugins: probing /usr/lib/purple-2/newline.so
(00:48:53) plugins: probing /usr/lib/purple-2/perl.so
(00:48:53) plugins: probing /usr/lib/purple-2/libgg.so
(00:48:53) plugins: probing /usr/lib/purple-2/libqq.so
(00:48:53) plugins: probing /usr/lib/purple-2/offlinemsg.so
(00:48:53) plugins: probing /usr/lib/purple-2/liboscar.so
(00:48:53) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(00:48:53) plugins: probing /usr/lib/purple-2/psychic.so
(00:48:53) plugins: probing /usr/lib/purple-2/log_reader.so
(00:48:53) plugins: probing /usr/lib/purple-2/libxmpp.so
(00:48:53) plugins: probing /usr/lib/purple-2/libzephyr.so
(00:48:53) plugins: probing /usr/lib/purple-2/libjabber.so
(00:48:53) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(00:48:53) plugins: probing /usr/lib/purple-2/libnovell.so
(00:48:53) util: Reading file accounts.xml from directory /home/japi/.purple
(00:48:53) util: Reading file status.xml from directory /home/japi/.purple
(00:48:53) sound: Initializing sound output drivers.
(00:48:53) GdkPixbuf: gdk_pixbuf_get_has_alpha: assertion `pixbuf != NULL' failed
(00:48:53) Gtk: Useless empty GtkIconSource
(00:48:53) GLib-GObject: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(00:48:53) gtkblist: added visibility manager: 1
(00:48:53) docklet: created
(00:48:53) util: Reading file blist.xml from directory /home/japi/.purple
(00:48:53) prefs: Reading /home/japi/.purple/prefs.xml
(00:48:53) prefs: Finished reading /home/japi/.purple/prefs.xml
(00:48:53) plugins: Unable to find saved plugin /usr/lib/gaim/docklet.so
(00:48:53) plugins: Loading saved plugin /usr/lib/pidgin/notify.so
(00:48:53) pounce: Error reading pounces: Failed to open file '/home/japi/.purple/pounces.xml': No such file or directory
(00:48:53) stun: using server 
(00:48:53) Session Management: ICE initialized.
(00:48:53) Session Management: Connecting with no previous ID
(00:48:53) Session Management: Handling new ICE connection... (00:48:53) done.
(00:48:53) Session Management: Connected to manager (GnomeSM) with client ID 117f000101000118871213300000057640018
(00:48:53) Session Management: Using pidgin as command
(00:48:53) gtkspell: Failed to setup GtkSpell: aspell: No word lists can be found for the language "en_US".
(00:48:53) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(00:48:53) dbus: The signal "gtkblist-hiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(00:48:53) account: Connecting to account uniguei@hotmail.com
(00:48:53) connection: Connecting. gc = 0xdd75a0
(00:48:53) msn: new httpconn (0xdf0740)
(00:48:53) dns: DNS query for 'messenger.hotmail.com' queued
(00:48:53) account: Connecting to account me.so.japi@gmail.com/Home
(00:48:53) connection: Connecting. gc = 0xdf0d40
(00:48:53) dns: DNS query for 'talk.google.com' queued
(00:48:53) account: Connecting to account kaworu_ta_happy@hotmail.com
(00:48:53) connection: Connecting. gc = 0xdf1580
(00:48:53) msn: new httpconn (0xdf1200)
(00:48:53) dns: DNS query for 'messenger.hotmail.com' queued
(00:48:53) Session Management: Received first save_yourself
(00:48:53) dns: Created new DNS child 7480, there are now 1 children.
(00:48:53) dns: Successfully sent DNS request to child 7480
(00:48:53) dns: Created new DNS child 7481, there are now 2 children.
(00:48:53) dns: Successfully sent DNS request to child 7481
(00:48:53) dns: Created new DNS child 7482, there are now 3 children.
(00:48:53) dns: Successfully sent DNS request to child 7482
(00:48:53) Session Management: Received save_complete
(00:48:53) docklet: embedded
(00:48:53) network: Entering nm_callback_func!
(00:48:53) dns: Got response for 'messenger.hotmail.com'
(00:48:53) dnsquery: IP resolved for messenger.hotmail.com
(00:48:53) proxy: Attempting connection to 65.54.239.80
(00:48:53) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(00:48:53) proxy: Connection in progress
(00:48:53) proxy: Connected to messenger.hotmail.com:1863.
(00:48:53) proxy: Error connecting to messenger.hotmail.com:1863 (Connection refused).
(00:48:53) proxy: Connection attempt failed: Connection refused
(00:48:53) msn: Connection error: Connection refused
(00:48:53) msn: Connection error from Notification server (messenger.hotmail.com): Unable to connect
(00:48:53) account: Disconnecting account 0x74ecb0
(00:48:53) connection: Disconnecting connection 0xdd75a0
(00:48:53) msn: destroy httpconn (0xdf0740)
(00:48:53) connection: Destroying connection 0xdd75a0
(00:48:58) util: Writing file accounts.xml to directory /home/japi/.purple
(00:48:58) util: Writing file blist.xml to directory /home/japi/.purple
(00:48:58) util: Writing file status.xml to directory /home/japi/.purple
dns[7481] Error: getaddrinfo returned -2
(00:49:03) dns: Got response for 'talk.google.com'
(00:49:03) dnsquery: Error resolving talk.google.com:
Name or service not known
(00:49:03) proxy: Connection attempt failed: Error resolving talk.google.com:
Name or service not known
(00:49:03) account: Disconnecting account 0x74aab0
(00:49:03) connection: Disconnecting connection 0xdf0d40
(00:49:03) connection: Destroying connection 0xdf0d40
dns[7482] Error: getaddrinfo returned -2
(00:49:03) dns: Got response for 'messenger.hotmail.com'
(00:49:03) dnsquery: Error resolving messenger.hotmail.com:
Name or service not known
(00:49:03) proxy: Connection attempt failed: Error resolving messenger.hotmail.com:
Name or service not known
(00:49:03) msn: Connection error: Error resolving messenger.hotmail.com:
Name or service not known
(00:49:03) msn: Connection error from Notification server (messenger.hotmail.com): Unable to connect
(00:49:03) account: Disconnecting account 0x74e030
(00:49:03) connection: Disconnecting connection 0xdf1580
(00:49:03) msn: destroy httpconn (0xdf1200)
(00:49:03) connection: Destroying connection 0xdf1580
(00:49:09) util: Writing file accounts.xml to directory /home/japi/.purple

```
Is there something that i am overlooking?

any suggestions?

You using wireless, or a direct connection?

---

### Post by very_japi on 2007-09-02
Well it makes no difference. It doesn't work in wither wireless or direct connection

---

### Post by very_japi on 2007-09-03
anyone?

---

### Post by Her Ghost on 2007-09-03
are you using a Belkin router?

---

### Post by very_japi on 2007-09-03
no, it's a 2Wire Router

---

### Post by philinux on 2007-09-03
Mines a 2wire router. Works fine with Gaim but I'm now using kopete. Have you changed the default settings?

---

### Post by very_japi on 2007-09-03
No, i haven't. even with a fresh install it doesn't work. The strange thing is that it does work with th native MSN client, so im guessing it has someting to do with the way Pidgin handles the connection

---

### Post by philinux on 2007-09-03
I'd give Kopete a try. It's in synaptic and it supports webcams.

---

### Post by very_japi on 2008-03-06
Problem solved... i have no idea why. I reinstalled (again) and out of the blue Pidgin works.

---

