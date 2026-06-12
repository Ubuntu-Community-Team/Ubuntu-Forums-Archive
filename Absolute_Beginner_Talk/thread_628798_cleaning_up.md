---
title: "cleaning up"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by raytheyounger on 2007-12-01
do i need to defrag and the others like i did when i had windows?
thanks,
raymond

---

### Post by overdrank on 2007-12-01
> **raytheyounger said:**
> do i need to defrag and the others like i did when i had windows?
thanks,
raymond

Hi and welcome, no there is no defrag but you may want to clean up with these commands.
```
sudo apt-get autoclean
sudo apt-get autoremove
``` these command are run in the terminal located under applications, accessories. This may help in the future

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by njparton on 2007-12-01
Nope, unix/linux filesystems don't need defragging. Read the wikipedia entries for ext3, reiserfs or xfs.

---

### Post by raytheyounger on 2007-12-01
solved, it worked thanks much..
raymond

---

### Post by XVII on 2007-12-01
Fragmenting will only occur lightly with years of hard and constant use with no upgrades or updates.

---

### Post by overdrank on 2007-12-01
> **raytheyounger said:**
> solved, it worked thanks much..
raymond

HI and you can mark the thread as solved under the thread tools. :)

---

### Post by Niniel on 2007-12-01
Hi, and you don't really need to defrag NTFS either, at least that's my experience. I have not seen any improvement from defragmenting. Didn't do it for over a year, then did it for some reason, and when it was done everything was as fast/slow as it was before. 
Total waste of time.

---

### Post by TxSoldier on 2007-12-02
Sorry maybe a dumb question...............what do those clean up commands do that you posted?   Thank you!

---

### Post by overdrank on 2007-12-02
> **TxSoldier said:**
> Sorry maybe a dumb question...............what do those clean up commands do that you posted?   Thank you!

sudo apt-get autoclean
To clean out .deb archives from packages which are no longer installed on the system, execute the command from konsole

sudo apt-get autoremove
To remove a installed package, for example Synaptic, and all dependencies, execute the command from konsole

---

### Post by TxSoldier on 2007-12-02
Awesome, thank you for the info!!

---

