---
title: "Totem DVD problem"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-04-16
1) insert dvd
2) totem opens
3) "AN ERROR OCCURED: could not read from resource"
4) (TBA)

---

### Post by wolfen69 on 2008-04-16
if you are using gutsy:
```
sudo apt-get install libdvdread
```then
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O - | sudo apt-key add - && sudo apt-get update
```
then
```
sudo apt-get install libdvdcss2
```

---

### Post by WalmartSniperLX on 2008-04-16
It's because Ubuntu does not come with the libraries needed to read copyrighted dvd videos. This should help you get your dvds working. 

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvd%29)

---

### Post by manicmailman on 2008-04-17
thanks that got it working!

this is just a minor thing now.. but when i put in the dvd, totem still thinks its a cd and it doesnt have the "menu" that comes with a dvd... it just plays it....

---

