---
title: "GPG error/medibuntu"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by jon zendatta on 2007-11-15
hello people
when i update i get  : gpg error- medibuntu signature could not be verified. 
the key in question is '2EBC260C5A2783' ..in my sources list this key is absent so i can't erase it.
if needed i can post my souce.list 
thank you

---

### Post by taurus on 2007-11-15
Try

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by santiagoward2000 on 2007-11-15
> **jon zendatta said:**
> hello people
when i update i get  : gpg error- medibuntu signature could not be verified. 
the key in question is '2EBC260C5A2783' ..in my sources list this key is absent so i can't erase it.
if needed i can post my souce.list 
thank you

HI!
When you added the Medibuntu repository, had you added the key too? You get it by typing this on a console:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by jon zendatta on 2007-11-15
yes that worked thanks   :KS

---

### Post by santiagoward2000 on 2007-11-15
> **jon zendatta said:**
> yes that worked thanks   :KS

You're welcome!

---

### Post by dfmalh on 2008-07-13
Thanks, this helped me as well!!  :guitar:

---

