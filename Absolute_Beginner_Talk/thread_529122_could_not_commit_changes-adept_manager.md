---
title: "could not commit changes-adept manager"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by asad12 on 2007-08-18
the error could not commit changes-adept manager:: there was an error commiting changes. 

i can't help it how to install any programs. because i a gettiing this error .

---

### Post by taurus on 2007-08-18
What happens when you run these two commands from a terminal (make sure you close down adept or synaptic first)?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by asad12 on 2007-08-21
i get this after i do that  , please help
> 
oem:sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libjasper-1.701-1 libjasper-runtime rsync
3 upgraded, 0 newly installed, 0 to remove and 0 not
Need to get 0B/423kB of archives.
After unpacking 12.3kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: syntax error: unknown group `root' in statover
E: Sub-process /usr/bin/dpkg returned an error code

can you please suggest anything else

---

