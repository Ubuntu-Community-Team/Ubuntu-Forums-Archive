---
title: "disable login?"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by hessiess on 2007-05-06
im the sole user of this computer, so i don't see any point in having 1 user account, and passwords on everything. is it posable to disable these features? its my computer so i don't see why ubuntu puts restrictions on where i can create a file.
i need a os that boots quickly and logs it self on. windows was taking 15 min to stabilise, witch is far to long. and regularly refused to shut down.

---

### Post by aysiu on 2007-05-06
If you're using Ubuntu, go to System > Administration > Login Window > Security > Enable Automatic Login

Let us know if you're using Kubuntu or Xubuntu instead.

---

### Post by oilchangeguy on 2007-05-06
go to system, admin, login window. from there you'll be able to disable the login password.

---

### Post by matoxxx on 2007-05-06
go system -  administration - login screen ,there is section where you define automatic login

---

### Post by hessiess on 2007-05-06
thx;) its all confusing wen you try an new program, if only windows had a comunaty like this.

---

### Post by chili555 on 2007-05-06
> i don't see any point in having 1 user account, and passwords on everythingThe point is security. If your computer is stolen, the thief will have access to your personal information, passwords, etc. through cookies. Once they log into your Amazon page, they will probably be able to order a "gift" for themselves, just before they pawn the computer.

If you never shop on-line, never do investments, on-line banking or pr0n, and you have an angry bull mastiff on duty, go right ahead.

In my opinion, 85% of Windows security issues could be solved, immediately if only Administrator could install software and Administrator log-in was disallowed by default. Imagine surfing the dark edge of the internet, a worm or virus wants to install itself and a window pops up and says, 'in order to install Worm.99.exe, the Administrator password is needed.' Would you give it?

---

### Post by aysiu on 2007-05-06
> **chili555 said:**
> The point is security. If your computer is stolen, the thief will have access to your personal information, passwords, etc. through cookies. Once they log into your Amazon page, they will probably be able to order a "gift" for themselves, just before they pawn the computer. I'm sorry, but this isn't true. If your computer is stolen, it is owned already. If someone has physical access to your computer, she has root access. She can reset your BIOS password (if you have one), boot a live CD (like Knoppix), open a root browser, and have access to all your files and settings (and cookies).

There are basically two kinds of security these passwords help:
1. Internal security (like a child-safe cap on a bottle of medicine or a safety latch on a paper-cutter)
2. External security (so that anything you execute as user won't corrupt your entire filesystem)

Physical security is a separate category and a password won't help you there. Encrypting your files might be a good barrier, though.

---

### Post by Scheater5 on 2007-05-06
I concur with aysiu.  Telling the GDM to automatically log you in is one thing.  A security risk, but a minimal security risk if your computer is never out of your possession.  However, enabling root privileges constantly is a bad idea, and a large part of the reason so many Windows computers' hardrives are filled to the breaking point with malware.  It's just a bad idea to log in a root.

---

### Post by azurehi on 2007-05-09
> **aysiu said:**
> If you're using Ubuntu, go to System > Administration > Login Window > Security > Enable Automatic Login

Let us know if you're using Kubuntu or Xubuntu instead.

I use both ubuntu and kubuntu, both feisty:  ubuntu on one HDD, kubuntu on the 2nd HDD.  I have enabled automatic login in ubuntu but have been unable to do so in kubuntu - help appreciated.  I'm finding that I am partial to Gnome/ubuntu, finding it easier to use and more understandable (for a linux newbie) but also like some the the KDE features.

---

### Post by aysiu on 2007-05-09
Well, you can really have only one display manager (KDM or GDM) running at a time. So even if you're using KDE, you'll still be using GDM and the autologin should apply. Maybe you could make it a timed login so you have time to switch desktop environments before the autologin happens?

---

### Post by hessiess on 2007-05-10
im not old enugh to buy stuf online anyway. i still think the safist solotion is to have a rubish pc for web serfing ;)

---

### Post by venzie on 2007-12-27
Same question, only, I'm using Xubuntu. :)

---

