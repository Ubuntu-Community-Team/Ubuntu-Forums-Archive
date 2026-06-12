---
title: "Error during 6.06 upgrade"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by dunomous on 2006-06-06
During upgrading from breezy badger 5.10 to the 6.06 LTS, I forgot that my memory was at it's max, thus a folder was not created, which gave me an error message about. Since I was multitasking, I made the mistake of closing the error instead of writing it down. Now that everything else installed fine, I'm curious as to if there is a quick error checking process that I can run, if it fixed itself.

---

### Post by giftnudel on 2006-06-08
Hi,

there is one which can determine if there are missing packages or unmet dependencies:

type:
```
sudo apt-get -f install
```
in a terminal, the requested passwort is yours, and see if it brings up any errors.

regards,
giftnudel

---

### Post by dunomous on 2006-06-08
ah, great!  danke schoen!

---

