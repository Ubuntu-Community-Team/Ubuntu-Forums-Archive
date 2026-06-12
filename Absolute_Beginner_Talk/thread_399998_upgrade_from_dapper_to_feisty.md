---
title: "upgrade from dapper to feisty"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-04-03
Just a quick one, I'm running dapper and have previously tried to upgrade to edgy by ..........
1; from the liveCD and .....
2; thru apt-get.
Both methods failed, on numerous attempts, some problem with Xorg. But dapper runs fine.

Anyway the guts of it is, can I upgrade direct to feisty from dapper? Or must I use the liveCD and set everything up again?

---

### Post by zvacet on 2007-04-03
You can not upgrade directly from Dapper to Feisty.It will be fresh install.you can upgrade to Edgy with this command
```
gksu "update-manager -c" 
``` 

Before you do the upgrade you can use [http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")
With that tool you will put your var/cache/apt/archives on the safe place in the case something goes wrong,because you will have all your downloads and updates from Dapper in the safe place.
It is up to you wich method you will use.

---

### Post by carloslosgrande on 2007-04-03
OK, thanks zvacet!:guitar:

---

