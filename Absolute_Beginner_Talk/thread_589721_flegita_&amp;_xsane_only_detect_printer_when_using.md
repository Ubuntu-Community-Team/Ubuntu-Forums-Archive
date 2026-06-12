---
title: "flegita &amp; xsane only detect printer when using 'sudo'"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-10-24
I have  Brother MFC-8440 installed and running with no problem.

The MFC is a printer, copier, scanner, fax machine, etc. and it's not your average $50 printer.

I've been trying to get my scanner to work since 5.10 and haven't been able to UNTIL I ran flegita and xsane as root! This is a fresh install of Gutsy (7.10) so all of my old install methods should have been wiped. This means that the new printerdrake print system that has been set up has actually found my scanner. That or the Brother library that I installed (that usually is corrupt) worked properly.

Anyway, my question is, how do I run the scanner without running as root!? I have other people on this computer that does have sudo permissions.

**DOESN'T WORK**
```
flegita
```
```
xsane
```

**WORKS CORRECTLY**
-- EDIT: sort of... scan keeps looping and doesn't stop
```
sudo flegita
```
```
sudo xsane
```

Weird huh!?

---

### Post by sphm on 2007-10-24
Hi,
maybe you can add these lines in your sudoers

First type:

```
# visudo
```

Than add these lines: 

```
%users ALL=NOPASSWD:/usr/bin/flegita
%users ALL=NOPASSWD:/usr/bin/xsane
```

This is kinda partial solution, but at least all users will be able to run these programs with sudo

---

### Post by altonbr on 2007-10-24
Well, now that I've actually used flegita using sudo, it doesn't stop scanning!

It keeps scanning in a loop without asking me to click 'next'.

I'll try your hack but I was hoping we could do something to the device to make it available to all users.

---

