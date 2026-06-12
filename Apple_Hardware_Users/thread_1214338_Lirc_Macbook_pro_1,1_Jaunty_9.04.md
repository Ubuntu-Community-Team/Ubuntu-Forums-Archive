---
title: "Lirc Macbook pro 1,1 Jaunty 9.04"
date: 2009-07-15
forum: Apple Hardware Users
---

### Post by malluen on 2009-07-15
After upgrading to 9.04 my lirc doesn't seem to work anymore.
I started with a clean install (purge and re-install) of lirc-x, input-lirc, lirc, lirc-modules-source, and module-assistant.

Upon restarting it seems as if lirc hasn't taken over yet. The default keys work (which worked out of the box before lirc) but only on rhythmbox.
 
Greping syslog for lirc gives me:
```
Jul 15 04:30:38 Igloo lircd-0.8.4a[2492]: caught signal
Jul 15 04:31:26 Igloo lircd-0.8.4a[2487]: lircd(macmini) ready
Jul 15 04:31:26 Igloo inputlircd: Started
Jul 15 04:31:31 Igloo inputlircd: Started
Jul 15 04:32:37 Igloo kernel: [   82.838108] rhythmbox[4107]: segfault at c ip b4c09867 sp bfea4d40 error 4 in liblirc_client.so.0.2.1[b4c07000+5000]

```
The rhythmbox part is from launching rhythmbox with the lirc plugin turned on. When I press a button from the remote it crashes.

When I try irw it seems to work. Shows:
```
72 0 KEY_VOLUMEDOWN event6
73 0 KEY_VOLUMEUP event6
9f 0 KEY_FORWARD event6
a4 0 KEY_PLAYPAUSE event6
8b 0 KEY_MENU event6

``` When I press given keys.
 
To make matters stranger for me I added irxevent and irxexec to 'startup
applications'. However when I try them from manually 'irexec -d' seems to run fine but 'irxevent' gives me:
"irxevent: bad file format, /home/malluen/.lircrc:5"

Dmesg gives me only the same rhythmbox hiccup as in my syslog.

Any clues would be appreciated. Btw I did indeed setup lirc as a macmini receiver as I was told from other ubuntu forums.

I'm lost as to why lirc won't work when irw is receiving my keys. It seems as if most people on macs have either the problem of irw not responding at all or it works flawlessly.

---

