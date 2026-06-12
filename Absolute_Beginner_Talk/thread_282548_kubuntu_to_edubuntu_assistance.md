---
title: "kubuntu to edubuntu assistance"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by benner on 2006-10-22
i have kubuntu installed.  i want to replace it with the new edubuntu 6.10.  i wanted to wipe the drive and start fresh with a new install but both of the CD-ROM's that i have don't want to read any of the unbuntu installer discs that i have (i have tried 5 different discs, all of which worked fine on my other 2 machines)  so what commands do i type in to apt-get to replace the OS?  I tried 'sudo apt-get install edubuntu' and that wasn't it.  thanks in advance for your guidance folks...  help is always appreciated by us new guys (even if we occasionally don't show it)

---

### Post by catlett on 2006-10-22
```
sudo aptitude update
```
```
sudo aptitude install edubuntu-desktop
```
```
sudo aptitude remove kubuntu-desktop
```
Do it in that order to be safe. After you finish do a dist-upgrade to make sure you have the latest version
```
sudo aptitude dist-upgrade
```

---

