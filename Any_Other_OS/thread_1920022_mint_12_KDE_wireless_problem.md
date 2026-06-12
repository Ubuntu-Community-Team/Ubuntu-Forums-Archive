---
title: "mint 12 KDE wireless problem??"
date: 2012-02-03
forum: Any Other OS
---

### Post by miasmablk on 2012-02-03
im on a dual boot machine and my windows partition is my only way to connect to the internet so i can only describe my terminal outputs:

```
sudo lspci -v
```lists my wireless card but doesn't list the drivers i have installed for it.
b43fwcutter firmware-b43-lpphy-installer

```
ifconfig
```
does not list my wireless card.

also i should mention these are the drivers i have always used without any problems the STA drivers tend to cut my speed down by almost 80%

---

### Post by Perfect Storm on 2012-02-04
Moved to Other OS/Distro Talk.

---

### Post by miasmablk on 2012-02-04
Never mind I found the problem. There was a package conflict, the STA driver, somehow was already installed but not reported by either "lspci -v" or "jockey-gtk" once I removed it wireless works again.

---

