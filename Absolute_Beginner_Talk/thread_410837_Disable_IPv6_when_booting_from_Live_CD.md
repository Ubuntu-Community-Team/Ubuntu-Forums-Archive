---
title: "Disable IPv6 when booting from Live CD"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by sricho on 2007-04-16
Hi, I’m new to Ubuntu.  I’d like to dual boot eventually but for now just want to boot from the Live CD.  I couldn’t get anywhere on the internet until I typed “about:config” in the address bar for Firefox, and then disabled IPv6.  I can go wherever I want now.  Prior to that both Firefox and ssh would time out before getting anywhere.  The stuff I saw for disabling IPv6 system wide was pretty much along the lines of

“Open the file /etc/modprobe.d/aliases
Add the first three lines to the file. The line with # starting is already in the file. Find it and add the # in front of it.

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

After making these changes a reboot is required.”

Is it possible to fix this for the whole system when I can’t reboot?  I’d like to access another computer using ssh and figured since disabling IPv6 fixed my general internet problem it would help with this.  I’m using Ubuntu 6.10.  Thanks a lot.

---

### Post by lamalex on 2007-04-16
[https://help.ubuntu.com/community/LiveCDPersistence](https://help.ubuntu.com/community/LiveCDPersistence)

enjoy!

---

### Post by sricho on 2007-04-16
Thanks.  Looks perfect :D

---

