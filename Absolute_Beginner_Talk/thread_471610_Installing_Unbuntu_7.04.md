---
title: "Installing Unbuntu 7.04"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Sailor-Moon on 2007-06-12
hi
i have a HP pavilion 754.uk model witgh a p4 2.8 cpu

i had a blank hard drive, no operating system

i downloaded the disk image from this site, and tried installing

i get the load screen with the options, i click on install or start in safe graphics and i get this error message

busybox v 1.1.3 (debian 1:1.1.3-3ubuntu3) built-in shell (ash)
enter 'help' for a list of built in  commands.

/bin/sh: can't access tty; job control turned off
(initramfs)


has anyone got any ideas whats causing this and how to fix it please.
also i'm not the best with computers so please make it as simple as possible, thank you

---

### Post by 3rdalbum on 2007-06-12
This is usually caused by a bad burn. You must burn the disc at 8x speed or lower.

---

### Post by digitaldoug on 2007-06-13
> **Sailor-Moon said:**
> hi
i have a HP pavilion 754.uk model witgh a p4 2.8 cpu

i had a blank hard drive, no operating system

i downloaded the disk image from this site, and tried installing

i get the load screen with the options, i click on install or start in safe graphics and i get this error message

busybox v 1.1.3 (debian 1:1.1.3-3ubuntu3) built-in shell (ash)
enter 'help' for a list of built in  commands.

/bin/sh: can't access tty; job control turned off
(initramfs)


has anyone got any ideas whats causing this and how to fix it please.
also i'm not the best with computers so please make it as simple as possible, thank you



I have the exact same problem with my new HP6500t (core 2 duo 2GHz).  I have tried both the 32 and
64 bit desktop 7.04 iso and both CD's have been verified with MD5SUM.

Digitaldoug

---

### Post by Sailor-Moon on 2007-06-13
disk was written at 8X and a friend of mine used the same disk and had no trouble

---

### Post by dustice on 2007-06-14
Try this thread:

[http://ubuntuforums.org/showthread.php?t=458189&highlight=can%27t+access+tty](http://ubuntuforums.org/showthread.php?t=458189&highlight=can%27t+access+tty)

---

### Post by Sailor-Moon on 2007-06-15
thank you i think its worked, am installing as we type!

for the other person with problems the solution which worked for me was this

The first solution is (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'all_generic_ide'


dont panic if theres no activerty for a fewmins while loading

---

### Post by Sailor-Moon on 2007-06-15
or installing, mine was stuck on 5% while formatting for about 20 mins

---

