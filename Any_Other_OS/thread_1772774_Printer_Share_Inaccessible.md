---
title: "Printer Share Inaccessible"
date: 2011-06-01
forum: Any Other OS
---

### Post by tareqf1 on 2011-06-01
I am relatively new to the Ubuntu world as a full time user. Currently I am using Ubuntu 11.04 (Linux Mint 11 distro) in my office PC. 

For several days I am having a problem adding a printer which is attached to a Server PC running Windows 7. There are three printers there. All shared and working. And I easily added one printer using Windows Printer via SAMBA. That is relatively easy task. But I could not add other two as whenever I try to verify the connection, it says "Printer Share Inaccessible". 

I searched for a solution but unable to find it. I was wondering what could be the problem when one of the printer is accessible and others are not. 

Finally I found the problem. **It turns out that Linux can't handle space in the Printer Share name** and the Printer Share name was : "Canon iR23182320 UFRII LT". 

So I just simply edit the Printer Share Name as "CanoniR23182320UFRIILT" in the windows machine and Ubuntu added the printer easily.

---

### Post by Perfect Storm on 2011-06-01
Moved to Other OS/Distro Talk.

---

### Post by combinatorist on 2011-06-03
I also have run into this problem. Unfortunately, I am possibly the only person using Linux on the network, and there is very little chance of getting them to change the printer name.

Does anybody have any idea as how to work around this problem without changing the name of the printer on the network?

---

