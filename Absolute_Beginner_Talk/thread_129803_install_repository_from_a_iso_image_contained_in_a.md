---
title: "install repository from a iso image contained in a dvd"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-02-14
i got a dvd with some programs and in particular with some repository of ubuntu. I found it in a linux magazine. I want to install softwares of repository because i got a 56k modem, but the problem is that the repository are in an iso image. How can i get the install cd from the iso image or how can i install that sofwares without creating an install cd?

thanks

---

### Post by mednamot on 2006-02-14
from a completely separate topic:

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.iso /mnt/iso
cd /mnt/iso
ls -la

it's from [Here]("http://www.ubuntuforums.org/showthread.php?t=128387&page=2")

---

### Post by ubunlilluz on 2006-02-15
[QUOTE=mednamot]from a completely separate topic:

sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.iso /mnt/iso
cd /mnt/iso
ls -la

it's from [Here]("http://www.ubuntuforums.org/showthread.php?t=128387&page=2")[/QUOTE]

i've  followed the above istrunctions.
then i added the new repository as personal: deb file:/mnt iso/
but if i try to reload i got that the load of local repo fault

lillux@lilluxsestum:/mnt/iso$ sudo apt-get update
Ign file: iso/ Release.gpg
Ign file: iso/ Release
Ign file: iso/ Packages

 and if i try to install software it is done by internet repos.
what's wrong?

---

### Post by ubunlilluz on 2006-02-16
nobody can help me?:cry: :cry: :cry:

---

### Post by ubunlilluz on 2006-02-21
i burst it in a cd and it worked

---

