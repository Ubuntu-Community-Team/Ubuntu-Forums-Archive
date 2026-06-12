---
title: "need help...im new..."
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Sean14 on 2007-07-09
whenever i try to open certain programs...this pops up...


This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

anyone that could help???:(

---

### Post by hanzj on 2007-07-09
I'm a newbie, too, and I can't diagnose the problem completely, but the experts here may be interested in seeing what's in your sources.list file.

So do this:
1. Press Alt + F2 key.
2. Type: gksudo gedit /etc/apt/sources.list
3. Copy that and paste here.

---

### Post by Rocket2DMn on 2007-07-09
Sounds like you're just missing some modules and/or libraries for certain Ubuntu apps.  Have you tried running those commands in terminal?  They should force all the dependencies to get checked and updated.
If the command fails to run because of permissions, run the command
```
chmod 644 /etc/apt/sources.list
```
then try again.

---

### Post by wj32 on 2007-07-09
try and run

sudo apt-get install -f

if that command gives a segfault and says /var/lib/dpkg/available is corrupted or something,

sudo mv /var/lib/dpkg/available /var/lib/dpkg/available_old

---

### Post by Church.Cameron on 2007-07-09
reinstall that shizznick, that is all....


:popcorn: agian popcorn anyone....

---

### Post by Rocket2DMn on 2007-07-09
> **Church.Cameron said:**
> reinstall that shizznick, that is all....


:popcorn: agian popcorn anyone....

Reinstall is kind of a last ditch effort.  It can be very annoying to have to go through and reconfigure everything to your preferences again, not to mention restoring your data from your backups (you DO keep backups, yes?)

---

