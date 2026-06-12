---
title: "ATI driver with Feisty?"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-23
Do I use the same ATI driver with Feisty that I used with Edgy and Dapper?
kh

---

### Post by v8YKxgHe on 2007-03-23
If you are new to Linux I'd suggest holding back on using Feisty until it's released ( April 19th ). It's only just gone into Beta stage, so - don't expect things to work as they should and things will break.

However, you should be able to use the new restricted-manager to install ATI drivers in Feisty now.

---

### Post by kittyhawk63 on 2007-03-23
> **AlexC_ said:**
> If you are new to Linux I'd suggest holding back on using Feisty until it's released ( April 19th ). It's only just gone into Beta stage, so - don't expect things to work as they should and things will break.
However, you should be able to use the new restricted-manager to install ATI drivers in Feisty now.

Here is what I have done:
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx **(I start having trouble at this point) **It won't take this command as it has in Edgy and Dapper.

I've read that you can't get Automatix to work in Feisty yet. Any other suggestions?

Note: I did finally get it to install, only later on reboot to have it blocked from botting into Feisty. I will be waiting for Feisty to greatly improve before I install it again. Maybe by then most of the major bugs will be worked out.

---

### Post by cyberdork33 on 2007-03-23
There should be a new management tool in Feisty to install restricted modules. Look through the menus.

---

### Post by kittyhawk63 on 2007-03-23
> **cyberdork33 said:**
> There should be a new management tool in Feisty to install restricted modules. Look through the menus.

Thanks. It got so messed up that I am going back to Dapper until most of the major bugs are worked out with Feisty. That should take several months (at least).
kh

---

### Post by v8YKxgHe on 2007-03-24
> **kittyhawk63 said:**
> Thanks. It got so messed up that I am going back to Dapper until most of the major bugs are worked out with Feisty. That should take several months (at least).
kh

Or just wait until it's released. You can't expect Feisty that is in development not to have bugs :P

---

