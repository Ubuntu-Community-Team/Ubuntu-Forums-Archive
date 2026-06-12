---
title: "Scanning with a printer"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2008-02-18
How can I get my printer, hp psc1315 all-in-one, to work as a scanner? It is recognized and print, but when I hit scan, nothing happens.
 thanks for any help.

---

### Post by jimrz on 2008-02-18
> **CapitanYochua said:**
> How can I get my printer, hp psc1315 all-in-one, to work as a scanner? It is recognized and print, but when I hit scan, nothing happens.
 thanks for any help.

Try going to System > Preferences > HPLIP Toolbox and doing your scan from there. Works just fine on my psc1610. Don't remember for sure but I think "toolbox" is there in the default install, if not you can get it from Synaptic.

---

### Post by jcwmoore on 2008-02-18
I have a PSC 1210 and the scanning didn't work at first...

the solution was to install the package 'hpoj'  you can do it by running

```
sudo apt-get install hpoj
```

or you can find it in synaptic

after that you can use XSane to scan (or any other scanner utility)

---

### Post by theRightNee on 2008-02-18
is there a "toolbox" for cannon printers? i have an mp350 and would like to know my options =]

---

### Post by CapitanYochua on 2008-02-18
> **jimrz said:**
> Try going to System > Preferences > HPLIP Toolbox and doing your scan from there. Works just fine on my psc1610. Don't remember for sure but I think "toolbox" is there in the default install, if not you can get it from Synaptic.

 I hit the scan button via HPLIP Toolbox, and an error message appeared stating that the device could not be opened because it was busy...

Thanks for the replies.

---

