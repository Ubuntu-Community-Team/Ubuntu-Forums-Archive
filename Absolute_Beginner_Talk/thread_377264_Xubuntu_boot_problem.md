---
title: "Xubuntu boot problem"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by ss_mckinney on 2007-03-05
I just finished a reinstall of Xubuntu 6.10 on a dell inspiron 2500 which I dual boot with XP.  The installation seemed smooth, but now whenever I try to boot up Xubuntu (in normal or recovery mode), I get a bunch of static looking stuff and then a blank screen with a sound effect that happens every few minutes.  Any suggestions?

---

### Post by taurus on 2007-03-05
Boot into recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Choose **vesa** as your video card for now.  When you're done, reboot with

```
shutdown -r now
```
What kind of video card do you have on that machine?

---

### Post by ss_mckinney on 2007-03-07
Not sure what kind of video card I have.  Where can I find out?

---

### Post by taurus on 2007-03-07
It should show up on this list with this command from a terminal.

```
lspci
```

---

### Post by ss_mckinney on 2007-03-08
OK, I got it to boot, but now my internet connection is not showing up.  The laptop sees my router and my wireless card seems to be acting normally.  Any test I can run or something?

---

### Post by taurus on 2007-03-08
```
/sbin/ifconfig
ping -c 3 www.google.com
```

---

### Post by ss_mckinney on 2007-03-08
The first command gave me a bunch of error messages (not really sure what to look for).

The second: unknown host [www.google.com](www.google.com)

---

### Post by taurus on 2007-03-08
Can you post the output of the first command?

```
/sbin/ifconfig
```
On the other hand, it would be nice if you can list the spec of your laptop especially the wireless card, brand & model.

---

### Post by ss_mckinney on 2007-03-08
lo  Link encap:local loopback
     inet addr:127.0.0.1  Mask:255.0.0.0
     inet6 addr: ::1/128  scope:host
     up loopback running mtu:16436 metric:1
     rx packets:332 errors:0 dropped:0 overruns frame:0
     tx packets:332 errors:0 dropped:0 overruns carrier
:0
     collisions:0 txqueuelen:0
     rx bytes: 24728 (24.1 KiB)  txbytes:24728 (24.1 KiB)

wifi0  Link encap:unspec hwaddr 00-09-7c-d1-8a-d1-00-00-00-00-0-00-00-00-00
     up broadcast running multicast mtu:2312  metric:1
1786
      tx packets:0 errors:5 dropped:0 overruns:2 carrier:0 collisions:0 txqueuelen:100
      rx bytes:0 (0.0b)  tx bytes 954 (954.0 b)
      interrupt: 3 base address:0x2100


card is a cisco systems-350 series    air-pcm352

---

### Post by ss_mckinney on 2007-03-09
Does anyone have any suggestions?

---

