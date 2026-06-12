---
title: "Dependency, what is this?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by housam on 2006-12-02
G'day,
I was trying to install a package needed for the modem driver installation and the following message poped out.
> housam@housam-laptop:~$ cd ~/Desktop
housam@housam-laptop:~/Desktop$ sudo dpkg -i linux-headers*.deb
Password:
Selecting previously deselected package linux-headers-2.6.15-23-386.
(Reading database ... 69523 files and directories currently installed.)
Unpacking linux-headers-2.6.15-23-386 (from linux-headers-2.6.15-23-386_2.6.15-23.39_i386.deb) ...
dpkg: dependency problems prevent configuration of linux-headers-2.6.15-23-386:
 linux-headers-2.6.15-23-386 depends on linux-headers-2.6.15-23; however:
  Package linux-headers-2.6.15-23 is not installed.
dpkg: error processing linux-headers-2.6.15-23-386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.15-23-386
what was that means? and how to do the installation?
thanks

---

### Post by smile_sunshine on 2006-12-02
A dependency is where a package depends on having something else already installed on your system for it to work.

Not sure but I think in this case it means you need to install linux-headers-2.6.15-23 first ???

---

### Post by 5-HT on 2006-12-02
linux-headers-2.6.15-23-386 depends linux-headers-2.6.15-23.
In order to install linux-headers-2.6.15-23-386, linux-headers-2.6.15-23 will need to be installed as well.

If you've access to a computer with Internet access, or are multi-booting and have net access on a different OS, you can fetch linux-headers-2.6.15-23 from [packages.ubuntu.com]("http://packages.ubuntu.com") and install it with dpkg (asssuming here that your Ubuntu install does not yet have net access). Once done, he installation of linux-headers-2.6.15-23-386 should proceed smoothly.

Hope that helps.

---

### Post by lamego on 2006-12-02
The safer way to install those packages is with apt :
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by 5-HT on 2006-12-02
> **lamego said:**
> The safer way to install those packages is with apt :
```
sudo apt-get install linux-headers-$(uname -r)
```

Absolutely! Just mentioned packages.ubuntu.com and dpkg as the OP was trying to install a modem driver which I'm assuming is required to get online. If not, apt would be an easier choice.

---

### Post by housam on 2006-12-02
Thanks for the clarification/replys. I'll try to install the package linux-headers-2.6.15-23 first after downloading.then I'll do the other installation.

Edit: I have dual boot

---

### Post by Sef on 2006-12-02
[How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by housam on 2006-12-02
Thanks Sef it's a great link.
I've posted another thread " [help installing a driver]("http://ubuntuforums.org/showthread.php?t=311134&highlight=help+installing+a+driver") ".
can you have a look and give me your advice?

---

