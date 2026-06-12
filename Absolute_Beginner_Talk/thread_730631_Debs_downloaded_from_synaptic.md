---
title: "Debs downloaded from synaptic"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by tel93 on 2008-03-21
When downloading debs via Synaptic, does it delete the .deb file or save it somewhere? If so, where does it save them to? I'm not talking about the installed programs in /usr/bin, but the .deb files used to install the programs.

---

### Post by PmDematagoda on 2008-03-21
It stores the packages in /var/cache/apt/archives.

---

### Post by forestpixie on 2008-03-21
If you're thinking of clearing them out to get the space back don't just delete them, they can be cleaned out from the terminal

```
sudo apt-get clean
```

---

