---
title: "Best tool for Ubuntu / Windows secure file encryption?"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by satellitepro on 2008-01-16
I've been looking for a tool to safely encrypt / decrypt files (eg plain text files), similar to omziff for Windows (see [http://www.xtort.net/xtort-software/omziff/](http://www.xtort.net/xtort-software/omziff/)).

The use is to securely keep a file containing bank information, online banking account info, plus other online accounts & passwords for reference when memory fails.  I would want to be able to access the file from both my desktop and from Windows when not using my own pc.

Omziff takes a plain text file & encrypts / unencrypts it, but it's for Windows only.

For ubuntu (7.10), I've looked at seahorse and revelation, both available in repositories - but neither can help me with accessing an encrypted file from Windows.

Ideas / suggestions?

---

### Post by nikoPSK on 2008-01-16
I'd have to say gpg. :)

---

### Post by satellitepro on 2008-01-17
Thanks.

I know gpg is the technology to use, and thought seahorse was probably the front-end to use on Ubuntu.  Not having a good enough understanding of gpg, I couldn't figure how to use it.

I'll go do some more reading ... :confused:

---

### Post by hyper_ch on 2008-01-17
use a TrueCrypt container.

On Windows you get a GUI and for an ubuntu gui have a look here: [http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10](http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10)

There are other guis also for Linux but that's a step-by-step guide...

the container is a pre-made encrypted file. You have to set its file limit. With truecrypt you can then make it transparent and mount it as drive (in windows) or somehwere in the systempath (in linux). Once it's transparent and mounted you can put in other files and stuff meaning that you don't actually encrypt the contained files but the "bottle" (=container) itself.

---

### Post by kpkeerthi on 2008-01-17
[Encfs + cryptkeeper]("http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html")

---

### Post by starfry on 2008-01-17
I second Truecrypt!

---

### Post by hyper_ch on 2008-01-17
> **kpkeerthi said:**
> [Encfs + cryptkeeper]("http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html")

And how to use that on windoze?

---

### Post by zero-9376 on 2008-01-17
i don't know what the security is like but you could just use a zip file which is password protected. archive manager on ubuntu lets you use a password with zip and rars (possibly other formats this is all i have checked for windows compatability)

---

### Post by hyper_ch on 2008-01-17
zip passwords are weak.

---

### Post by zero-9376 on 2008-01-17
are rar files better? i know windows doesn't natively support rar but 7zip is a very nice little app for handling archives of this and many other formats. i was trying to provide a solution which would not require installation of software on windows as you may not always be able to do that.

---

### Post by Dr Small on 2008-01-17
I was going to suggest GPG like nikoPSK, but I don't know how you would decrypt / encrypt it on Windows. I assume there are Windows applications that are used to GPG, but I don't know what they are.

Anyhow, here is my tutorial on GPG:
[http://php.8ez.com/drsmall/blog/?p=209](http://php.8ez.com/drsmall/blog/?p=209)

Dr Small

---

### Post by hyper_ch on 2008-01-17
Well, for the ease of use I'd go with TrueCrypt for Windoze and Linux

---

### Post by nikoPSK on 2008-01-17
> **hyper_ch said:**
> Well, for the ease of use I'd go with TrueCrypt for Windoze and Linux

that's nice too. :) Gpg encryption on text files will make the text unreadable until you decrypt. ;)

---

### Post by hyper_ch on 2008-01-17
the containers are also unreadable until made transparent ;)

---

### Post by nikoPSK on 2008-01-17
yup.. it's fun to watch text get mashed... hehe here's an example of gpg signed with my public key:
```
-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.6 (GNU/Linux)
Comment: http://firegpg.tuxfamily.org

hQEOAxlZeJNLhiGpEAP/Vex0Nrj5UGXTdXnwCgwxKaZSX68/AlvC3Z6Rwd6D/ns+
rrOptTBDHnNtqFHK3YS9Qu0bMTS8vWOWwMDaLRBuBXKKwtnuQPUm53GTv1jV3lrL
nvYn6UABZQ095S2lA3M1lpF6aBhWJckaJYAiM1vdKeGpC8dTTf/LpEDj0CAutlEE
ALpz33ZGlyJs2VgqLhX2MMq9DB+LSmb12utVFtJFmyJ9lRpj5C6tU+Lxd3yPwGC3
Ipaw974/f9t3sUb967PYTkNBUlbD3B27IjiRrlhnw9QzcDEds/ahgEgmwYAr7Lb4
bZo+TMexlORJZykEJEotnmiweYf/Yi8hir74g5+7sUE30okBQNF5p9Ft1eGf/SVR
yaGvsfKquOMPIicwE52c/LpZfHzUaRCYqC8cyQ7UgtHiC40cNqM7kCPegcHo7hLK
gsAyku4PmSydkxoA0+ln6bB1D1TIX3TOihsgUvXsBGy+nMYjocxYeIutDn08czza
tJcmUpzrIhXc9NswE6QFFhE7m/Ol9ldaJzvEOQ==
=/8qW
-----END PGP MESSAGE-----

```

---

### Post by kevdog on 2008-01-17
Gpg runs on windows.  Gpg4win or through cygwin.

---

### Post by nikoPSK on 2008-01-17
ooh, fun... :D

---

### Post by satellitepro on 2008-01-18
Excellent! I've got as far as creating a key and encrypting a file on Ubuntu using GPG and seahorse / nautilus extensions. Not got as far as installing gpgee (gpg4win gui) and unencrypting in Windows yet, but definitely progress.  (thanks Dr Small for the tutorial!).

Never knew that TrueCrypt was available for linux, but looking at the step-by-step guide linked by hyper_ch, might be the ideal easy to use gui answer.

---

### Post by hyper_ch on 2008-01-19
I don't use a gui for my truecrypt container on my usb pendrive. I have a two small scripts for that ;)

---

