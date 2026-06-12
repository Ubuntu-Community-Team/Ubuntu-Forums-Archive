---
title: "Help fixing apt-get problem"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by osotogari on 2008-03-01
```
E: Unable to parse package file /var/lib/apt/lists/ie.archive.ubuntu.com_ubuntu_dists_gutsy-updates_main_binary-i386_Packages (2)

```

hi im getting the above error when trying to upgrade using both apt-get from the terminal and synaptic. Any ideas as i cant find anything to remedy the problem on the forums and I cant install new packages.

thanks in advance

---

### Post by SOULRiDER on 2008-03-01
Try:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by aidanr on 2008-03-01
Try changing to the main server in synaptic -> settings -> repositories -> download from:

---

### Post by osotogari on 2008-03-01
> **aidanr said:**
> Try changing to the main server in synaptic -> settings -> repositories -> download from:

that fixed it. thanks

---

### Post by SOULRiDER on 2008-03-01
Good to hear. Please mark the thread as solved :)

---

