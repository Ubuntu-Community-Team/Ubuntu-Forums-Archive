---
title: "uninstall madwifi kernel panic"
date: 2008-10-23
forum: Apple Hardware Users
---

### Post by Jeratt on 2008-10-23
This is a long story. Okay. At the beginning, like many other MacBook users, I discovered my wifi didn't work. Luckly, I found [this page]("https://help.ubuntu.com/community/MacBook#Wireless"). I installed madwifi, and it worked! Soon though, I discovered that any major update overwrote madwifi, and it stopped working. So, instead of having to find a wired internet connection every time, I kept the install instructions and files in my home directory. On the most recent update that required me to restart my computer, I found my wifi connection was gone. No problem, I reinstalled madwifi, and restarted. Uhoh. Now every time I restart in that kernel (2.6.24-21-generic I belive) it gives me a kernel error. I'm kind of a noob, and I don't understand make completely, but I did try running "make uninstall-modules" in the directoy I installed madwifi from, and it prints out a script called scripts/find-madwifi-modules.sh. I tried running it with the arguments it gave me, but it still won't uninstall. Help please?

---

### Post by StooJ on 2008-10-23
Try to boot into a recovery console (one should be available from grub)

Navigate to your madwifi folder (where you make installed from in the first place) and type

```
make uninstall
```

I think that should do it.

---

### Post by cyberdork33 on 2008-10-23
use the newer ath9k module..

---

