---
title: "[SOLVED] Upgrading releases..."
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by KaYnemO on 2007-09-30
This is a stupid question, but nevertheles..

Different distros have it in a different way - I am new to Ubuntu, so I want to know. When the next release comes out (I am happy with Feisty Fawn though), will I need to completely reinstall the system or will it simply update through Synaptics?

thx

---

### Post by insane_alien on 2007-09-30
update-manager should notify you of the new release and handle everything for you.

if you want to to it the old fashioned way, replace all mentions of feisty with gutsy in /etc/apt/sources.list and do ```
sudo aptitude update && sudo aptitude dist-upgrade
```

---

### Post by ThrobbingBrain66 on 2007-09-30
You can either download Gutsy when it comes out and perform a fresh install or upgrade through Synaptic: [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

