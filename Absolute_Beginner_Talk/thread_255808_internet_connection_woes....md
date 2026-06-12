---
title: "internet connection woes..."
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by cjh on 2006-09-12
i have a small question.

after an exhausting time getting the modem driver working, whenever i connect using the network settings app it stops the connection when i click "ok" and it closes.
net connection will not connect using KPPP and my connection comes up as loopback interface (lo). under the networking tool the two devices presented are "loopback interface (lo)" and "ethernet". 
i did not have this problem with my first install of ubuntu 6.06 but i do now after i have re-installed the OS due to a mess I made when partitioning.

funnily now with my new install i can also access my windows filesystem straight from the desktop which i couldnt do at all in the first install of ubuntu.

I do not understand. could someone please shed some light on the connection difficulties?

i have a v92 conexant internal modem that does work under ubuntu. i am using it now, i just cannot close the" network settings" box or it will reset the modem configuration.

cjh

---

### Post by Najand on 2006-09-12
Do you know your chipset?
if not:
```
wget -c http://easylinux.info/uploads/scanModem.gz
gunzip -c scanModem.gz > scanModem
chmod +x scanModem
sudo cp scanModem /usr/bin/
sudo scanModem
cat Modem/ModemData.txt
```

---

### Post by cjh on 2006-09-12
chipset is hsfmodem. i have used the scanModem to check and download appropriate drivers for kernel.

---

### Post by cjh on 2006-09-12
i have to go out for awhile. i will be back in maybe an hour or so. i hope you can help think of something. if not it is ok. thankyou very much for your help i appreciate it greatly and i hope you are still here when i return

thankyou, cjh.

---

