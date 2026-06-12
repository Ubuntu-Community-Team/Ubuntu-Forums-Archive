---
title: "problem installing new apps from add/remove"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by thedragon4453 on 2007-04-30
The problem I have is that most of the apps say that they are ucompatible with the i386. This is a fresh install of feisty, but on the install before that i had no problem. 

For example, I want to install wine, but it wont allow me because it says that wine is incompatible with i386.

Im running a p4 3.2g. i read a little, and that isnt i386, is it?

---

### Post by bobplano on 2007-04-30
i386 is the OS structure for a single core machine. if anything it should be saying that is isn't compatible with amd64. it's not your system structure because i run wine on the i386 version of ubuntu

---

### Post by Nythain on 2007-04-30
try installing with apt-get and see what it says
sudo apt-get update
sudo apt-get install wine

---

### Post by thedragon4453 on 2007-04-30
it is returning the following error code:

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA

I get the same thing through the add/remove programs functions.

---

