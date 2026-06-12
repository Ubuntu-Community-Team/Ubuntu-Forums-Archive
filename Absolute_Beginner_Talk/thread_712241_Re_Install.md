---
title: "Re Install"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Mr_Bond_UK on 2008-03-01
Evening All

How hard is it to re install without losing all of my files, ie doc and music etc, just finding that ubuntu keeps crashing, so would like to start a fresh, currnetly running gutsy. Downloaded and burnt the iso so is it as simple as plug and play?

---

### Post by scragar on 2008-03-01
the liveCD should let you try before you decide to install it, only if you want to do you have to run the installer, and nothing is done until the final step where you are asked to confirm a white screen with a lot of text(confirming everything from language to partition setup and such), so feel free to check it out before you decide what you want.

---

### Post by Mr_Bond_UK on 2008-03-01
Im already running Gutsy, so know what to expect, i just need a step by step guide to a reinstall of the OS whilst still keeping my Home folder untouched!

---

### Post by RealPSL on 2008-03-01
Is your /home directory on a separate file system? You can tell pretty easily from the command line by doing a df /home if the output looks like this 

/dev/sda9              3842376    757696   2889492  21% /home

it means /home is on disk partition /dev/sda9 and you can reinstall simply choosing not to format that partition.

If the output looks like this 
/dev/sda3              3842376    757696   2889492  21% /

I would recommend you take a backup of /home prior to reinstall. In fact you should take a backup even in the first scenario as we all make mistakes.

Can you describe a little more the crashes you are experiencing?

---

### Post by Mr_Bond_UK on 2008-03-01
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             37958500  14116824  21913476  40% /

Crashes happen, ALOT. Completly frezes on me, and nothing will bring it out of it but a hard re-boot. Not sure what it is but is very annoying, especially when doing remote upgrades through putty.

---

### Post by Mr_Bond_UK on 2008-03-02
any ideas?

---

### Post by RealPSL on 2008-03-03
Regarding the crashes I would recommend running a memory test. You could just have a bad memory module that is resulting in the crashes and freezes you described.You can run the memtest from the liveCD. I would recommend you do this first to rule it out as the source of the crashes.

Regarding your potential update. I believe your /home directory would be overwritten during an upgrade because it is on the root "/" file system. I would recommend that you copy all the data their to a backup drive.

---

