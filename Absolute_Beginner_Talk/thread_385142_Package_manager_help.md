---
title: "Package manager help"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by AMHA on 2007-03-15
hi all...
i have tried to install google earth, so i downloaded the package and run it into Gdebi package installer, but it took too long and i killed the process.
now whenever i try to use the synaptic package manager or update manager, i get this message: 
E: The package googleearth needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

when i try to reinstall the googleearth package it doesn't work also.

i am new with linux and i am using ubuntu 6.10.
this is my first post... please be easy on me.:lolflag: 

thanx in advance

---

### Post by lamalex on 2007-03-15
try running these commands in terminal
```
sudo apt-get clean
sudo apt-get autoclean
```

---

### Post by haelters on 2007-03-15
try:
```

dpkg --remove --force-remove-reinstreq googleearth

```

Hope it helps !

---

### Post by Kobalt on 2007-03-15
> **haelters said:**
> try:
```

dpkg --remove --force-remove-reinstreq googleearth

```

Hope it helps !

Maybe a little 'sudo' before all that would be appropriate ;)

---

### Post by AMHA on 2007-03-15
thank you very much guys.
the update manager and synaptic now work just fine.
your replies are appreciated very much.:guitar:

---

