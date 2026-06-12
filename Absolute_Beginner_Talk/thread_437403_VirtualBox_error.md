---
title: "VirtualBox error"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by NAT1V3 on 2007-05-08
I just installed VirtualBox and I'm trying ot set up my XP virtual machine but every time I start the VM I get [this error]("http://img252.imageshack.us/img252/6465/img1ea8.png") any help would be appreciated, Brad

---

### Post by H.E. Pennypacker on 2007-05-08
[http://www.virtualbox.org/wiki/User_FAQ](http://www.virtualbox.org/wiki/User_FAQ).  Scroll down to the Linux hosts part.

---

### Post by MRiGnS on 2007-05-08
```
sudo apt-get install build-essential linux-source
sudo su
/etc/init.d/vboxdrv setup
exit
sudo chmod 666 /dev/vboxdrv
sudo usermod -G vboxusers -a <your userid>
sudo /etc/init.d/gdm restart (or kdm restart if using kde)
```

if it says it can't find your kernel sources try

```
sudo apt-get install linux-headers-`uname -r`
sudo su
/etc/init.d/vboxdrv setup KERN_DIR=/usr/src/linux-headers-`uname -r`
chmod 666 /dev/vboxdr
usermod -G vboxusers -a <your userid>
exit
sudo /etc/init.d/gdm restart (or kdm restart if using kde)
```

---

### Post by NAT1V3 on 2007-05-08
ok I read thet what exactly should i put in the terminal i tried "sudo usermod -G vboxusers -a <brad>" and iget this error "syntax error near unexpected token `newline'" Thanks, Brad

---

### Post by NAT1V3 on 2007-05-08
nm thanks post above me

---

### Post by MRiGnS on 2007-05-08
without the <> just brad in your case. the <bla> just represents a place holder :D

---

