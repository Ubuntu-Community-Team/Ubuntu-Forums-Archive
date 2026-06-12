---
title: "Packard Bell Laptop Button"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by howiehowie93 on 2008-02-23
Hi

I have a PB EasyNote Laptop Model ED1 (I think its also known as A418). there is a button on the front Panel which, in Windows Flashes Blue when Wireless is enabled and steady blue when connected to a wireless network. It also can be pushed to enable/disable wireless as well as a function Button on the keyboard.

This machine is a duel Boot XP Pro/Gutsy. This button gives no indication while running linux but there's the wireless icon which is adequate.

I had no worry about this until i installed SUSE 10.3 to try it out and the button works and indicates as it does with Windows! 

Is there something SUSE has which I can install/activate in Gutsy which will make it happen? I tried the latest release of 08.04 but it doesn't work with that either.

regards and thanks in advance.

Howie

---

### Post by Presto123 on 2008-02-23
It's a matter of restricted drivers in Gutsy. What is your wifi card type?

If you don't know, look at the output of:
```
lspci
```

If you can't understand which it is, post that output here in code tags (# sign on reply window).

---

### Post by howiehowie93 on 2008-02-23
Hi again,
the laptop has a Centrino Chipset and it has the Wirelss controler below pasted as you suggested from lspci:

02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

I forgot about restricted drivers but the only one listed in the Restricted Drivers Manager is a Software Modem Driver.

What next to do as i assume Gutsy has the optimum Drivers already in the Kernel?

regards
Howie

---

