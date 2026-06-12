---
title: "Root"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by sunrex on 2005-08-21
my scripter for my CSS deleted the root account, how do i get back root and SUDO

plz tell me i mean it, its so freekin annoying, without root our server is slowly crashing.....

can anyone tell me how to get root/sudo back....asap...please?

---

### Post by humanity_to_others on 2005-08-21
[http://ubuntuguide.org/#allowmoresudoers](http://ubuntuguide.org/#allowmoresudoers)

---

### Post by sunrex on 2005-08-21
if i have no root or sudo that will work?
oh well i can try..

---

### Post by humanity_to_others on 2005-08-21
[QUOTE=sunrex]if i have no root or sudo that will work?
oh well i can try..[/QUOTE]
you can use a livecd then chroot

---

### Post by sunrex on 2005-08-21
[QUOTE=sunrex]if i have no root or sudo that will work?
oh well i can try..[/QUOTE]
 once again i knew it wont help, im not in the sudoers file, and my scripter destroyed his account. THERES NO ONE IN THE SUDERS FILE

---

### Post by sunrex on 2005-08-21
[QUOTE=sunrex]once again i knew it wont help, im not in the sudoers file, and my scripter destroyed his account. THERES NO ONE IN THE SUDERS FILE[/QUOTE]
 > you can use a livecd then chroot

i cant just use the cd i installed with, if i can what do i do?

---

### Post by sunrex on 2005-08-21
...

please there has to be a very simple command for this =/

---

### Post by humanity_to_others on 2005-08-21
[http://ubuntuguide.org/#gainrootinstallcd](http://ubuntuguide.org/#gainrootinstallcd)
or
[http://ubuntuguide.org/#gainrootwithoutlogin](http://ubuntuguide.org/#gainrootwithoutlogin)

---

### Post by sunrex on 2005-08-21
allright i got this far but how do i add more users to sudo? the link way up there with things need GEDIT which i dont have becouse this is in "server only" not full install.

can anyone tell me how to add somone to sudo file and root?

---

### Post by humanity_to_others on 2005-08-21
you can use nano
```
export EDITOR=nano && sudo visudo
```

---

### Post by sunrex on 2005-08-21
THANK YOU ALL SO MUCH!!!

i managed to get root - passoword to run so at least we got sudo back, no root on other accounts yet, but it works none the less, thank you all so much!

---

