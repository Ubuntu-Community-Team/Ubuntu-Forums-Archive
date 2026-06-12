---
title: "Not detected network devices on Lenovo Yoga 2 13&quot;"
date: 2014-08-10
forum: Any Other OS
---

### Post by mOrzan90 on 2014-08-10
Hi,

last wee my friend VF came to my house with his Lenovo Yoga 2 13 just bought on-line (with Windows 8 already inside).
He came to me because he wanted to install for the first time a Linux  os. I suggested Linux Mint 17 Mate (based on Ubuntu Trusty Tahr).

Before installing, I showed him the Live version (which runs on RAM,  without making changes to the system) with my external CD player. It was  fine, faster than Windows and the touchscreen worked. The wi-fi didn't  work, but I thought it was because there were no drivers (it was in  Live, I thought).

After the Live tour, back on Windows and we note that miss the network devices! Panic ... ](*,)

With my laptop, I looked on the internet and I found [this thread]("http://ubuntuforums.org/showthread.php?t=2215044"). I read  all 10 pages of the topic, and I tried the Haohe's  procedure ([post #26]("http://ubuntuforums.org/showthread.php?t=2215044&page=3&p=13001552#post13001552")) :wink: .
I installed Linux Mint next to Windows to be able to perform the procedure.

The Lenovo couldn't connect to internet, so I performed step 1 on my  computer and then copy packages (and their dependencies) and the *workspace* folder on him computer.

Then I had the problem in step 6, that I solved following the [post #35]("http://ubuntuforums.org/showthread.php?t=2215044&p=13036627#post13036627") of chili555.

I ran all the commands and I didn't got no errors.

I reboot (point 7), did access in Mint, but still does not detect network devices!
I try to start Windows and give me error!

So in summary, I installed Linux next to Windows, I followed the steps  and now Windows will not start, and on Linux is impossible to connect to  the Internet.

After an advice I tried these commands:
```
lspci -nn | grep 0280
rfkill list all
lsmod | grep idea
```

with this results:
```
ealtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
```
```
0: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no
```

the last don't have answer

Someone can help me, please?
(and sorry for my english)

---

### Post by howefield on 2014-08-10
Thread moved to "*Other Operating Systems and Projects*" forum.

---

### Post by chili555 on 2014-08-10
The driver for this device is included in Ubuntu 14.04. Let's load it and see what happens:```
sudo modprobe rtl8723be
iwconfig
dmesg | grep rtl
```

---

### Post by mOrzan90 on 2014-08-11
ok, we have
```
modprobe: FATAL: Module rtl8723be not found.
```
```
lo        no wireless extensions.
```

and the third don't give answer

---

### Post by chili555 on 2014-08-11
It is certainly present in Trusty:```
chili@T410:~$ modinfo rtl8723be
filename:       /lib/modules/**3.13.0-32**-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     0D59E0301AAA6E5A93400BB
<snip>
```Is your Mint fully updated? What kernel version are you using?```
uname -r
```

---

### Post by mOrzan90 on 2014-08-12
```
3.13.0-24-generic
```

I installed Linux Mint 17 Qiana with Mate, based on Ubuntu 14.04 (Trusty Tahr) for repository

---

### Post by chili555 on 2014-08-12
> **mOrzan90 said:**
> ```
3.13.0-24-generic
```

I installed Linux Mint 17 Qiana with Mate, based on Ubuntu 14.04 (Trusty Tahr) for repositoryI see. The module rtl8723be doesn't appear until 3.13.0-27; that is, one update away from your -24. 

In order to compile the driver from source code, you would need many prerequisites, build tools, linux-headers, etc. and all their dependencies. I assume you'd transfer them on a USB key. It seems a whole lot easier to simply download the 3.13.0-32 (the latest) linux-image and install it instead. I am not familiar with the Mint repos, but in Ubuntu, you'd need this: [http://packages.ubuntu.com/trusty/linux-image-3.13.0-32-generic](http://packages.ubuntu.com/trusty/linux-image-3.13.0-32-generic)

The dependencies, the packages noted with red dots, are probably already installed; check:```
sudo dpkg -s <some_package> | grep Status
```Here is an example from my machine:```
chili@T410:~$ sudo dpkg -s module-init-tools | grep Status
[sudo] password for chili: 
Status: install ok installed

```

---

### Post by mOrzan90 on 2014-08-20
Hi, sorry for the long time, but my friend was in holiday.

We installed with success the package linux-image-3.13.0-32-generic (3.13.0-32.57) and his dependencies.

Now I repeat the procedure of the [other thread]("http://ubuntuforums.org/showthread.php?t=2215044") or I need other packages?

Thaks for your help

---

### Post by chili555 on 2014-08-20
> **mOrzan90 said:**
> Hi, sorry for the long time, but my friend was in holiday.

We installed with success the package linux-image-3.13.0-32-generic (3.13.0-32.57) and his dependencies.

Now I repeat the procedure of the [other thread]("http://ubuntuforums.org/showthread.php?t=2215044") or I need other packages?

Thaks for your helpWhat does this tell us?```
rfkill list all
```

---

