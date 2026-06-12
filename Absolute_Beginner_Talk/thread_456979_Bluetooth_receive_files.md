---
title: "Bluetooth receive files"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by jbiskupiak on 2007-05-28
I am running Feisty Fawn on my Sony Vaio laptop.  I am able to send files to other computers or mobile phones with bluetooth, however I am unable to receive files from other computers or mobile phones via bluetooth.  When I try to send to the laptop, I receive an error message on the computer trying to send to my laptop that the necessary services are not found.

---

### Post by Inxsible on 2007-05-29
try this: 
 
```

sudo aptitude install gnome-bluetooth bluez-utils python-bluez

```
 
Then Go to Applications -- > Accessories -- > Bluetooth File Transfer and switch it on. You should be good to go then.

---

### Post by La muerte del DIos on 2007-06-05
Thanks, works perfect on my computer, just right clickin' > sent to > bluetooth.  Finally got the dongle working.:popcorn:

---

