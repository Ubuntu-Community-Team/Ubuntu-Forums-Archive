---
title: "softwares don't install"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by ans5685 on 2007-12-02
Hi i am new to linux and know next to nothing of it. But through these help forums posts  I was able to install xubuntu-desktop
and then a little bit more adventurously greenos-desktop
But since then i cannot install any more neither through Synaptics nor through apt-get
the error is roughly the same
This is what Synaptics says after downloading the requisite files.(without quotes)

"""**E: /var/cache/apt/archives/libdb4.4_4.4.20-8.1ubuntu3.1_i386.deb: files list file for package `iat' is missing final newline**"""


HELP!:confused::confused::confused::confused::confused:

---

### Post by arijarot on 2007-12-25
> **ans5685 said:**
> Hi i am new to linux and know next to nothing of it. But through these help forums posts  I was able to install xubuntu-desktop
and then a little bit more adventurously greenos-desktop
But since then i cannot install any more neither through Synaptics nor through apt-get
the error is roughly the same
This is what Synaptics says after downloading the requisite files.(without quotes)

"""**E: /var/cache/apt/archives/libdb4.4_4.4.20-8.1ubuntu3.1_i386.deb: files list file for package `iat' is missing final newline**"""


HELP!:confused::confused::confused::confused::confused:

are you able to update the system? what is the output of ```
sudo apt-get update && apt-get upgrade 
```?

---

