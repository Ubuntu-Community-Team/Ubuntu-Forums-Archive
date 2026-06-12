---
title: "enable multiverse"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by GotRoar on 2007-07-26
how can i enable multiverse? i want to install unrar but evert where i look i see you need to do that but know one ever says how.

---

### Post by Rocket2DMn on 2007-07-26
```
gksudo gedit /etc/apt/sources.list
```
Enable here by removing the # in front of the appropriate lines for multiverse.

GUI approach: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Vague on 2007-07-26
Open Synaptic.  Go to Settings>Repositories and check the box for Multiverse.

---

### Post by RomeReactor on 2007-07-26
Hi. As **Vague** said, enabling the repository through Synaptic is easy. Just press the **Reload** button after enabling the repository so Synaptic is brought up to date with the repository information.

Or, if you went with the command line method, do this afterwards:
```
sudo apt-get update
```

---

