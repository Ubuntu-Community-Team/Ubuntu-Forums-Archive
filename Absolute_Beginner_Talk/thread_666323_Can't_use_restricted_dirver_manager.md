---
title: "Can't use restricted dirver manager"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-13
Hi, 

I reinstalled Ubuntu gusty gibbon and followed the instructions 'the Master Kernel Thread'.. [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

and compiled kernel. 

Before compling kernel, I got a message from the task bar about installilng restricted driver  for Nivida card and modem. After compiling kernel, I don't get it anymore. when I go to System --> Administration --> restricted drvier manager...  I get the following error mesage. 

You need to install the package linux-restricted-modules-2.6.23.12 for this program to work. 


Thus, I tried to install it by 

sudo aptitude install linux-restricted-modules-2.6.23.12  

but it doesn't install anything and I still get the same error message..

---

### Post by ThrobbingBrain66 on 2008-01-13
That version of the linux-restricted-modules doesn't exist in the Gutsy repos.  The latest version is 2.6.22-14

---

