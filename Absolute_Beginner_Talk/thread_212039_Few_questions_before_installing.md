---
title: "Few questions before installing"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Bino on 2006-07-09
I´m about to install ubuntu on my systems since I´ve heared soo much good things about it. But I have a few questions before I do:

- Do I have to format my system and create an extra boot before installing ubuntu or can I run the install directly?
- If you can run it directly, does it make you able to dual boot or do I need to install something to able to doing that?
- Does Ubuntu already have features like a dvd playing program or do I need to install that afterwards?

That´s about it for now. 
Thanks in advance.

---

### Post by MrHorus on 2006-07-09
> **Bino said:**
> 
- Do I have to format my system and create an extra boot before installing ubuntu or can I run the install directly?

No, but you will need to resize the partitions and split them into your Windows partition (if thats what you have presently) and then your Linux ones, so make sure and run defrag first so you have a nice block of contiguous free space.

> - If you can run it directly, does it make you able to dual boot or do I need to install something to able to doing that?

You install a bootloader as part of the installation process and the bootloader will detect any other operatating systems that are currently installed.

> - Does Ubuntu already have features like a dvd playing program or do I need to install that afterwards?

No because the legal status of Content Scrambling System and decrypting commercial DVDs is somewhat dubious in some jurisdictions so no distributions ship with these packages by default.

Look for some howtos as to how you install this support but I assure you it's a fairly simple matter assuming it's legal in your juristiction :)

---

### Post by Bino on 2006-07-09
Thanks for your answers. 

So reading by your answers I first need to create a partition for Ubuntu before I can begin. Right?

---

### Post by daou on 2006-07-09
> So reading by your answers I first need to create a partition for Ubuntu before I can begin. Right?

The installation of Ubuntu has a partitioning program which will let you partition space for Ubuntu. If you are using the 6.06 desktop liveCD, it has GParted which is a graphical partitioning tool very similar to Partition Magic and is easy to use.

---

### Post by daou on 2006-07-09
[This page]("http://www.psychocats.net/ubuntu/installing.html") has pictures of the installation process and of GParted. It also has a link to a guide how to partition space for Ubuntu.
[Here is the direct link to that page.]("http://www.psychocats.net/ubuntu/partitioning.html")

---

### Post by daou on 2006-07-09
If you get stuck and don't know what to do during the installation, you can set up your internet connection during the installation and go look for help (or view the partition guide while partitioning). If you are using DHCP you won't even need to set up the internet, you will likely have access right away. If not, you can find the network configuration in the menu of the LiveCD: **System->Administration->Networking**

This is that part that blew my mind while installing Ubuntu for the first time. I never imagined it would be possible to get help for the installation of an OS while installing it. Another one of those Windows conditioned thought patterns.

---

