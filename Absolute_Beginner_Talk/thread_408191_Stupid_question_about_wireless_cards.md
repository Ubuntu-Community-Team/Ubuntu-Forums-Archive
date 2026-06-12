---
title: "Stupid question about wireless cards"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by supazio on 2007-04-13
If I buy, install a wireless card on the Supported wireless cards list (the Linksys WMP54G specifically), what more do I have to do to get wireless working? (Besides enter the SSID and WEP key)
PS: Ubuntu 6.10

---

### Post by su_penguin on 2007-04-13
You'll need the correct driver associated w/ your card. Look on the list again.

then:

sudo apt-get install ndisgtk

sudo apt-get install ndiswrapper-utils

...and go from there.


P.s. Buy the WMP300N by Linksys

---

