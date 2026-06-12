---
title: "whats wrong :( :( :("
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by jrockpunk1 on 2008-02-17
i installed ubuntu 6.10, upgraded to 7.04, then to 7.10. ive installed compizconfig setting manager, but when i click on it (system, preferences, ccsm), nothing happens, its as if i havent clicked anything. also, the desktop efects in the preferences section has gone. it just isnt there. should i reinstall or something??? if so, how?

---

### Post by jan quark on 2008-02-17
upgrading over so many distribution versions may cause some well disorder in the packages

it is always better to do a fresh install of the latest version and not to start with the olderst and upgrade

to enable compiz you must set up your graphic card correctly

 please post the output of 
```

lspci
```
```

sudo lshw
```

---

### Post by jrockpunk1 on 2008-02-17
ok the wobbly windows etc i have got working, but now i just cant get on the preferences to change the effects :( it wont come up with ccsm when i goto system preferences ccsm. or if i go to system preferences appearance visual effects prefereces. what should i do?

---

### Post by jan quark on 2008-02-17
run 

```
ccsm
```

in terminal

what error messages do you get ?

---

