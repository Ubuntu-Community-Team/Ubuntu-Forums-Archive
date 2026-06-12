---
title: "Broadcom Corporation BCM4331-MacbookPro 10,2- Connection gets lost over time"
date: 2018-02-26
forum: Apple Hardware Users
---

### Post by odydoum on 2018-02-26
I have recently attempted to install a dual boot ubuntu on my macbook pro, with the only thing unresolved being the wireless connection. I am currently using the bcmwl-kernel-source driver, since this appears to be the most stable by now but i have also tried the b43-firmware-installer one. The issue is that after some minutes the connection seems to be lost even though the applet shows that i am still connected. I even tried to ping my router and again, after some time packages appear to get lost or ping reports over 1000 ms. Some times reconnecting may solve the issue temporarly. After trying many possible fixes i decided to give it a go writing to the forums.

[ATTACH]278673[/ATTACH]

---

### Post by wildmanne39 on 2018-02-26
*Thread moved to **Apple Hardware Users, a more appropriate forum**.*

---

### Post by wildmanne39 on 2018-02-26
> I am currently using the bcmwl-kernel-source driver, since this appears to be the most stable
Is this determined by actual performance on your computer? because the other driver is what is called for I suggest you purge the one you are using now and install the other one. There are also error messages concerning this driver in dmesg.

Please do:
```
sudo apt purge bcmwl-kernel-source
```
Then:
```
sudo apt install firmware-b43-installer
```
Then reboot and run the script again and we will see what else we can change if needed.

Thanks

---

### Post by odydoum on 2018-03-05
> **wildmanne39 said:**
> Is this determined by actual performance on your computer?


Yes, this was determined by actual performance, or to be more precise, by how stable i perceived my connection.
> **wildmanne39 said:**
> because the other driver is what is called for I suggest you purge the one you are using now and install the other one. There are also error messages concerning this driver in dmesg.

Please do:
```
sudo apt purge bcmwl-kernel-source
```
Then:
```
sudo apt install firmware-b43-installer
```
Then reboot and run the script again and we will see what else we can change if needed.

Thanks
  I did as you asked. I should also add that the results were as expected, meaning even more frequent drops while the applet shows i am connected, probably every 3-5 minutes.

---

