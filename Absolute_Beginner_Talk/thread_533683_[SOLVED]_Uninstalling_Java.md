---
title: "[SOLVED] Uninstalling Java"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Gorlinux on 2007-08-24
--------------------------------------------------------------------------------

Hello,

I tried to install Java but I encountered some problems and now when I run Synaptic it gives me this error:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I think I know what happened and it's all my fault . I did not read the instructions provided by Kilz.

> **Kilz said:**
> This howto/script is a way to run the 32bit firefox on the amd64 version of Ubuntu. That way all plugins will work. The script works on Dapper, Edgy, and there is a Feisty script. 
It is recommended that you use the script to install vs the howto. The script will be the most up to date. The howto is left in place so those with installs can trouble shoot if minor problems arise.

Well enough chatter, on to the howto :D 

First, I tried installing Java, I accidentally used an older script below - my bad  

cd ~/Desktop
sudo bash
chmod 777 ./jre-1_5_0_07-linux-i586.bin
./jre-1_5_0_07-linux-i586.bin

The download went okay though until it got to I guess the EULA message and it sort of hung there. But then I realized then that there is now an updated version of JRE when I checked Java website. So I downloaded the 6u-i586 from Java.com and then run the script in the terminal:
cd ~/Desktop
sudo bash
chmod 777 ./jre-6u2-linux-i586.bin
./jre-6u2-linux-i586.bin

Again, the installation when okay until an error message came up that one of the packages could not be opened (sorry, was not able to take note which package it was)

I would really want to make Java work in Firefox and hopefully the right way next time. But I have to uninstall or remove everything I did wrong. Please help. Is there hope for me? Thanks.

Remoresfully,
Golinux

P.S. Kilz if you're reading this your script is brilliant! I am the one who's not :(

---

### Post by Ink-Jet on 2007-08-24
Run
```
dpkg --configure -a
```
And then make sure Java is un-installed, and then install it again.
You should probably do it through the repos, too.

---

### Post by Gorlinux on 2007-08-24
I tried this:

gorlinux@gorlinux:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

but it requires superuser privilege. How do I  become a superuser?
Thanks.

---

### Post by Gorlinux on 2007-08-24
I was able to resolve problem by adding:
sudo dpkg --configure -a

Thanks.

---

