---
title: "Seahorse / gedit plug ins ?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by ryan on 2006-11-22
I recently complied Seahorse from the 9.7 source  and I am trying to get the right click "encrypt" "Decrypt" and "sign" functions to work as per the documentation below.

[B]Text Editor: To enable the Seahorse plugin in gedit choose Edit &#8594; Preferences

Then select the tab Plugin and check Text 		Encryption.[/B]

When I go to gedit/edit/preferences/Plugin there is no option for "Text Encryption".

Does that mean that I did some thing wrong when I compiled Seahorse ? Was there a flag that I was supposed to use or did I miss a library when I did the configure deal ?

tks for any input.

---

### Post by ryan on 2006-11-23
> **ryan said:**
> I recently complied Seahorse from the 9.7 source  and I am trying to get the right click "encrypt" "Decrypt" and "sign" functions to work as per the documentation below.

[B]Text Editor: To enable the Seahorse plugin in gedit choose Edit &#8594; Preferences

Then select the tab Plugin and check Text 		Encryption.[/B]

When I go to gedit/edit/preferences/Plugin there is no option for "Text Encryption".

Does that mean that I did some thing wrong when I compiled Seahorse ? Was there a flag that I was supposed to use or did I miss a library when I did the configure deal ?

tks for any input.

In thinking about it a little more and looking at the output from "./configure" there seemed to be no support for nautilus so I installed libnautilus-extension-dev as it was the only nautilus dev lib I could see in the repos and it wasn't installed.

**Output from ./configure with libnautilus-extension-dev not installed**
ryan@ubuntu:~/Seahorse/seahorse-0.9.7/seahorse-0.9.7$ ./configure --prefix=/usr --sysconfdir=/etc
GnuPG Version:           gpg (GnuPG) 1.4.3
GPGME Version:           1.1.2
SSH Support:             yes
gnome-keyring Support:   yes
Keyserver Support:       no
  LDAP:                  no
  HKP:                   no
Plugins:
  Epiphany:              no
  GEdit (v <= 2.12):     no
  GEdit (v >= 2.14):     yes
  Panel Applet:          no
  Seahorse Agent:        yes
  **[COLOR="Red"]Nautilus:              no[/COLOR]**
  Key Sharing:           no
Notification Support:    no


**Output from ./configure with libnautilus-extension-dev installed**
ryan@ubuntu:~/Seahorse/seahorse-0.9.7/seahorse-0.9.7$ ./configure 
GnuPG Version:           gpg (GnuPG) 1.4.3
GPGME Version:           1.1.2
SSH Support:             yes
gnome-keyring Support:   yes
Keyserver Support:       no
  LDAP:                  no
  HKP:                   no
Plugins:
  Epiphany:              no
  GEdit (v <= 2.12):     no
  GEdit (v >= 2.14):     yes
  Panel Applet:          no
  Seahorse Agent:        yes
  **[COLOR="Red"]Nautilus:              yes[/COLOR]**
  Key Sharing:           no
Notification Support:    no


"Encrypt" with right click works now but not "decrypt file" but I am sure that it will get sorted out soon.

---

