---
title: "Updating Clamav"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-01-29
Hi,

Could someone kindly tell me how to update my Clamav anti-virus data base via the terminal.  I tried in the GUI, but it keeps telling me I must be in root.  The exact code would be nice, so I can copy and paste.

Thank you very much.:D

---

### Post by an.echte.trilingue on 2007-01-29
just put "sudo" in front of whatever you input before.

---

### Post by Norfolk 'n' Good on 2007-01-29
Thanks.  I know about the sudo or sudo -s command, I just don't know what to write after that...  
for example, sudo apt-get clamav data?  

I'm still a bit Ubuntu/Linux illiterate.

---

### Post by an.echte.trilingue on 2007-01-30
```
sudo freshclam 
```
will update your database
```
sudo clamscan -ir /home
```
will scan your home directory.  Scanning "/" does not do much good.  If you suspect that your system itself is comprimised, you should run clamav from a livecd like backtrack and scan the partition it is on that way.  See also chkrootkit and rkhunter.

By the way, I know you are new here, do you know how to read the manual pages?  They are helpful.

Take care,
-mat

---

