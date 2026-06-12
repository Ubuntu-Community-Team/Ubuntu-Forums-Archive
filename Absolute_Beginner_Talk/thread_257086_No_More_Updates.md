---
title: "No More Updates ?"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-09-14
Yeah,everything's running just hunky-dory,but...........
I haven'nt got any update for close to a week, just seems kinda strange to me,since they usually come about every other day ??


Got this: 
drakkor@drakkor:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gftp gftp-text
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
drakkor@drakkor:~$
Which would be the gFTP,and gftp text ???  :confused:

---

### Post by halcyon on 2006-09-14
You should try running Synaptic (under the Administration menu), hit the Reload button in the top left corner to update your repository lists, and then hit the Mark All Upgrades button beside it and then Apply to see if that fixes it.

---

### Post by Najand on 2006-09-14
You have to do both update and upgrade:
```

sudo apt-get update && sudo apt-get upgrade

```
Anyway they haven't been a lot of upgrades for Dapper recently.
I am looking forward for kernel 2.6.17.* too, but haven't been ready yet, it seems.

---

### Post by Najand on 2006-09-14
Anyway, gFTP is a free multithreaded ftp client for *NIX based machines running X11R6 or later. I think according to your setting, you have kept gftp  on a particular version. It just prevent it to upgrade gftp as you do the upgrade process.

---

### Post by Drakkor on 2006-09-14
Thanks, halcyon that seems to have done the trick ! I'm still learning,lol
got 2 months into Ubuntu and Linux,but ya gotta love it !! :) 

drakkor@drakkor:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
drakkor@drakkor:~$

---

### Post by halcyon on 2006-09-14
Haha, you're welcome, I'm new to this too, despite what my joined date says :P  I tried it back then and gave up on it.

---

### Post by Drakkor on 2006-09-14
Thanks also, Najand, most of Linux is so new to me,but I love it way more than anything that I grew up in e.g Windoze,lol :p
**[COLOR="Red"]UBUNTU ROCKS !![/COLOR]** ,LOL first time I used colors,lol
:)

---

### Post by Najand on 2006-09-14
The interesting thing about linux is that there is always something you don't know about it and you can have and amazing interesting adventure to learn about it. So it is always seems new to me when trying to do something new...

---

### Post by Drakkor on 2006-09-14
Yep, just used gFTP yesterday, and it works great, just as good as Bulletproof FTP in Wndows !! 
Moobuntu.......Linux for Cows,lol :p 
Sorry I stole that,lol !

---

