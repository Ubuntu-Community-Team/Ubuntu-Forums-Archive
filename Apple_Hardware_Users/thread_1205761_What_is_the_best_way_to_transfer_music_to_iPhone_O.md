---
title: "What is the best way to transfer music to iPhone OS 2.2.1 on Ubuntu today?"
date: 2009-07-06
forum: Apple Hardware Users
---

### Post by wersdaluv on 2009-07-06
At this time of writing, the current iPhone OS is 3.0 but syncing isn't possible on Ubuntu yet. I don't know how long it is going to take but I still decided to downgrade to 2.2.1.

I have an iPod Touch 2g 16gb. To my best knowledge, I followed the instructions from [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) correctly. However, whenever I run ```
sudo ipod-touch-mount
``` I get
```
ssh: connect to host ipod port 22: No route to host
read: Connection reset by peer
```. 

What did I do wrong? I wasn't able to install the BSD Subsystem package because Installer doesn't seem to work anymore. I installed openssh from Cydia and I suppose that it should satisfy the requirements for the instructions of installing openssh and BSD Subsystem from Installer. 

I set 192.168.1.33 as the static IP address. I just noticed that it disabled internet access in my iPod. Any idea why? What is a right IP address to use for this purpose? Other adds don't remain static.

Syncing the old iPhone firmware is still tricky for me even if it has been out for a while. What could be the most sophisticated way to transfer music using Ubuntu? I really can't stand iTunes.

EDIT:
If it makes a difference, my wifi router is connected to a wired router.

---

