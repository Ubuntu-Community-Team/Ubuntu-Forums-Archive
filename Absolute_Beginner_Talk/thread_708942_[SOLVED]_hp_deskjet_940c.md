---
title: "[SOLVED] hp deskjet 940c"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by rockerphil on 2008-02-26
ok, i am currently trying to install the driver for my hp deskjet 940c, the self extracting file does fine for the first few steps and then gives me an error message saying :

error: A required dependency 'cups (common unix printing system)' is still 1 missing.
error: installation can not continue without this dependency
error: please manually install this dependency and re-run this installer,

so what i'm looking for is how to download and install 'cups' and if it's possible to do it from my terminal. any help would be appreciated. thanx

---

### Post by spiderbatdad on 2008-02-26
cups should already be installed. Type localhost:631 into your address bar to set up your printer.

---

### Post by rockerphil on 2008-02-26
oh, sorry, i'm sure it'll help to tell you that i'm working in Fluxbuntu

---

### Post by rajj on 2008-02-27
Try this:
sudo apt-get install cupsys.
(Not sure about Fluxbuntu, but works in Ubuntu).

---

### Post by rockerphil on 2008-02-27
thanx rojj, worked perfectly, printer is up & running

---

