---
title: "fstab /from recovery"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-03-15
is there a way i can edit my fstab from recovery mode in edgy,,

thank you

---

### Post by tommcd on 2007-03-15
You should be able to <sudo nano /etc/fstab> from recovery mode. Then just ctrl+X, Y, to save the file. Then sudo reboot. What problem are you having?

---

### Post by STREETURCHINE on 2007-03-15
i edited my fstab to mount hdb2 but i put hdb3 and now it wont load 


error

unable to resolve uuid=423d214d etc etc etc 
fsck died with exit status 8
and when i try to boot it tells me my last session lasted less than 30 seconds and i keep getting sent to the login page..

---

### Post by tommcd on 2007-03-15
Can you boot to recovery mode? If so you should be able to edit the fstab with nano like I described. In the future back up any config file before editing in case you make a mistake.

---

### Post by STREETURCHINE on 2007-03-15
advice i normally give to outher people yes i have backup but just dont get it 

it is telling me there is an erro on line 14 in the fstab
i only have 12 lines.

plus i now seem to have lost permissions to my home file i will just reinstall

---

