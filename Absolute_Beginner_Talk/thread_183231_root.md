---
title: "root?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by SZF2001 on 2006-05-27
I try to do something with ndiswrapper, and this comes along:

> coleman@ColemanNetwork:~/Drivers/WUSB11v4_08272004/Drivers$ ndiswrapper -i WUSB11v4.inf
Installing wusb11v4
Unable to create directory /etc/ndiswrapper/wusb11v4. Make sure you are running as root


Run as root? I thought I was! wtf

---

### Post by Koech on 2006-05-27
Just run as root and see what happens.

---

### Post by Perfect Storm on 2006-05-27
Tried with 

sudo ndiswrapper -i WUSB11v4.inf

---

### Post by meng on 2006-05-27
Unlikely you are, since the prompt ends in $. If you're root, prompt usually ends with #. What happens if you try "sudo ..."?

---

### Post by mostwanted on 2006-05-27
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by SZF2001 on 2006-05-27
Awesome, sudo worked.

But now this:

> coleman@ColemanNetwork:~/Drivers/WUSB11v4_08272004/Drivers$ sudo ndiswrapper -i WUSB11v4.inf
Password:
Installing wusb11v4
Parse error in inf. Unable to find section @mdusb.out

Any help?

---

