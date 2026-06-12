---
title: "Seamless Virtualization"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by thecomputingexpert on 2007-07-06
Hi guys, I have been following this tutorial from Ubuntu: [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization). I am using Virtual Box with an XP Pro SP2 box installed, I have followed it exactly but when try and connect with this:

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Windows Media Player\wmplayer.exe" <ip>:3389 -u administrator -p password

(I did add the IP where it says <ip>)

it just brings up the following statement and not the log in screen like it should:

Autoselected keyboard map en-gb

Can anyone help me, thank you

---

### Post by lazyart on 2007-07-06
1- can you ping the address?
2- did you enable remote desktop in the windows installation?

---

### Post by the8thstar on 2007-07-06
I'm experiencing similar problems but I have no idea what the IP should be... My system detected 2 unused IP addresses... I tried each, to no avail. Any ideas on how to fix the problem???

---

### Post by the8thstar on 2007-12-16
Bump

---

### Post by HermanAB on 2007-12-16
In Windows, open a DOS box and type:
c:\> ipconfig /all

Use that IP address from Linux.

Cheers,

Herman

---

