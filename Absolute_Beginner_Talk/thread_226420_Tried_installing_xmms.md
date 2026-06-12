---
title: "Tried installing xmms"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by tdaman927 on 2006-07-31
I tried installing xmms and on the add/remove Applictions window it says 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.   

What do i do.

---

### Post by sabitha on 2006-07-31
> I tried installing xmms and on the add/remove Applictions window it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

What do i do.

thats mean u just have not finish your another installation
u can run
$ sudo dpkg --configure -a
or
$ sudo apt-get -f install

to fix that first
then u can install xmms

---

### Post by tdaman927 on 2006-07-31
it says bash: $: command not found when i type them in?

---

### Post by NewbieNik on 2006-07-31
after opening the terminal type

sudo apt-get install -f

if that fails check apt is working by

sudo apt-get update

this should contact all the apt sources to update your software list. Then try

sudo dpkg -configure -a xmms

to repair. Let us know how you get on!

---

### Post by tdaman927 on 2006-07-31
Thanks it worked

---

### Post by tdaman927 on 2006-07-31
ok now i get E: sun-java5-doc: subprocess post-installation script returned error exit status 1

What does that mean?

---

### Post by NewbieNik on 2006-07-31
sounds like the Java package is not installed correctly.
did you run the

sudo apt-get install -f

command? or just the dpkg command?

---

