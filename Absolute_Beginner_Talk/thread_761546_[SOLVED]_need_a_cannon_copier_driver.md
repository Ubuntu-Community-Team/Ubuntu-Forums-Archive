---
title: "[SOLVED] need a cannon copier driver"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by jasonk on 2008-04-21
hi all,
we just got a cannon ir-c3220 here at this business.  the problem is, i'm having a really hard time finding a driver that will work for it.  anyone know where i can go?  getting kind of desperate

---

### Post by boomdiddly on 2008-04-21
[http://www.canon.com.au/products/multifunctionals/multifunctional_digital_devices/irc3220_drivers.aspx](http://www.canon.com.au/products/multifunctionals/multifunctional_digital_devices/irc3220_drivers.aspx)

Bottom driver is listed as:

**PostScript Printer Driver v1.50**
Contains 32bit and 64bit for x86 rpm packages and 32bit Debian package.
For Linux

hope this helps.

Paul

---

### Post by jasonk on 2008-04-21
call me newbie.  i downloaded that driver before, but i can't figure out how to install it.  when ever i do i get this error 

Error: Dependaency is not stisfiable: libcupsys2-gnutls10

i searched for that file in the synaptic file manager, but couldn't find it.  so i still don't know what to do.

---

### Post by wolfen69 on 2008-04-21
here [http://packages.ubuntu.com/gutsy/libcupsys2-dev](http://packages.ubuntu.com/gutsy/libcupsys2-dev)

---

### Post by jasonk on 2008-04-21
ok, i followed your link and installed libcupsys2-dev with all the dependencies, but still got that same error

---

### Post by boomdiddly on 2008-04-21
> **jasonk said:**
> ok, i followed your link and installed libcupsys2-dev with all the dependencies, but still got that same error

You don't need the dev files

The problem right now is, this thing called 'libcupsys2' has been renamed. Your printer drivers think it should be called 'libcupsys2-gnutls10' (old name). Your computer thinks it should be called 'libcupsys2'.

I don't speak French, but I found this link:
[http://ftp.fr.debian.org/debian/pool/main/c/cupsys/libcupsys2-gnutls10_1.2.7-4_all.deb](http://ftp.fr.debian.org/debian/pool/main/c/cupsys/libcupsys2-gnutls10_1.2.7-4_all.deb)

on this site references the exact package your driver thinks you need to install (not required reading, just there if you're interested):
[http://doc.ubuntu-fr.org/materiel/imprimantes_canon_ixxx](http://doc.ubuntu-fr.org/materiel/imprimantes_canon_ixxx)

Click the first link above, save that package to your desktop then open it with the gDebi package installer.

Hopefully, once that is installed, it can trick your printer drivers into working!

Let me know how this goes

Paul

---

### Post by jasonk on 2008-04-22
thank you guys for all of your help.

boomdiddly - i converted the rpms with alien and that worked for the install on my machine. i have to install it on 3 more though, so i will try it with the link you sent and see if that works too.  thanks for again for your help!

---

### Post by mdr on 2008-04-23
Alternatively find the ppd driver on the install disks
and use this with cups.

I have done this with my ir2200 to good effect.

---

### Post by Malikius on 2008-04-24
For a Cannon PIXMA MP530 driver that will work with Linux (Ubuntu) It works beautifully in windows. Would love to be able to use the software on the CD that came with it. It included Omnipage. I have tried doing it via Crossover but got an error. Please advise.

---

### Post by jasonk on 2008-05-20
boomdiddly, the link you gave me worked, but i found that more of the driver options work if i just installed from the rpm after using alien to convert it.  thanks for all of your help guys!

---

