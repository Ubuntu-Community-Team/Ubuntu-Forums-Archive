---
title: "Another process is using the packaging system database"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by joel_quiles on 2007-04-11
Hi.
I have a strange problem. I'm new to Linux (go figure hehe). During the apt packet system update I turned off the computer. Now everytime I try to run it (or add/remove programs, or any program related to it) the following message appears:

>>"You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one."

I researched some in the internet and many answers explained that I must run the Ksysguard and kill the processes related to apt and adept. I already did that... well, I think. I don't know the process name so i searched it on ksysguard and some processes appeared. I killed them all. After that I re-entered the Adept Manager and the same message reappeared. I went again to the ksysguard but now I cant find  te processes with search and I dont know the names.

I also tried deleting a lock file under /var/lib/apt/lock  or something lie that but again the same message appeared.

Is there any other solution to  my problem? Or I am doing something wrong? well I hope someone answers me because I'm getting exhausted and thinking of leaving Linux for a while. Nvm that, help! thanks in advance for any reply...

---

### Post by caffienefree on 2007-04-11
This bug report might be helpful.

[https://answers.launchpad.net/ubuntu/+ticket/3481](https://answers.launchpad.net/ubuntu/+ticket/3481)

---

### Post by zambilo76 on 2008-07-05
> **caffienefree said:**
> This bug report might be helpful.

[https://answers.launchpad.net/ubuntu/+ticket/3481](https://answers.launchpad.net/ubuntu/+ticket/3481)

I've got the exact same problem, my battery died while I was installing the restricted extras to get java ... and now I can't get Adept installer to unlock .. When you try to unlock it it crashes .. 
-----------------------------------------------------------------------------------------------------------------
The solution should be:
run : sudo apt-get check ....it should prompt you run : sudo dpkg --configure -a
whether it does or not run it and it should solve you problem

---

