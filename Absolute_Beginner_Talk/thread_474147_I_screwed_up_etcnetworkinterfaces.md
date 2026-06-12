---
title: "I screwed up /etc/network/interfaces"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-06-14
Ok, I made some changes to /etc/ntwork/interfaces based on some Google searches (I was having trouble conntecting to the internet), and now I can't log on (I log on, the cursor appears, it sits for a while, and then a grey box appears in the top-left corner of the screen). Anyway, they only way I can log on is through the failsafe terminal. So I need a way to edit that /etc/network/interfaces from the terminal, but it says that it can't. So, any ideas?

Thanks.

---

### Post by mattze on 2007-06-14
you have to be root to edit that file (just a reminder), so use sudo.
can you post the error message?

---

### Post by Austin_KW on 2007-06-14
You will need to use a terminal mode editor. A lot of people us nano (i use vi but it is convoluted)
sudo nano /etc/network/interfaces
make your changes and ctrl-x to exit, and answer yes to save your changes.  As a minimum your interfaces should have the loopback adapter and maybe your first ethernet adapter 
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

```

---

### Post by Yes on 2007-06-14
Ok, I tried to reboot in Ubuntu (I dual-boot with WinXP), and where it normally says "GRUB loading stage 1.5" it just said a bunch of random symbols, and then waited for input.  I pressed enter, and it bypassed the GRUB menu and went straight into Windows.  Any ideas?

Thanks.

---

### Post by Yes on 2007-06-14
Oops, I had just forgotten to unplug my iPod :$ .

Anyway, I fixed the /etc/network/interfaces ,and I can log in now.  Thanks!

---

