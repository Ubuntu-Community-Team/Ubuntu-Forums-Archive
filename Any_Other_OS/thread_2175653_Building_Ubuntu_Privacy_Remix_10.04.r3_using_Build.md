---
title: "Building Ubuntu Privacy Remix 10.04.r3 using Buildscript doesn't work"
date: 2013-09-20
forum: Any Other OS
---

### Post by BzrtncE on 2013-09-20
Hey! 

I'm Trying to build the distro Ubutu Privacy Remix ([www.privacy-cd.org](www.privacy-cd.org)) using their buildscript ([https://www.privacy-cd.org/en/tutorials/build-your-own-cd](https://www.privacy-cd.org/en/tutorials/build-your-own-cd))
But unfortunatly the Buildscript 10.04.r3 doesn't work for me (tried on Debian 32/64 bit, Ubuntu 12.04 32 Bit)
Seems that kompiling the new Kernel doesn't work.

Heres the code (sorry for the german language, hope it serves)


 ---

 XXX@XXX:~$ sudo '/home/XXX/ubuntu-10.04.r3.sh' -n -V
Note: you will most likely be required to enter your sudo password  multiple times while this script runs. If you do not like this, increase  the timeout in /etc/sudoers (man sudoers(5)).
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.
Statusinformationen werden eingelesen.... Fertig
genisoimage ist schon die neueste Version.
kernel-wedge ist schon die neueste Version.
squashfs-tools ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
mount: warning: /home/XXX/mnt seems to be mounted read-only.
Parallel unsquashfs: Using 4 processors
127481 inodes (130105 blocks) to write
 [====================================================================================================-] 130105/130105 100%
created 95787 files
created 15499 directories
created 30852 symlinks
created 87 devices
created 0 fifos
gpgv: Schlüsselblockhilfsmittel`/root/.gnupg/trustedkeys.gpg': Fehler beim Öffnen der Datei
gpgv: Unterschrift vom Fr 19 Okt 2012 17:11:34 CEST mittels RSA-Schlüssel ID FDCE24FC
gpgv: Unterschrift kann nicht geprüft werden: Öffentlicher Schlüssel nicht gefunden
dpkg-source: Warnung: Fehler beim Überprüfen der Signatur von ./linux-lts-backport-oneiric_3.0.0-27.44~lucid1.dsc
dpkg-source: Information: linux-lts-backport-oneiric wird nach /home/XXX/kernel extrahiert
dpkg-source: Information: linux-lts-backport-oneiric_3.0.0-27.44~lucid1.tar.gz wird entpackt
patching file libata-core.c
Hunk #1 succeeded at 2183 (offset -226 lines).
cp: Aufruf von stat für „/home/XXX/edit/tmp/config.flavour.upr“ nicht möglich: Datei oder Verzeichnis nicht gefunden
Exiting /home/XXX/ubuntu-10.04.r3.sh with 1
XXX@XXX:~$ sudo '/home/XXX/ubuntu-10.04.r3.sh' -n -V -c
Note: you will most likely be required to enter your sudo password  multiple times while this script runs. If you do not like this, increase  the timeout in /etc/sudoers (man sudoers(5)).
dpkg-source: Fehler: Entpackziel existiert: /home/XXX/kernel
Exiting /home/XXX/ubuntu-10.04.r3.sh with 255
XXX@XXX:~$

---

### Post by SamTarling on 2013-09-20
Affected by [Bug #1228071]("https://bugs.launchpad.net/upr/+bug/1228071")?

---

### Post by ibjsb4 on 2013-09-20
I tried to look at the buildscript, but all I get is

[ATTACH=CONFIG]246359[/ATTACH]

So anyhow. from your description, are you trying to use a script built for ubuntu 10.04 on a 12.04 ubuntu install?

---

### Post by BzrtncE on 2013-09-20
> **SamTarling said:**
> Affected by [Bug #1228071]("https://bugs.launchpad.net/upr/+bug/1228071")?

Looks like :p

> **ibjsb4 said:**
> I tried to look at the buildscript, but all I get is

[ATTACH=CONFIG]246359[/ATTACH]


So anyhow. from your description, are you trying to use a script built for ubuntu 10.04 on a 12.04 ubuntu install?

Hm maybe it works like [this?]("https://www.privacy-cd.org/en/tutorials/build-your-own-cd") 

Jes im trying to buildl an ubuntu 10.04 on an Ubuntu 10.04 isnt that possible?

---

### Post by ibjsb4 on 2013-09-20
> **BzrtncE said:**
> Jes im trying to buildl an ubuntu 10.04 on an Ubuntu 10.04 isnt that possible?

10.04 has reached end of life and no longer supported.  I recommend 12.04 which will be supported till 2017.

---

