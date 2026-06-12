---
title: "Printer driver trouble"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by Jewden on 2006-02-11
Hello, I've been using ubuntu for some weeks now and i really like it. But when i tried to install printer drivers to my Brother MFC9180 something went wrong. Since then, every time i have tried to apt-get something, it doesn't work, it only   says that the package mfc9180lpr has to be reinstalled.  

I've tried to remove the package, but it doesnt work either. 

Does anyone have any idea to solve this problem??

---

### Post by Lord Illidan on 2006-02-11
Can you type:

```
sudo apt-get -f install
``` in a terminal, and display what it says here, before pressing 'Y'?

---

### Post by Jewden on 2006-02-11
it says that the package mfc9180lpr has to be reinstalled, but i cant find any archieve for it.   (i have ubuntu in swedish so i translated it)

---

### Post by starsnake on 2007-01-04
hello,
try the following in the terminal:

yourname@yourcomputer:~$ sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd

yourname@yourcomputer:~$ sudo dpkg -i mfc9180lpr-1.1.2-1.i386.deb

(Lese Datenbank ... 98749 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereiten zum Ersetzen von mfc9180lpr 1.1.2-1 (durch mfc9180lpr-1.1.2-1.i386.deb) ...
Entpacke Ersatz für mfc9180lpr ...
* Restarting Common Unix Printing System: cupsd [ ok ]
Richte mfc9180lpr ein (1.1.2-1) ...
mkdir: kann Verzeichnis „/var/spool/lpd/MFC9180“ nicht anlegen: No such file or directory
chown: Zugriff auf „/var/spool/lpd/MFC9180“ nicht möglich: No such file or directory
chgrp: Zugriff auf „/var/spool/lpd/MFC9180“ nicht möglich: No such file or directory
chmod: Zugriff auf „/var/spool/lpd/MFC9180“ nicht möglich: No such file or directory
* Restarting Common Unix Printing System: cupsd 

After that at least your problem was solved.
The printer did not work anyhow.
BR
Henning

---

