---
title: "Add/Remove Apps Not working"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by OptimusPrime on 2006-09-24
I get this message after everytime I Install something from Add/Remove Apps.:

E: liblog4j1.2-java-doc: subprocess post-installation script returned error exit status 2
E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

It's only done this recently, so I just don't understand what I did.

---

### Post by someonedumb on 2006-09-24
I had that problem a few days ago... What happens is one (or more) package gets messed up and it renders the entire package manager useless. I had a package for a modem driver get messed up that was for an LT modem. To solve the problem I did a "locate ltmodem" and deleted all the files that were listed which appeared to be realated to the package. 

Maybe you can still remove the packages you're having trouble with graphically, but if you cannot then as far as I know, the best way to solve the problem is to "locate" the package files and manually delelte them.

Once the troublesome package files are gone package manager can begin working normally once again.

---

