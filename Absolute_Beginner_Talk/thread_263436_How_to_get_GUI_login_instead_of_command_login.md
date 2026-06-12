---
title: "How to get GUI login instead of command login?"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by Tamil on 2006-09-23
I'm getting command login instead of usual GUI login. How to get it back?

---

### Post by bulldog on 2006-09-23
Tell a little more how this happened.

My christal ball is broken and I can't see why you can't use the GUI.

---

### Post by Tamil on 2006-09-23
> **bulldog said:**
> Tell a little more how this happened.Sorry, I don't know how this happened.

---

### Post by bulldog on 2006-09-23
Do you get an X-server warning? [blue box]

Did you update your kernel by any chance?

There must be something assuming you had a Desktop before this happened :D

---

### Post by chrisfay on 2006-09-23
What's the output from:

```
sudo gdm start
```
or 
```
sudo /etc/init.d/gdm start
```

---

### Post by Tamil on 2006-09-23
> **chrisfay said:**
> What's the output from:

```
sudo gdm start
``` I'm getting > sudo: gdm: Command not found

---

### Post by chrisfay on 2006-09-23
I'm assuming you're using Gnome/GDM...

Have you checked whether your GDM dameon is actually running?

```
ps aux | grep gdm
```

If no output, its not...

---

### Post by Tamil on 2006-09-23
> **chrisfay said:**
> I'm assuming you're using Gnome/GDM...

Have you checked whether your GDM dameon is actually running?

```
ps aux | grep gdm
```I'm using Kubuntu without any updates. I got the following:
> tamil 4805 0.0 0.0 2860 772 ttyl S+ 16:16 00:00 grp gdm

---

### Post by chrisfay on 2006-09-23
Oh, you're using kubuntu...Try:

```
sudo /etc/init.d/kdm start
```

Like Bulldog said, did you make any changes to your system or get any errors prior to this happening?

---

### Post by Tamil on 2006-09-23
> **chrisfay said:**
> Oh, you're using kubuntu...Try:

```
sudo /etc/init.d/kdm start
```Got this message. > Starting K Display Manager: kdm/usr/bin/kdm: error while loading shared libraries: /lib/tls/i686/cmov/libutil.so.1: Cannot read file data: Error 21

> **chrisfay said:**
> Like Bulldog said, did you make any changes to your system or get any errors prior to this happening?No.

---

### Post by chrisfay on 2006-09-23
> /lib/tls/i686/cmov/libutil.so.1: Cannot read file data: Error 21 

I think thats related to the libc6-i686 package..try:

```
sudo aptitude install libc6-i686
```

---

### Post by Tamil on 2006-09-23
> **chrisfay said:**
> I think thats related to the libc6-i686 package..try:

```
sudo aptitude install libc6-i686
```Got this message.
> aptitude: /lib/tls/i686/cmov/libpthread.so.0: version 'GLIBC_2.0' not found (required by aptitude)
aptitude: /lib/tls/i686/cmov/libpthread.so.0: version 'GLIBC_2.3.2' not found (required by aptitude)
aptitude: /lib/tls/i686/cmov/libpthread.so.0: version 'GLIBC_2.0' not found (required by /lib/tls/i686/cmov/libpthread.so.0)
aptitude: /lib/tls/i686/cmov/libpthread.so.0: version 'GLIBC_PRIVATE' not found (required by /lib/tls/i686/cmov/libpthread.so.0)

---

### Post by Tamil on 2006-09-25
Any suggestions?

---

### Post by lupin492 on 2006-09-25
Hi!  I´m having a similar problem with Gnome.
The PC starts with command line login.
The output to sudo gdm start is 'sudo: gdm: not found'
The output to sudo /etc/init.d/gdm start is nothing (returns prompt).
I found no 'gdm' file nowhere.
Furthermore, I tried to do: 'sudo apt-get upgrade gdm' but I´m behind a proxy (and I don´t know how to tell Ubuntu to redirect all http requests through address A.A.A.A:pppp (a specific port).  Ubuntu seems to have lost the proxy information configured before.
All this happened after the last update I made, including a kernel version upgrade (the next release for the same architecture), despite I´ve done upgrades like this one many times before.
Thanks in advance for any help.
Regards!

---

