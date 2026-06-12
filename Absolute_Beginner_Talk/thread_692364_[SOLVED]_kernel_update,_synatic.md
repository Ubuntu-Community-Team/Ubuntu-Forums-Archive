---
title: "[SOLVED] kernel update, synatic"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by (((X))) on 2008-02-09
Hello

First I turned on my laptop.
System update-icon flashed about new updates are availabe.
There were updates of all kinds, firefof, firefox-bin, kernel***, kernel-headers and so on, so I I just  updated my system, after rebooting my laptop gete errors about ALLOCATING RECOURCE REGION.
I installed updates, because updater indicated they were important, for security reasons..so I thought, ok
My question is now, is there a way to brig my old kernel back and is it SAFE to use?

---

### Post by dcstar on 2008-02-09
> **(((X))) said:**
> Hello

First I turned on my laptop.
System update-icon flashed about new updates are availabe.
There were updates of all kinds, firefof, firefox-bin, kernel***, kernel-headers and so on, so I I just  updated my system, after rebooting my laptop gete errors about ALLOCATING RECOURCE REGION.
I installed updates, because updater indicated they were important, for security reasons..so I thought, ok
My question is now, is there a way to brig my old kernel back and is it SAFE to use?

Do you know if the updates completed 100% successfully?

---

### Post by vamsibethapudy on 2008-02-09
hi 
i get this 'allocating resource region' errors everytime i login.
i didnot take notice if these messages started after an update.
any progress in this forum is highly appreciated

---

### Post by (((X))) on 2008-02-09
yes, I´m 100% sure

---

### Post by dcstar on 2008-02-09
Assuming your machine still boots up, the message may not be important:

[http://ubuntuforums.org/showthread.php?t=692166](http://ubuntuforums.org/showthread.php?t=692166)

---

### Post by (((X))) on 2008-02-09
This slows down ubuntu boot process.
And looks ugly, About 32 pts big:(

---

### Post by (((X))) on 2008-02-09
so, they not going to fix this?
Then, I have another question, How to go back to privious kernel?

---

### Post by spiderbatdad on 2008-02-09
check /boot/grub/menu.lst to see if the previous kernel is still there...uncomment it and comment out the upgrade. unfortunately, if it was in position 0, it may have been overwritten. There may be yet another kernel upgrade to fix the error. make sure your sources are all enabled and run```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by (((X))) on 2008-02-10
Today I booted without errors.:lolflag:
:)great
Probably I had to shutdown after upgrade, not reboot..

---

