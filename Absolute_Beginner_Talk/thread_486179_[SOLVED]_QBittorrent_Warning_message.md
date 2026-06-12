---
title: "[SOLVED] QBittorrent Warning message"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-06-27
I used this link to add the qBittorrent sources to my sources.list.

But when I try to install qBittorrent thru aptitude it gives me the following warning. I was concerned because I have never seen such a warning message before for any other reps that I added.

```
sudo aptitude install qbittorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  libboost-program-options1.33.1 libboost-regex1.33.1 libmysqlclient15off 
  libpq5 libqt4-core libqt4-gui libqt4-qt3support libqt4-sql libsqlite0 
  mysql-common qt4-qtconfig rblibtorrent1 
The following packages have been kept back:
  compiz-core compiz-gnome compiz-plugins 
The following NEW packages will be installed:
  libboost-program-options1.33.1 libboost-regex1.33.1 libcurl3 
  libmysqlclient15off libpq5 libqt4-core libqt4-gui libqt4-qt3support 
  libqt4-sql libsqlite0 mysql-common qbittorrent qt4-qtconfig rblibtorrent1 
0 packages upgraded, 14 newly installed, 0 to remove and 3 not upgraded.
Need to get 12.6MB of archives. After unpacking 31.2MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  qbittorrent rblibtorrent1 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No":
```Will it be ok to say yes and install it anyway?

---

### Post by Inxsible on 2007-06-28
Bump

---

### Post by paulg on 2007-06-28
That's a normal message for repositories outside the 'Ubuntu' realm. It's the OSes way of saying, "are you sure you want to trust these people? It's not on my "verified" list." 

Your first post didn't have the repository so I cannot comment one way or another. Anything outside the official repositories always carries a risk. It's a small risk but you should be aware it's there. Anyway, if you trust the source or whoever directed you to the repository then it's probably alright. There is a way to add the gpg signature to your repository so it does not ask you every time but unfortunately I don't remember how to do it or where to find said site's signature.

---

### Post by Inxsible on 2007-06-28
> **paulg said:**
> That's a normal message for repositories outside the 'Ubuntu' realm. It's the OSes way of saying, "are you sure you want to trust these people? It's not on my "verified" list." 
 
Your first post didn't have the repository so I cannot comment one way or another. Anything outside the official repositories always carries a risk. It's a small risk but you should be aware it's there. Anyway, if you trust the source or whoever directed you to the repository then it's probably alright. There is a way to add the gpg signature to your repository so it does not ask you every time but unfortunately I don't remember how to do it or where to find said site's signature.
 
Ok. Thanks for the info. 
 
I was just wondering because I have put other third party reps like videolan, tuxfamily etc. in my sources.list and it never asked me anything like that. 
 
Maybe i downloaded the key for it, I dont quite rbr now.

---

