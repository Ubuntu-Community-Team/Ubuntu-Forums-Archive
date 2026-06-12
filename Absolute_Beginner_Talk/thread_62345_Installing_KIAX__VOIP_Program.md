---
title: "Installing KIAX // VOIP Program"
date: 2005-09-04
forum: Absolute Beginner Talk
---

### Post by Dutch on 2005-09-04
I'm trying to install KIAX and after several hours not to kill the PC

attempt 1

root@Paul:/tmp # tar -xvzpf kiax-0.8.4-bin.tar.gz
kiax-0.8.4-bin/
kiax-0.8.4-bin/kiax
kiax-0.8.4-bin/i18n/
kiax-0.8.4-bin/i18n/kiax_bg.qm
kiax-0.8.4-bin/i18n/kiax_de.qm
kiax-0.8.4-bin/i18n/kiax_en.qm
kiax-0.8.4-bin/i18n/kiax_fr.qm
kiax-0.8.4-bin/i18n/kiax_pl.qm
kiax-0.8.4-bin/i18n/kiax_pt.qm
kiax-0.8.4-bin/i18n/kiax_mk.qm
kiax-0.8.4-bin/icons/
kiax-0.8.4-bin/icons/contact.png
kiax-0.8.4-bin/icons/dial.png
kiax-0.8.4-bin/icons/failed.png
kiax-0.8.4-bin/icons/hangup.png
kiax-0.8.4-bin/icons/hold.png
kiax-0.8.4-bin/icons/incoming.png
kiax-0.8.4-bin/icons/missed.png
kiax-0.8.4-bin/icons/outgoing.png
kiax-0.8.4-bin/icons/resume.png
root@Paul:/tmp # cd kiax-0.8.4-bin/kiax
bash: cd: kiax-0.8.4-bin/kiax: Geen map
root@Paul:/tmp # cd kiax-0.8.4-bin/
root@Paul:/tmp/kiax-0.8.4-bin # ./configure
bash: ./configure: Onbekend bestand of map

second attempt

root@Paul:/tmp # ls
Acro000bBv0tU  gconfd-root     kiax-0.8.4-bin                    mapping-paul
fileNcseLh     gpg-rhRuUL      kiax-0.8.4-bin.tar.gz             mcop-paul
fr-SvCKF4      kde-paul        ksocket-paul                      orbit-paul
fr-xptloy      keyring-BuZbsT  libgksu1.2-86UxYq                 orbit-root
gconfd-paul    kiax            Mapje voor kiax-0.8.4-bin.tar.gz  ssh-CcqfLG7366
root@Paul:/tmp # chmod +x kiax-0.8.4-bin
root@Paul:/tmp # ./ kiax-0.8.4-bin
bash: ./: is a directory
root@Paul:/tmp # ./kiax
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
zo sep 4 16:20:30 2005 Using IAXClient ver. CVS-2005/04/13-20:14
zo sep 4 16:20:31 2005 IaxWrapper::iaxc_initialize() result = -1
Error message:cannot initialize iaxclient!

Exitting application. Possible reason: Device initialization failed.


Now what ?

---

### Post by Jussi Kukkonen on 2005-09-04
> root@Paul:/tmp # cd kiax-0.8.4-bin/
root@Paul:/tmp/kiax-0.8.4-bin # ./configure
bash: ./configure: Onbekend bestand of map

Here you hadn't downloaded the source package but the binary (evident from the name kiax-0.8.4-**bin**), but tried to **./configure** anyway.

> root@Paul:/tmp # chmod +x kiax-0.8.4-bin
root@Paul:/tmp # ./ kiax-0.8.4-bin
bash: ./: is a directory
root@Paul:/tmp # ./kiax

Dont know what **./kiax** here was but I can see you never executed **kiax-0.8.4-bin**. The correct command is:
```
./kiax-0.8.4-bin
```
(note lack of space char after slash)


**As general advice**:
You'll need to either A) download and install a debian package or B) d/l and install a binary OR C) download the source and follow the compilation instructions. 

Using the debian package might work. Then again it might not. I wouldn't try this first.

Compiling might be difficult if you don't know what you are doing -- there are some dependencies (QT and iaxclient at least). The last error message sound like you have a compiled version without iaxclient installed...

so I suggest you try installing the binary again.

---

