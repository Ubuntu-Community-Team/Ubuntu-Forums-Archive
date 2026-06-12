---
title: "install ati from live cd how do i do it?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by rickycodie on 2007-07-01
i need to install the restricted driver from the live cd, but i dont know how. i just got this new toshiba and x fails so i can't get online unless  i use the live cd.

---

### Post by Raineer on 2007-07-01
Are you sure you're not online already?  Even though x doesn't start, try:
```
ifconfig
```

And see if it reports you are online, if so try

```
sudo apt-get install linux-restricted-modules-2.6.20-15-generic
```
This should include the ATI driver (fglrx)

After you download the driver, you should be able to:
```
sudo dpkg-reconfigure xserver-xorg
```

And select the proper drivers and X should start after that

---

### Post by rickycodie on 2007-07-01
i'm sure i'm not online, i'm on a laptop and my network is secure, i never typed in the access code. i tried sudo apt-get update and it couldn't connect to anything.

---

### Post by Raineer on 2007-07-01
Do you have another system you can download it to and burn to CD?

This link could help:
[http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-generic](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-15-generic)

---

