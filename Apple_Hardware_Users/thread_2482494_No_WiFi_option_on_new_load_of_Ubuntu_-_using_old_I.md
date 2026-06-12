---
title: "No WiFi option on new load of Ubuntu - using old Intel MacBook Pro"
date: 2023-01-02
forum: Apple Hardware Users
---

### Post by ejwjohn on 2023-01-02
I have decided to learn more about Linux and have loaded the latest version of Ubuntu desktop onto my old MacBook Pro.
The first issue I come across is that I have o option to select WiFi.

I am no expert on Linux but managed to determine that the wireless Networking hardware in my system is a Broadcom 4360 14e4 43a0 rev 3 I cannot seem to find any driver for it and I have no idea how to install it when I do find it.

One other piece of info that could be of importance is that on checking my devices on the system i notice that one intel Communications controller does not appear to have any Driver linked to it ??? not sure if this is a "red Herring" or important..

In an attempt to further isolate this issue I have an old Mac Mini also, and that system has been loaded up with Ubuntu as well and that appears to work fin in regard to WiFi but i have another issue on that system which will be the subject of another post.

Any help to resolve this WiFi issue would be greatly appreciated.

Thank You
JohnW

---

### Post by howefield on 2023-01-02
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by tea for one on 2023-01-02
Have you seen the Broadcom info here [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)?

---

### Post by ejwjohn on 2023-01-02
Hello,

Firstly, thank You for your response.

Yes, I had seen that info and the issue I have is that my Wireless Adapter is being identified as [14e4:43a0} (rev 03) which is not on the list.

And I am unclear on how to proceed from this point.
This is my inexperience showing??

JohnW

---

### Post by tea for one on 2023-01-02
> **ejwjohn said:**
>  identified as [14e4:43a0} (rev 03) which is not on the list.
14e4:43a0 is third from the end of the list suggesting the installation of bcmwl-kernel-source.

N.B. The installation procedure is done in terminal and while connected to the internet with a temporary wired ethernet connection or USB modem or whatever means possible:

---

### Post by ejwjohn on 2023-01-02
> **tea for one said:**
> 14e4:43a0 is third from the end of the list suggesting the installation of bcmwl-kernel-source.

N.B. The installation procedure is done in terminal and while connected to the internet with a temporary wired ethernet connection or USB modem or whatever means possible:



Hi, Yes but that enty does not specify that it is rev 3? so on that basis I ignored it as there are others in the list that are specific about the ref to the rev number.

JohnW

---

### Post by tea for one on 2023-01-02
> **ejwjohn said:**
> Hi, Yes but that enty does not specify that it is rev 3? so on that basis I ignored it as there are others in the list that are specific about the ref to the rev number.
The entries with rev2 and rev3 show where there has been a change of driver.
There doesn't seem to be a change for your device.

---

### Post by ejwjohn on 2023-01-02
Hello,

Tried that, but does not seem to locate the package after I use the following command

sudo apt-get install 14e4:43a0

Not sure if I am formatting the command correctly.
thanks

JohnW

---

### Post by jeremy31 on 2023-01-02
```
sudo apt install bcmwl-kernel-source
```
Reboot

---

### Post by ejwjohn on 2023-01-02
Brilliant... thanks very much everyone on this issue, Now u and running with Wifi

But I thought I was following the instructions correctly in regard to trying to load the individual package... but was a bit mystified, by that as one of the previous instructions was to purge this bcmwl-kernel-source package.

A little more learning....

Thanks

---

