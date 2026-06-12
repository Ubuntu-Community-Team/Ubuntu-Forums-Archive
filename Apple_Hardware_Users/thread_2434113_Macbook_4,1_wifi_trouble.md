---
title: "Macbook 4,1 wifi trouble"
date: 2019-12-30
forum: Apple Hardware Users
---

### Post by tiny2go on 2019-12-30
Hi Ubuntu community! It's my first time here, I'm new to Linux overall, and I could really use some help!

I currently have Lubuntu on my 2008 macbook 4,1 however I'm having a real tough time getting the wifi to work. I know that my computer has a weird Broadcom Wifi driver after perusing the forums. I found this particular forum of someone having the same problem but the solution didn't work for me: [https://ubuntuforums.org/showthread.php?t=2210202](https://ubuntuforums.org/showthread.php?t=2210202)

Currently I can see all the wifi networks, but none of them seem to connect. In the "Additional Drivers" tab, it won't let me select the broadcom device, and seems to always go back to "do not use this device."

Here's some info that might help: 

tony@TonyHackbook:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
tony@TonyHackbook:~$ lsb_release -d
Description:    Ubuntu 18.04.3 LTS
tony@TonyHackbook:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)


Thanks in advance!!

---

### Post by wildmanne39 on 2019-12-30
Hello and welcome to the forum.

Please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created. 

*Thread moved to **Apple Hardware Users a more appropriate sub-forum**.*

---

### Post by tiny2go on 2019-12-30
Hi wildmanne, I hope this is right:

[https://pastebin.com/S0kPajvp](https://pastebin.com/S0kPajvp)

---

### Post by wildmanne39 on 2019-12-30
Please do:
```
sudo apt purge bcmwl-kernel-source
sudo apt install firmware-b43-installer
```
Make sure your wired connection is unplugged then reboot.

---

### Post by tiny2go on 2019-12-30
I'm replying through wifi and it feels good! Cheers!! :p

---

### Post by wildmanne39 on 2019-12-30
Glad it worked, please use thread tools at the top of the page to mark the thread solved.

Thanks

---

