---
title: "dpkg error message"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2006-01-23
i was trying to install a rpm file which i had converted to a deb and all sorts of crazy stuff, but it kept giving me errors so i canceled it but now when i try to use synaptic it gives me the error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" but i ran that and nothing happened

---

### Post by az on 2006-01-24
Did you try to remove the culprit package?

sudo apt-get remove --purge wonkycrap

(wonkycrap.rpm)


Did you try 

sudo apt-get -f install

too?

---

