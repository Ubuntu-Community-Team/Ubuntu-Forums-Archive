---
title: "Marvell Yukon Ethernet Card on iMac"
date: 2007-09-15
forum: Apple Intel Users
---

### Post by Gestalt_splash on 2007-09-15
I am a novice in linux and I have never used Mac. I just bought an iMac with Intel Core 2 Duo and managed to triple boot OS X, Windows XP, and Ubuntu Linux (Dapper Drake) after some struggle. Unfortunately, the ethernet card was not recognized by Ubuntu linux during installation. I tried in vain to solve the problem by configuring the kernel. Please advise how I may locate the required module and install it. Many thanks.

---

### Post by cyberdork33 on 2007-09-15
> **Gestalt_splash said:**
> I am a novice in linux and I have never used Mac. I just bought an iMac with Intel Core 2 Duo and managed to triple boot OS X, Windows XP, and Ubuntu Linux (Dapper Drake) after some struggle. Unfortunately, the ethernet card was not recognized by Ubuntu linux during installation. I tried in vain to solve the problem by configuring the kernel. Please advise how I may locate the required module and install it. Many thanks.

The sky2 driver is the one you need. I do not know if it was included in the Dapper Drake kernels... You should upgrade to Feisty though or gutsy when it comes out next month.

---

### Post by Gestalt_splash on 2007-09-15
Hi cyberdork33,

Thanks for your advice. Could you please advise me how to install sky2? In fact, I tried sk98lin and installed it by dpkg in vain. I read that sky2 may not be so reliable as sk98lin. What is your comment?

---

### Post by cyberdork33 on 2007-09-16
> **Gestalt_splash said:**
> Hi cyberdork33,

Thanks for your advice. Could you please advise me how to install sky2? In fact, I tried sk98lin and installed it by dpkg in vain. I read that sky2 may not be so reliable as sk98lin. What is your comment?
sky2 is fine in newer kernels (2.6.20?) It is still marked as experimental, but is used by default in Ubuntu on feisty and gutsy. I have not had an issues with the ethernet at all on my iMac (not using gigabit though).

---

### Post by Gestalt_splash on 2007-09-17
I tried Edgy and Feisty Live CDs on my iMac to see if the Gigabyte Marvell Yukon ethernet card might be recognized. My screen just showed me colors without pattern on Edgy, and left me in the console in a deadlock on Feisty. The best Ubuntu Linux version that may be used in my case is Dapper Drake. 

I have an idea, which may work but I may not have time to try it out now. Perhaps, the ethernet card problem may be solved by making a virtual machine out of the linux partition with Parallels or Fusion.

---

### Post by cyberdork33 on 2007-09-17
> **Gestalt_splash said:**
> I tried Edgy and Feisty Live CDs on my iMac to see if the Gigabyte Marvell Yukon ethernet card might be recognized. My screen just showed me colors without pattern on Edgy, and left me in the console in a deadlock on Feisty. The best Ubuntu Linux version that may be used in my case is Dapper Drake.
Edgy is too old, as is dapper for proper  Intel Mac support. Install Feisty with the Alt Install CD and you will be OK. 

> I have an idea, which may work but I may not have time to try it out now. Perhaps, the ethernet card problem may be solved by making a virtual machine out of the linux partition with Parallels or Fusion. That would work fine as a VM uses Virtual hardware... The system never sees your real ethernet card.

---

### Post by Gestalt_splash on 2007-09-18
Thanks for your advice. I was actually trying Feisty Live CD to see if it would be okay to install Feisty. Why did Feisty Live CD hang at the Console?

---

### Post by cyberdork33 on 2007-09-18
> **Gestalt_splash said:**
> Thanks for your advice. I was actually trying Feisty Live CD to see if it would be okay to install Feisty. Why did Feisty Live CD hang at the Console?
There are some odd issues with the ATI video hardware and the opensource ati driver.

---

### Post by Gestalt_splash on 2007-09-19
Does this mean I will encounter the same problem with ATI after installing Feisty by your approach?

---

### Post by cyberdork33 on 2007-09-19
> **Gestalt_splash said:**
> Does this mean I will encounter the same problem with ATI after installing Feisty by your approach?
yes/no... update everything and install the fglrx driver (which you will want anyway) and your display will look wonderful. you can probably get x to work on the live cd by doing the same sort of thing. 

Use ALT+CTRL+F1 to get to a terminal. (If that works for you).
     Code:
     ```
sudo apt-get install linux-restricted-modules-generic
```Then edit your xorg.conf to use the fglrx driver, and x should then be able to start, which can be done by entering the command:
```
sudo /etc/init.d/gdm restart
```I find that you sometimes have to do the above command more than once to get everything to restart properly.

---

