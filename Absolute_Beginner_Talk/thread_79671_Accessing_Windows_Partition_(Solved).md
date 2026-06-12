---
title: "Accessing Windows Partition (Solved)"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by weneedjuice on 2005-10-20
hi
I had installed Ubuntu after I began getting a message saying something along the lines of a file being missing called "system" and that I needed to insert the Windows XP install disk and press "r" to repair it. So, when I installed Ubuntu, I partitioned 74gb of material I had downloaded when I used WIndows XP. I'm not sure what I did, but now when I try to access that partition (called "hda2"), it says I don't have permission to access it. It says that "root" does, but when I try to log in as "root", every password i would have possibly used doesn't work. I don't think I was even asked for a password for root. I even tried not entering a password at all. I just can't get in. I've also tried booting up in Windows XP, but it does the exact thing as it did before (the error message). 
I guess what I'm asking is, is there anything I can do, or do I have to completely erase that partition and start over again? Have I overlooked anything?
Please know that I'm very new to linux and the whole command process, so I'm sorry if I'm asking a really stupid/obvious question here.

---

### Post by Emerzen on 2005-10-20
To set a root password, follow the instructions listed here:

[www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by Ampersand on 2005-10-20
To perform an action as root, you need to use the sudo command. To do this, simply type 'sudo' before the command, then put in your usual password.

For example, if you open a terminal (from the Accessories menu) and run
```
sudo nautilus
```
then enter the password you used to log in, a file manager running as root will open, and you should be able to access your windows partition with it.

---

### Post by weneedjuice on 2005-10-20
when i try to enter the password, it won't let me type anything. the only thing it responds to is pressing the enter key, and when i do that, it says "Sorry, try again."

---

### Post by weneedjuice on 2005-10-20
[QUOTE=weneedjuice]when i try to enter the password, it won't let me type anything. the only thing it responds to is pressing the enter key, and when i do that, it says "Sorry, try again."[/QUOTE]


nevermind, I think I have it. Thanks!

---

### Post by angelstar123 on 2006-10-19
thanks, this is the same problem that I was having as far as accessing windows partition. this worked out perfectly.

---

