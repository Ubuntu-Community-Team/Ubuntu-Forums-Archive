---
title: "RT5370 wireless adapter usb driver on Backtrack 5 R1"
date: 2012-08-27
forum: Any Other OS
---

### Post by JoshScuban on 2012-08-27
Hello everyone!!

As you can imagine from reading the title, I need to install the driver for a wireless adapter with the RT5370 chipset on Backtrack 5 R1..
I already searched for a solution in the forums, and I found a thread about it ([HTML]http://ubuntuforums.org/showthread.php?t=1800178&highlight=RT5370+backtrack+R1[/HTML]), where a user of this forum explains how he/she installed this driver on Backtrack 5 R1, editing some directories in the makefile. His explanation is the following:

> i wanted to read the makefile and noticed it was not looking in the right directories for some reason and was missing Module.symvers in my /usr/src/linux when compiling the first time; i do know a few things unix so i used: 

Code:
```
locate Module.symvers
cp "dir without quotes where found" /usr/src/linux

```
I tried changing the following in the makefile with after using locate to locate some of the requirements of the makefile

Code:
```
LINUX_SRC =/lib/modules/$(shell uname -r)/build
to
LINUX_SRC =/usr/src/linux
```
and below it:

Code:
```
LINUX_SRC =/lib/modules/$(shell uname -r)/kernel/drivers/net/wireless
to
LINUX_SRC =/usr/src/linux/drivers/net/wireless
```
ran
Code:
```
make
make install
modprobe rt5370sta
```
and now it works in Wicd after changing the preferences for wlan0 to Ra0 I can connect and it works

I tried doing the same, but I don't know how to locate the requirements of the makefile..so I cant get it to work.. **could someone explain to me **(I'm a real newbie when it comes to Linux, but I'm willing to learn) **what could I do?**

It would be great to get my new wireless adapter running..

Thanks!

---

### Post by Ms. Daisy on 2012-08-29
You know that Backtrack is a toolkit designed for specific security tasks such as penetration testing, right? It's not designed to be a day-to-day operating system for typical desktop users.

Aside from that Backtrack is built on an Ubuntu base, but it's not supported by Ubuntu per se.

---

