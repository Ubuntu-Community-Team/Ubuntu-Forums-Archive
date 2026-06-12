---
title: "Firefxo and other geck-based browsers not connecting to internet"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-11-16
Firefox and Oceweasel are not able to connect to the net; Opera is doing it fine.

1. I have proxies lifted (at home no proxy required)--set to automatic
2. Router and DSL modem all working fine
3. WIFI nm-applet picking up signal
4. apt-get and synaptic is working fine


What could be going on? What did I do recently: I created a new user account.

Why would Opera work but not Firefox/Iceweasel?

Help will be appeciated,

S

---

### Post by alienexplorers on 2007-11-17
Try creating a new profile for firefox.  Run in terminal:
> firefox -profilemanager
try firefox again and if it works you can migrate your extensions to the new profile.
> [http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

---

### Post by shuttleworthwannabe on 2007-11-17
that fixed it. What could have gone wrong with the 'default' profile?

many thanks

---

### Post by corevette on 2007-11-17
try running firefox in safe mode
```
firefox -safe-mode
```
or
```
/path/to/firefox/firefox -safe-mode
```

---

### Post by FuturePilot on 2007-11-17
> **shuttleworthwannabe said:**
> that fixed it. What could have gone wrong with the 'default' profile?

many thanks

Sometimes they just get corrupted for some reason.

---

