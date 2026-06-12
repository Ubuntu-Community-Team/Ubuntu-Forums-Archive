---
title: "Apt-get"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by linuxforrealpeople on 2007-06-25
Does apt-get install the latest stable release by default?

What happens when a new release comes out?

It is just that I am terrified of compiling binaries manually...........


Thanks.

---

### Post by mlentink on 2007-06-25
apt handles packages only, it does not take care of source. 
Whether you get the latest stables releases depends a bit on which repositories you use. If you stay with the ubuntu ones and don't use backports etc., you get stable stuff only.
So no need to worry, I guess...

---

### Post by kevdog on 2007-06-25
Usually when a new release comes out, I am notified by an icon in the system try that updates are available.  I cant remember the actual program that does this -- I think its called update notifier or something.  Anyway I run a shell script that checks for updates everytime I boot.  You could add a cron job if you wanted to run a shell script that would check and install updates in you wanted to check more frequently.

---

### Post by mlentink on 2007-06-25
```
sudo apt-get update
sudo apt-get upgrade
```
will do that for you. Nevertheless. that will get you the latest versions placed in the repo's you have in your sources.list, not necessarily the bleeding edge.

---

