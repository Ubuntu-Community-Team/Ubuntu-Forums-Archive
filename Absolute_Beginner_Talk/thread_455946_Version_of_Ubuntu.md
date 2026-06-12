---
title: "Version of Ubuntu"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by padrino210 on 2007-05-27
Dear All, 

I would like to update to ubuntu version 7.04. 

Could someone please insturct me how to do it? 

Looking forward to a fast reaction? 

Regards, 

Il Padrino

---

### Post by Jimmyfj on 2007-05-27
Hi 

To upgrade your Ubuntu online you need to do this:

Open a terminal and make sure you are root by the sudo su command

sudo su

Then you type these in order:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

This will make your upgrade of Ubuntu run from the Internet, but before you do that be sure that you have some hours to burn on this. It will, depending on your connection speed take a while to complete.

The easiest thing will be to download the latest iso-file and burn it onto a cd, then make a fresh install instead of just an upgrade. The longest upgrade I have ever tried was when updating my daughters old computer. It ran for 6½ hours before completing.

---

### Post by TheWizzard on 2007-05-27
careful
dist-upgrade can break your system, especially when you customised your system a lot. 
i'd always do a fresh install!

---

