---
title: "[SOLVED] Linux Build Enviroment"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by funkshun on 2007-07-22
Ok so I just go my ethernet connection going. I'm now trying to get my wirless activated. I have a broadcom 802.11g wirless connector (BCM4311 chipset) wich ubuntu does not recognize. I was following this manul on how to install.

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

1st I removed any existing copies of ndiswrapper ( there were none)
2nd - Disable any competing drivers
3rd - Prepare the linux build enviroment **This is were I ran into problems.**

    **"**You will need to install the essential build files to compile the driver:

user@ubuntu:~$ sudo apt-get update
user@ubuntu:~$ sudo apt-get install build-essential

Install the correct headers for your version of Ubuntu: (don't worry if it tells you that yours are up to date.)

user@ubuntu:~$ sudo apt-get install linux-headers-`uname -r`
user@ubuntu:~$ sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build**"**  So I proceed

funkshun@funkshun-laptop:~$ sudo apt-get install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-uname -r
funkshun@funkshun-laptop:~$

Im new to ubuntu..so I am stuck any help would be appriciated My objective is to finish out the tutorial so I can get my wirless working. Thanks

---

### Post by sad_iq on 2007-07-22
You misspelled ```
sudo apt-get install linux-headers-`uname -r`
``` just copy-paste from that how-to and you should be fine!!!

---

### Post by funkshun on 2007-07-22
Thanks I did that it seems to be taking me to the next process.

---

### Post by annda on 2007-07-22
what is the error now? remember, always copy&paste the commands - the backquotes (`) are important because they tell the system to execute the command within and return the results. this is how you get the correct kernel version without typing or even knowing it...

---

