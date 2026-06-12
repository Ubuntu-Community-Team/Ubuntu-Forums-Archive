---
title: "FireFox will not start!"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by lutherhert on 2007-09-14
I am using Ubuntu 7.04. on an older Compac machine with 769 MB 

memory. The installation went well, but I cannot get FireFox to start when 

I click on it. 

I am using Yahoo, which uses a PPPOE connection. I used the terminal 

command: sudo pppoeconf. It did not work, so I assume that I also need 

to install the pppoe package.

Should I remove and re-install Firefox?

I tested my network connection and it is working. I can ping my router.

I am new to Ubuntu and would appreciate some advice.

Thanks

---

### Post by SOULRiDER on 2007-09-14
sudo pppoeconf should work for setting up your PPPoE connection. Type: ```
sudo pon dsl-provider
``` and see if it connects.

To see whats wrong with FF, open a Terminal ** Applications > Accessories > Terminal** and type: ```
firefox
``` then paste the output here so we cna help you.

---

### Post by SunnyRabbiera on 2007-09-14
hmm, well a re install might help.
There is no real difference between firefox here and on windows though there vare a few here and there and there might be a quirk somewhere in the system.

---

### Post by SOULRiDER on 2007-09-14
I suggest you purge and then reinstall it. Mind you, config files EILL be lost, that may include bookmarks etc:
```
sudo aptitude purge firefox
sudo aptitude install firefox
```

---

