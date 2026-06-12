---
title: "dpkg error using automatix"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by NirvanaRush2112 on 2006-12-30
well this just happend a couple of mins ago and i searched the forums and found this... sudo dpkg --configure -a .. then i did it but this is what i get...

matt@ubuntu:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.21.78.2ubuntu1~dapper1) ...
Downloading...

then i leave it and it doesint do anything...ive had this problem getting flash and it's probly why i have the error...so what do i do to fix this error?

---

### Post by NirvanaRush2112 on 2006-12-30
lalalala bumpa

---

### Post by NirvanaRush2112 on 2006-12-30
bump..bummm..bump..bump

---

### Post by NirvanaRush2112 on 2006-12-30
plz help me!

---

### Post by MkfIbK7a on 2006-12-30
try to just download and install flash in synaptic (am i right in assuming this is for firefox?)

---

### Post by arnieboy on 2007-01-01
try doing 
```
sudo apt-get -f install
```
automatix does not install the flash package in multiverse. In fact it uninstalls it (because its buggy).

---

### Post by MkfIbK7a on 2007-01-01
> matt@ubuntu:~$ sudo dpkg --configure -a
Setting up flashplugin-nonfree (9.0.21.78.2ubuntu1~dapper1) ...
Downloading...

i had the same problem i let it sit for 10 or so minutes and it finished and installed flash

---

