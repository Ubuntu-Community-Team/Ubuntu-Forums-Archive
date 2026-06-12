---
title: "Automatix2: restricted extras and codecs install error"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by epidemiks on 2008-01-20
Hi, I'm trying to install restricted extras and codecs with automatix2 and its bringing back an 'apt-based error' and not downloading them, it downloaded other packages, just not this one... do i need to update apt or what am i doing wrong?
Cheers

---

### Post by Kilz on 2008-01-20
> **epidemiks said:**
> Hi, I'm trying to install restricted extras and codecs with automatix2 and its bringing back an 'apt-based error' and not downloading them, it downloaded other packages, just not this one... do i need to update apt or what am i doing wrong?
Cheers

Please dont use automatix, if you need the codecs[ just read this page]("https://help.ubuntu.com/community/RestrictedFormats"). All the files are already in the repositories.

---

### Post by epidemiks on 2008-01-20
Righto, whats wrong with automatix? A friend recommended it.. 
Doesn't seem to be in the reposiories... I think I may have messed up my list. Is there a good comprehesive sources list floating aroud the internet I can copy/paste?

---

### Post by epidemiks on 2008-01-20
ah, I just read why automatix is bad. i think i might remove it...

---

### Post by Faud on 2008-01-21
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)

---

### Post by epidemiks on 2008-01-21
Ok, silly question #2: how do uninstall automatix? It doesn't seem to appear in add/remove

---

### Post by Dope on 2008-01-22
> **epidemiks said:**
> Ok, silly question #2: how do uninstall automatix? It doesn't seem to appear in add/remove

This is for automatix2, but I'm gonna guess it'll be the same for automatix:


Automatix2 can be removed as follows:

sudo apt-get remove automatix2

This is where I got that from:
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.10_AMD64.2C_i386_.28Gutsy.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.10_AMD64.2C_i386_.28Gutsy.29)

---

### Post by erfahren on 2008-01-22
this shows how to set up your /etc/apt/sources.list - [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)
(sometimes that link doesn't go directly to the section - so just scroll down in the contents a little to the 
"1.2.1 How to add extra repositories" section

(make sure you do the part where it says to add the key for Medubuntu)

---

