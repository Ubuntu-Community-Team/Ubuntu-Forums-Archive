---
title: "Can I run dos box on Lubuntu on my iMac g3"
date: 2015-09-07
forum: Apple Hardware Users
---

### Post by thomas62 on 2015-09-07
Hi

This question may be better posted elsewhere, but I kind of like this little section of the internet.

I want to install dosbox to run old games, however, the only option on the DL page is for Ubuntu. Noob question, will that work with Lubuntu also? Should I just try? 

[http://www.dosbox.com/wiki/Ubuntu_Configuration](http://www.dosbox.com/wiki/Ubuntu_Configuration)

[http://www.dosbox.com/download.php?main=1](http://www.dosbox.com/download.php?main=1)

I think the answer is yes.

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by patlkli on 2015-09-07
Lubuntu is based on Ubuntu, so yes, you can use the instructions for Ubuntu on your system as well.

You can install DosBox from the package repository using:

```
sudo apt-get install dosbox
```

---

### Post by thomas62 on 2015-09-07
Ty - tried to collect package and it failed:

dpkg: unrecoverable fatal error, aborting:
fork failed: Cannot allocate memory
E: Sub Process /usr/bin/dpkg returned an error code (2)

---

### Post by patlkli on 2015-09-07
Your system is out of memory. You should try to close some applications to free up some memory.

You can find the processes with the highest memory usage with the command:
```
top -o %MEM -n 1
```

However, I cannot guarantee that DOSBox will even work properly on a system which doesn't even handle dpkg without running out of memory.

How much RAM do you have in your iMac G3?

---

### Post by thomas62 on 2015-09-08
Hi

Thanks for you reply.

I ran the command and located 129 total, 1 running the rest sleeping. Xorg was the highest user.

Being new to Lubuntu, your questions serve more questions for me. I have a few fundamental questions

I think that I have 384 mb Ram. I am looking to upgrade this.

Anyway I wanted to check how much ram I had so I installed lshw.

I run it and the terminal says
(lshw-gtk:3502): IBUS-WARNING **: The owner of /home/XXX// .config/ibus bus is not root!

Where XXX is my user-name. I am running as Sudo

(can I make the owner of that file root?

I made a user with SUDO permissions, still ran it as SUDO and got same result. LSHW gets stuck on PCI (sysfs) after I select refresh.

---

### Post by patlkli on 2015-09-08
To find out how much memory you have, you can just free:
```
free -m
```
This will show you the total memory and current usage statistics in MiB.

---

### Post by thomas62 on 2015-09-08
Ok, so I have 241 mb ram, ta.

It's odd, on boot, out of 241 total, 236 is being used.

I am thinking this machine is not really capable of running dosbox, as you've suggested. I may keep an eye out for a cheap g4 (and keep learning on this one).

I thought there was more than that.

PS I think the that the fact PCI (sysfs) is stopping my LSHW  program is related to my radeon parameters / KMS.

Q (If  may).

I have posted this here / will ask that it be closed.

[http://ubuntuforums.org/showthread.php?t=2292825&page=2](http://ubuntuforums.org/showthread.php?t=2292825&page=2)

I am trying to make yaboot parameters permanent as per this article

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F)

I have followed the steps many times, but I always need to use the parameters regardless.

This is not just isolated to the yaboot.conf file

If I edit /etc/modules as per this article

[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_get_a_working_battery_indicator.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_get_a_working_battery_indicator.3F)

To try and make my battery appear, or keyboard light up, it does not work.

---

