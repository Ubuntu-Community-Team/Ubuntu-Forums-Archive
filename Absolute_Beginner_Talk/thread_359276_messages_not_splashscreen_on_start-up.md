---
title: "messages not splashscreen on start-up"
date: 2007-02-11
forum: Absolute Beginner Talk
---

### Post by epsydom12 on 2007-02-11
This may be old school or at least not mainstream with ubuntu but how do i remove the splash screen during startup and watch the messages instead. I run several servers and like to see if the services started on boot rather than having to go look at the logs.  thanks for any help in advance.

---

### Post by nickburns on 2007-02-11
This may be dangerous territory, but look at the following packages:

libusplash0
usplash
usplash-theme-ubuntu

I think ( don't kill me if I am wrong ) that if usplash-theme-ubuntu is removed you will not get the progress bar, only text.

---

### Post by nickburns on 2007-02-11
You may want to look at:

cat /boot/grub/menu.lst

to see if there are settings you can change.

---

### Post by the.phantom on 2007-02-11
if you are using edgy

system
preferences
sessions
sessions options

;-)

---

### Post by epsydom12 on 2007-02-12
I am running kde so the option in system doesn't exist.  Instead I edited what looks to be the ubuntu version of grub.conf file, /boot/grub/menu.lst, to removed "quite" and "splash" from the entry for the kernel.  I suspect this will have to be done every time the file is rewritten due to a kernel upgrade.  The messages are a bit more detailed and harsh looking from other variants but the end result is the same.

---

