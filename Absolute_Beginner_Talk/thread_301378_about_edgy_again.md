---
title: "about edgy again"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by jonathan21 on 2006-11-17
if i were to run the command sudo aptitude dist-upgrade and i get disconnected from internet while downloading some of the packages will it effect my current installation.by that i mean will i be able to boot into ubuntu have backed up already but just wanted to ask as a precaution

---

### Post by anguste on 2006-11-17
No, I think.

Basically the principle is DOWNLOAD -> INSTALL/REPLACE. So during download phase actually nothing is changed.

---

### Post by adam.tropics on 2006-11-17
Correct. The packages are downloaded to /var/cache/apt/archives before they are installed. Once you are disconnected, the downloads remaining will fail, and you will be asked if you want to install those that did download. Don't bother, and next time you're online again, start over. The packages you succesfully downloaded will still be stored locally, so will not have to download those again.

---

### Post by jonathan21 on 2006-11-17
thank you

---

### Post by junglepeanut on 2006-11-17
I have actually had my Internet disconnected for more than 3 minutes during this procedure, after the Internet came back on it just resumed where it left off with out me doing anything.

---

### Post by adam.tropics on 2006-11-17
Well that is odd, and must be related to an Ubuntu specific setting, because so far as I am aware, the default timeout is 2 minutes (120 seconds).

---

