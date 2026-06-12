---
title: "Terminal error?"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by 3wells on 2008-02-29
In terminal I get this message 'E: The package hl1230lpr needs to be reinstalled, but I can't find an archive for it.' (Printer driver)

The *.deb file gives me the error '...do not have permission tho install...'

The deb file is on my desktop, now what?

3

---

### Post by taurus on 2008-02-29
Did you remember to install it with sudo?

```
sudo dpkg -i** filename.deb**
```

---

### Post by 3wells on 2008-02-29
Thanks! However, got this mess of errors.... still stuck!

ross@ross-desktop:~$ sudo dpkg -i /home/ross/Desktop/hl1230lpr-1.1.2-1.i386.deb
[sudo] password for ross:
(Reading database ... 222643 files and directories currently installed.)
Preparing to replace hl1230lpr 1.1.2-1 (using .../hl1230lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1230lpr ...
/var/lib/dpkg/info/hl1230lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing /home/ross/Desktop/hl1230lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 3: /etc/init.d/lpd: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 /home/ross/Desktop/hl1230lpr-1.1.2-1.i386.deb
ross@ross-desktop:~$ 

3

---

### Post by seventhc on 2008-02-29
To make things easier, since it's  .deb file, just double click on it. It should open with a deb installer and install graphically. It will prompt you for a p/w and then install. Or have you already tried this and it failed??

Edit: never mind, just saw your last post

---

### Post by 3wells on 2008-02-29
Yup! Failed... grrr!

3

---

### Post by 3wells on 2008-02-29
Anyone? Trying to keep this on page one..

---

### Post by oldos2er on 2008-02-29
Check System, Administration, Software Sources, and make sure all repositories are enabled.

---

### Post by 3wells on 2008-02-29
> **oldos2er said:**
> Check System, Administration, Software Sources, and make sure all repositories are enabled.
everythig is checked...

---

### Post by forrestcupp on 2008-02-29
try
```
sudo apt-get update
```
then try to install again.

---

### Post by 3wells on 2008-03-01
Log in as 'root'

sudo dpkg --force-remove-reinstreq -P hl1230lpr >>> done! Synaptic & Updates work again!

Still get an error > E: kubuntu-docs: subprocess post-installation script returned error exit status 1

The Fix for this >

In synaptic, select kubuntu-docs, mark for complete removal, apply, reinstall.

Now - cleanup....

sudo apt-get autoclean
localepurge
deborphan > sudo deborphan | xargs sudo apt-get -y remove --purge

I'm just learning (it's my day off)! It's only been a week or so, playing with Linux, I think I've made some progress!

Damn it, the printer still does not work!

3

---

