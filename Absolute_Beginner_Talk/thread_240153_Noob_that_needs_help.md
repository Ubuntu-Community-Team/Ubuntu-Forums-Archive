---
title: "Noob that needs help"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by eldrid001 on 2006-08-20
Hi all. I'm new here. I'm installing ubuntu by live CD, but some windows system overwrites (i have no idea wad) that are due to me installing flyakite osx emulator disallow me to view some of the setup steps during setup. The os is installed but i have no idea wad my username and password is. Is there anyway to retrieve thins information? I cant even log into the os!!

:confused:

---

### Post by taurus on 2006-08-20
Assuming you use GRUB to boot your machine, pick the recovery mode from it and wait for it to boot.  At the prompt, you can look in /etc/passwd to see the exact username of your user with

```
more /etc/passwd
```
Assuming it's called john in this case, then type

```
passwd john
```
Then, reboot and login with user john and the new password that you just created for john...

---

### Post by eldrid001 on 2006-08-20
I tried that, but the weird thing is when i try and boot, it shows usb renewing or something like that, the list just goes on and on, is it some hardware issues?

---

### Post by eldrid001 on 2006-08-21
Hi, i solved the usb problem, but when i type /etc/passwd, its says access denied. Why?

---

### Post by Haegin on 2006-08-21
Try using ```
sudo more /etc/passwd
``` (dont forget the more) and then ```
sudo passwd <username>
```

---

