---
title: "Error Message"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by knoxy5000 on 2006-11-10
Just installed 6.06 lts on my system. Atfer running easyubuntu i get this error message when trying to either update or run easy unbuntu


W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: GPG error: [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57

Anyone know how i can fix this ? ](*,) :-?

---

### Post by loell on 2006-11-10
you need to install the public key for that repository

---

### Post by loell on 2006-11-10
```
wget http://easyubuntu.cafuego.net/969F3F57.gpg -O - | sudo apt-key add -
```

---

### Post by knoxy5000 on 2006-11-10
Thanks for that, added that key for easy unbuntu. Any ideas on how to add the other key ?

---

