---
title: "Error when attempting to install updates"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by Elotero on 2007-11-29
I get this error whenever i try and add/remove programs. It is also keeping me from installing the latest updates.  Please can anyone help me out? 

E:Tzdata:subprocess post installation script returned error exit status 1

---

### Post by ItsMitsHere on 2007-11-30
you may try **sudo apt-get --fix-missing** first, then **sudo apt-get update** and finally update manager (graphical) to update!

let me know if you still have problems!!!

i think you should also take a look at [http://ubuntuforums.org/showthread.php?t=588272]("http://ubuntuforums.org/showthread.php?t=588272")

---

### Post by Elotero on 2007-11-30
Awww thanks so much... i will try as soon as i get home and let you know if its fixed.  This has been a major thorn in my side for a little bit over a week now...

---

### Post by Elotero on 2007-12-01
sorry man... the command looked like it would work, but as soon as i tried to install the updates i got the same error message...

---

### Post by Elotero on 2007-12-03
NVM.. I had to switch the timezone in KDE and GNOME to BErlin time.. it works now..

---

