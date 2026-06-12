---
title: "need help to install ubuntu on a system with windows xp"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by simcher on 2007-09-18
hi guys. sorry i am a noob... really interested to use ubuntu, but facing problem... now i can't even access my windows xp... am posting this now on the ubuntu live cd before i install ubuntu :P

ok here is my problem... 

i have 2 SATA hdd...
primary 300gb drive have windows xp and a storage drive...
secondary 500gb drive is partition into 3 partition, mainly for installation of ubuntu 7.04, swap and storage.

ok now i am at the prepare partition screen, i make a 50gb partition on the secondary 500gb for ubuntu with a mount drive of "/", and a 1gb parition as a swap.

i went ahead to install ubuntu happily... everything was smooth... until it restarted my computer... then i see "grub loading, please wait...." i waited for like 10mins... and nothing happened? did i do anything wrong?

---

### Post by anemptygun on 2007-09-18
When you went through the installation process did it tell you if there were any suitible operating systems to import from?

---

### Post by alienexplorers on 2007-09-18
Did you get any error numbers or any text during the time the machine hung.

---

### Post by alienexplorers on 2007-09-18
You could try reloading grub from the directions in my sig line.

---

### Post by simcher on 2007-09-18
> **anemptygun said:**
> When you went through the installation process did it tell you if there were any suitible operating systems to import from?

yes it did... i imported... still stuck at the grub loading... please wait... and it just stop there... nothing happened....

---

### Post by simcher on 2007-09-18
> **alienexplorers said:**
> Did you get any error numbers or any text during the time the machine hung.

it didn't hung... it just stop loading from there... like it couldn't find anything...

---

### Post by simcher on 2007-09-18
what i see when preparing partition is 
/dev/sda
-sda1 NTFS  /media/sda1
-sda2 NTFS  /media/sda2

/dev/sdb
-sdb1 ext3 /
-sdb2 swap
-sdb3 NTFS /media/sdb1

after that it detected my windows xp professional and ask if i want to import anything over... and so i did...

---

### Post by simcher on 2007-09-18
the ubuntu i installed was a amd64 version (i am using athlon 64 3400+) my windows xp is 32bit... could that be the problem?

---

### Post by simcher on 2007-09-18
can someone help me here?

---

### Post by simcher on 2007-09-18
still looking for help...

---

### Post by anemptygun on 2007-09-18
> **simcher said:**
> the ubuntu i installed was a amd64 version (i am using athlon 64 3400+) my windows xp is 32bit... could that be the problem?

Yeah that would defidently not be the problem. I am not sure exactly whats going on, but since you have XP installed on a separate drive the first thing I would do is to put that hard drive in another computer and see if it will boot up or even be recognized.

---

