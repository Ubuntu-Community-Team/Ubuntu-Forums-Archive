---
title: "[SOLVED] Can't find installed programs"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by OldNewb on 2008-02-14
I've used synaptic package manager to install aircrack-ng but I can't find it.  when I check synaptic it says it is installed but I can't find it in the menus.

How do I find it and how do I run it?

---

### Post by ComputerHermit on 2008-02-14
I dont know if your kidding but I thought it would be funny if I told you
```

sudo aircrack -g

```

I'm pritty sure that is how you do it I havent played with aircrack in along time but you can google aircrack and they also have a forum

---

### Post by PeterJS on 2008-02-14
Horay for Aircrack, brought my roommate and I many hours of fun completely pointless weekend competition. If you right click on the package in synaptic, one of the options under properties is installed files, which gives a listing of all the installed files (go figure). The program itself is probably in one of the bin folders. Once you've gotten the name from there, open up a terminal, type in and off you go.

---

### Post by OldNewb on 2008-02-14
> **ComputerHermit said:**
> I dont know if your kidding but I thought it would be funny if I told you
```

sudo aircrack -g

```

I'm pritty sure that is how you do it I havent played with aircrack in along time but you can google aircrack and they also have a forum

terminal just says:

computername:~$ sudo aircrack -g
sudo: aircrack: command not found

---

### Post by OldNewb on 2008-02-15
I tried downloading aircrack from their site and I made it a little farther but now I am here

make works but make install gives me this output

~/aircrack-ng-0.9.2$ make install
install -d /usr/local/bin
install -m 755 aircrack-ng airdecap-ng packetforge-ng ivstools kstats /usr/local/bin
install: cannot create regular file `/usr/local/bin/aircrack-ng': Permission denied
install: cannot create regular file `/usr/local/bin/airdecap-ng': Permission denied
install: cannot create regular file `/usr/local/bin/packetforge-ng': Permission denied
install: cannot create regular file `/usr/local/bin/ivstools': Permission denied
install: cannot create regular file `/usr/local/bin/kstats': Permission denied
make: *** [install_userland] Error 1

Any help would be appreciated.

---

### Post by oldos2er on 2008-02-15
Run "sudo make install" instead of just make install.

---

### Post by OldNewb on 2008-02-15
Thanks oldos2er that fixed it for me!

---

