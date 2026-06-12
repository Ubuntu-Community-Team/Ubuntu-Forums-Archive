---
title: "Backups - tools and tips?"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by CallMeDerek on 2007-08-06
Couple of questions on backups – 

I am running Kubuntu and am looking for a good backup solution that will allow me to backup workstations to a Samba share.  I have tried to use “Keep” and it does not want to see the Samba share for some reason.   Every other solution seems to require a lot of scripting.

Is there another recommend tool that would allow the following;
-Differential backups
-Compression
-Easy restore of data and configs

Second question is what to backup
User level directories contains a lot of “.app” structures.  Should I be faced with a full restore is it as easy as simply restoring the whole user directory to get back to the full config or should I assume I will need to reload packages and redo configs anyway and simply focus on data directories only?

I have searched and found a lot of scripting solutions, too complex for my neophyte status any advice on a good GUI tool would be appreciated.

~thanks in advance

---

### Post by hyper_ch on 2007-08-06
Those .folders in the user dirs are just the config files for other programs - you will also need to install the programs anew, but you won't have to configure them.

---

### Post by Inxsible on 2007-08-06
I haven't used it myself, but theres a tool called SBackup. Give that a try.

---

### Post by hyper_ch on 2007-08-06
I use my own backup script... I don't compress the backups as I make use of hardlinks, so I can make a full (snapshot style), incremental backup every 6h back to 90 days.

---

