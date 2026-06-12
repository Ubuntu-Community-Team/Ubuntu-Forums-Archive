---
title: "Testing Lubuntu PowerPC quantal 12.10"
date: 2012-06-09
forum: Apple Hardware Users
---

### Post by nm_geo on 2012-06-09
I just finished live USB qa-testing Lubuntu Quantal 12.10 on my G4 Powerpc and installing from there to the entire HHD.  The installation went quite well but if you decide to test know this:

There is no working installed internet browser in the present daily live build.  However you can install FireFox 11.0 with Synaptic or CLI and get a working browser.

---

### Post by EuroCity on 2012-06-10
... In others words, that would be:

```
sudo apt-get update

sudo apt-get install firefox firefox-locale-***xx***
```

... where ***xx*** is your language localisation code (for example, *de* with German, *fr* with French, *it* with Italian, and so on...).

---

