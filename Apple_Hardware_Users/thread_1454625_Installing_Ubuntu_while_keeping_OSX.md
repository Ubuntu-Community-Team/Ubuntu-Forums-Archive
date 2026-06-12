---
title: "Installing Ubuntu while keeping OSX"
date: 2010-04-14
forum: Apple Hardware Users
---

### Post by History500 on 2010-04-14
Is it possible to install Ubuntu without uninstalling mac os X? Can I just shrink the OSX partition while I install Ubuntu? I don't have the OSX DVD, so I can't just reinstall OSX. I am running an iBook G4.

---

### Post by linuxopjemac on 2010-04-15
I think that's possible.
[http://mac.linux.be/content/successful-osx-partition-shrink-g4-mini](http://mac.linux.be/content/successful-osx-partition-shrink-g4-mini)

---

### Post by gcndavidmn on 2010-04-15
Use Boot Camp Assistant to make a new partition.
When you install Ubuntu use the new partition. (You get awarded no marks for erasing your OSX partition).

---

### Post by srs5694 on 2010-04-15
> **gcndavidmn said:**
> Use Boot Camp Assistant to make a new partition.

History500 specified using a PowerPC-based Mac. AFAIK, Boot Camp is used only on Intel-based Macs.

---

### Post by gcndavidmn on 2010-04-15
I completely forgot that! It's what you get when your first mac was intel :/

---

### Post by History500 on 2010-04-15
Would it work to install ubuntu onto a flash drive, then plug in that flash drive and boot off of it whenever I want to use linux?

---

### Post by gunnarlinux on 2010-04-15
> **History500 said:**
> Would it work to install ubuntu onto a flash drive, then plug in that flash drive and boot off of it whenever I want to use linux?

OSX Can't boot from flash drives, your going to have to use a cd/dvd you burned.

---

### Post by linuxopjemac on 2010-04-16
That's not true. I booted Ubuntu alternate installer from USB. To have it boot a live environment is more tricky, it's complicated due to the fact that you have to poke around with xorg.conf to have a working X. It's all possible, but you have to be good in Linux.

---

### Post by galenorama on 2010-04-16
> **gcndavidmn said:**
> Use Boot Camp Assistant to make a new partition.
When you install Ubuntu use the new partition. (You get awarded no marks for erasing your OSX partition).


I have an intel Macbook, and that is what I thought I should do, except when I booted off my live CD, and opened the installer, I selected the partition I already created in OSX, and Ubuntu gave a Root File System Unavailable, please fix this and try again" error. Any thoughts?

---

### Post by gcndavidmn on 2010-04-16
In the live CD you could try deleting the partition made by boot camp (NOT YOUR OS, I know I say it a lot, but you will look foolish if you do) and making a new on in the free space.

---

### Post by galenorama on 2010-04-16
I'll try that.

---

