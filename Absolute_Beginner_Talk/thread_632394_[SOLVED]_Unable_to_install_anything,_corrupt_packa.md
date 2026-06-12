---
title: "[SOLVED] Unable to install anything, corrupt package."
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by sephiap on 2007-12-05
Hi guys, I've taken the plunge and installed Ubuntu Studio, everything running perfect, loving it - thought I would download Virtualbox to run a Win XP host within. Downloaded the .deb file, double clicked - GDebi was running a progress bar and nothing happened, I left it for about 6 hours and it didn't move. I therefore force quit and tried again, it now says the package is corrupt or permissions are not correct...

Synaptic won't load as it gives the message...

"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."

So I've tried downloading other things via apt-get to have...

"E: The package virtualbox needs to be reinstalled, but I can't find an archive for it."

Whilst trying to redownload Synaptic that is... I've tried everything... sudo apt-get install virtualbox --reinstall / --fix-broken  | sudo apt-get remove virtualbox...

nothing.

Have I borked my installation? I will cry if I have... I wanted to love Linux...

please guys... help!

---

### Post by forestpixie on 2007-12-05
that takes me back :) - try this 

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by sephiap on 2007-12-05
It worked! I love you!!! :x

---

