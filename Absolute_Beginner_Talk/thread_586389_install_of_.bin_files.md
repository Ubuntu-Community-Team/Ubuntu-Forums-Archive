---
title: "install of .bin files?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by dorogavtsev on 2007-10-22
> "RealPlayer10GOLD.bin" cannot be opened

No application suitable for automatic installation is available for handling this kind of file.

what should i do?

---

### Post by hyper_ch on 2007-10-22
(1) Open synaptic

(2) Activate the Canoncial Repository

(3) Update the packages

(4) Search for real player and install it

---

### Post by dorogavtsev on 2007-10-22
> **hyper_ch said:**
> (1) Open synaptic

(2) Activate the Canoncial Repository

(3) Update the packages

(4) Search for real player and install it

How to activate the Canoncial Repository? :-)

---

### Post by realvz on 2007-10-22
> **dorogavtsev said:**
> what should i do?

chmod 775 RealPlayer10GOLD.bin

then
sudo sh ./RealPlayer10GOLD.bin

---

### Post by mirons on 2007-10-22
> **dorogavtsev said:**
> How to activate the Canoncial Repository? :-)

You should use the "add/remove programs" application and there find a button called "modify repositories", or something like that. (I have it in my kmenu under kubuntu, button and apps name are translated from my native lang, so I say look for something similar)

---

### Post by realvz on 2007-10-22
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by hyper_ch on 2007-10-22
In synaptic, you have somewhere the option of managing the repositories (don't have a linux box here :( so I can't say exactely). In there you have the official ones and then there's also a tab for 3rd partie. The canonical is listed there.

The help link above is outdated for gutsy. The canoncial one is already listed somewhere inside synaptic, but not activated.

---

