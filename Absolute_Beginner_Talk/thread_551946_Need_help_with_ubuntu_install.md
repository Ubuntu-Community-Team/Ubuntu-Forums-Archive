---
title: "Need help with ubuntu install"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by Alt3r3g0 on 2007-09-15
I am trying to install ubuntu 7.04 feisty fawn on my desktop and have tried both the regular and alternate .iso's but i keep getting the kernel attempting to kill itself

i figured it was probably hardware related

my desktop:

20GB western digital hard drive
Nvidia geforce4 mx 440
AMD 800Mhz processor
512MB RAM
American Megatrend motherboard from gateway

all my drivers are up to date but it still wont install

is ubuntu not compatible with my hardware or is it something else?

---

### Post by Dylock on 2007-09-15
with the specs you have ide suggest looking into the lighter versions, maybe xubuntu

but i dont know what would be causing your problems

---

### Post by Sef on 2007-09-15
> with the specs you have ide suggest looking into the lighter versions, maybe xubuntu


Incorrect.  Ubuntu should work just fine.  


> with the specs you have ide suggest looking into the lighter versions, maybe xubuntu


1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")?

2) Did you burn the iso at 4x or less?

3) Check the disks for errors?

4) Has the Live CD run ok?

---

### Post by uglykigjoe on 2007-09-15
did you try to run a Live session.
If it works in Life session, there shouldnt be a problem to install.
:)

edit..
opsss.. someone already mentioned this..

---

### Post by Alt3r3g0 on 2007-09-16
i cant get the live sessions to work...the kernel attempts to kill itself before the session loads

i checked md5sum

i will try to reburn the cd at 4x. i believe i burned it at 8x so ill see what happens

---

### Post by Alt3r3g0 on 2007-09-16
still a no go. live cd starts running then stops at:

[  169.029015] Call Trace:
[  169.029116] ==================
[  169.029171] Code: Bad EIP value.
[  169.029296] EIP: [<bfcfdcc7>] 0xbfcfdcc7 SS:ESP 0068dff85f3a
[  169.029432]  <0>Kernel Panic - not syncing: attempted to kill init!

and then hangs on:
[  169.029598]  _

---

