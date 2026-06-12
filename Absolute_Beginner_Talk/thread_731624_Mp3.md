---
title: "Mp3"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by miykle on 2008-03-22
G'Day ;  Just arrived from windows, hope to stay !!!
  Got a major drama trying to play MP3 files, Click on file >> Player opens >> says have to get appropriate codec >> ok  >> gets codec then says cant install codec it will conflict with other programs ??? codec is  gstreamer0.10-plugins-ugly
 Ubuntu  latest  7.10 (?)

 Any clues would be appreciated  Blessings Miykle

---

### Post by vikram on 2008-03-22
please see
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

### Post by oedha on 2008-03-22
make sure that you have pointed to a repository server
can be done :==> system - administration - software sources
then open terminal type :
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras
you'll get almost all codecs :)

---

