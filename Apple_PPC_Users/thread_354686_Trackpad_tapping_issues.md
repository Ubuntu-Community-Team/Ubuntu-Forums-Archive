---
title: "Trackpad tapping issues"
date: 2007-02-06
forum: Apple PPC Users
---

### Post by galvatron1983 on 2007-02-06
Im running Kubuntu on my Powerbook G4 and Im able to use a tap on the trackpad to click with the following command

```
sudo trackpad tap
```

The problem is, everytime I restart Kubuntu or wake from sleep mode, I lose the tapping function, and I have to enter the command over again to reactivate it. Is there a way for Kubuntu to remember the trackpad function through a restart or sleep and keep the trackpad tapping functionality active?

---

### Post by sulobanks on 2007-02-11
If you install powerprefs from the repos, it allows you to change all your pbbuttons settings.  Then they will stick.  Or if you prefer editing text files, just edit /etc/pbbuttonsd.conf.  The setting to edit is TPMode.  Set it to "tap".

---

