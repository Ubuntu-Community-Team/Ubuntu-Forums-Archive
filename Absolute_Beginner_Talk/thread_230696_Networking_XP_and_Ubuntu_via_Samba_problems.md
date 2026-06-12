---
title: "Networking XP and Ubuntu via Samba problems"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by Haverhill Dave on 2006-08-06
Iinstalled Ubuntu a few days ago on my PC and I wantto set up a network between my only linux machine and 5 windows XP machines. Yesterday my friend and I managed to access the XP pcs shared files and send a document for printing through the printer conected to the XP machine (it printed an ubuntu test page).
Apparently I dont have Samba server files on my computer, and I tries downloading them from [http://us3.samba.org/samba/ftp/Binar...ebian/samba/3/](http://us3.samba.org/samba/ftp/Binar...ebian/samba/3/)
Some of them worked, but others said "Error: Dependency is not satisfiable:..."
Please ca nsomeone help?

---

### Post by Najand on 2006-09-05
> **Haverhill Dave said:**
> Iinstalled Ubuntu a few days ago on my PC and I wantto set up a network between my only linux machine and 5 windows XP machines. Yesterday my friend and I managed to access the XP pcs shared files and send a document for printing through the printer conected to the XP machine (it printed an ubuntu test page).
Apparently I dont have Samba server files on my computer, and I tries downloading them from [http://us3.samba.org/samba/ftp/Binar...ebian/samba/3/](http://us3.samba.org/samba/ftp/Binar...ebian/samba/3/)
Some of them worked, but others said "Error: Dependency is not satisfiable:..."
Please ca nsomeone help?

Hmm, No need to download the packages from samba homepage. Just use apt to get all packages and depedecies easily.... Using the following command:
```
apt-get install samba samba-common smbldap-tools
```

---

