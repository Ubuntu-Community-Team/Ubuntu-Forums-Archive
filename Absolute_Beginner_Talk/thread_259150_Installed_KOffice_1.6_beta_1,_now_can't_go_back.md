---
title: "Installed KOffice 1.6 beta 1, now can't go back"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by Books on 2006-09-17
I saw that KOffice 1.6 beta1 was out and I use Krita and Kexi so I thought I would try it. I followed the directions at [http://kubuntu.org/announcements/koffice-16beta1.php](http://kubuntu.org/announcements/koffice-16beta1.php)

After it installed Kexi wouldn't start, neither would Krita.

I took out the "deb [url]http://kubuntu.org/packages/koffice-16beta1 dapper main" from my repositories list and uninstalled the broken packages.

I updated the list of packages and tried to re-install but they won't. Adept says that the packages are "broken" and it won't get them.

The needed files, now missing, are:

kexi
kivio
koffice-libs
koshell
kplato
krita
kspread
kword

What do I do? Thank you!

Books

---

### Post by Books on 2006-09-17
Ok, here's the latest.

I found out that koffice-data didn't uninstall so I re-enabled the "deb [url]http://kubuntu.org/packages/koffice-16beta1 dapper main" in my repositories list and uninstalled koffice-data.

I then disabled the deb and tried to re-install KOffice. It showed all the packages ready to install except "koffice", which said "BROKEN"

I also am now seeing that krita-data didn't uninstall, so when I select to remove it, Adept wants to install koffice-libs and koffice-data. What gives???

I wish I had never tried the KOffice 1.6 beta1. It is BADLY broken!

Books

---

### Post by Qrk on 2006-09-17
Have you tried 

```
sudo apt-get -f install
```?

If not, you should. If you have, you should post more information here. Paste the actual error message and you shouldn't have a problem getting help.

---

### Post by Books on 2006-09-17
> **Qrk said:**
> Have you tried 

```
sudo apt-get -f install
```?

If not, you should. If you have, you should post more information here. Paste the actual error message and you shouldn't have a problem getting help.

Thanks, Qrk!

First, what is *sudo apt-get -f install* ? I've been using Kubuntu since December but there is still SO much I don't know I consider myself a "newbie." :-) 

Second, I think I fixed it... I think. I'll explain what I did in case someone else is having the same difficulty after trying koffice-16beta1. What happened is that when I uninstalled the 1.6 beta it left a lot of the "-data" files of the programs still on there. These were the KOffice 1.6 versions of the files. When I tried to re-install the 1.5 versions there were conflicts. The following 1.6 files were left, and I think one or two more, if I remember right...

[I]krita-data
kivio-data
kword-data[/I]

What you have to do is make sure the "deb [url]http://kubuntu.org/packages/koffice-16beta1 dapper main" is enabled in your repositories list and uninstall them one at a time. You have to get them all or KOffice 1.5 won't re-install back. Once you have all the "-data" files uninstalled, then disable the deb source in your repositories and fetch the updates so your list is refreshed. Then try re-installing KOffice 1.5. It *finally* worked for me and I tried out a few of the apps and they appear to be working.

My advice to fellow Kubuntu users: Wait until Beta 2 to try the new KOffice 1.6.

Books

---

