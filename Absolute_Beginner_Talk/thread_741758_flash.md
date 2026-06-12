---
title: "flash"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Neilisgreat on 2008-04-01
Hello, on trying to install flash on Gutsy i downloaded the given player
which is not the abode flash and under my admin logon works fine but when one of my kids login and try you tube or iplayer they keep getting messagae that suitable codec is needed ?
Any ideas?

---

### Post by zvacet on 2008-04-01
This is probably not the only way but anyway...... go to the synaptic and remove what you installed,then go to the terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```

That will give you flash,java,plugins....

---

### Post by Neilisgreat on 2008-04-01
yes but flash works only my admin account but not the kids logon.
do i have to give admin rights and get them to logon so flash can be installed and then take away rights?

---

### Post by zvacet on 2008-04-01
I installed flash the same way I recommended to you and all users are able to use it.

---

### Post by forrestcupp on 2008-04-01
He's right.  If you install the flashplugin-nonfree from the repositories rather than from Adobe's site, it will work for everyone.

---

