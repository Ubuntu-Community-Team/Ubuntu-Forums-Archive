---
title: "[SOLVED] Please help! I'm upgrading from Dapper to Edgy to Feisty"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by mahasmb on 2007-06-09
I initially installed 6.06 LTS a few months ago, but wireless wasn't working because I have the BCM43XX card. After a lot of tinkering and looking around I got it fixed. So wireless was working beautifully.

Just the other day I decided to upgrade to Feisty Fawn. So I upgraded to 6.10 and am now in the middle of upgrading to 7.04. (Wireless didn't seem to be working with 6.10... but I've decided to leave that problem for when I'm finished upgrading to Feisty ). But I've been asked this and I don't know which to pick:


======================================
Replace the customized configuration file '/etc/modprobe.d/blacklist' ?

--- /etc/modprobe.d/blacklist 2007-05-02 20:24:08.000000000 -0400
+++ /etc/modprobe.d/blacklist.dpkg-new 2007-04-03 10:03:42.000000000 -0400
@@ -24,5 +24,7 @@

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
-#module below does not work with Broadcom 4318 wireless cards
-blacklist bcm43xx
+
+# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
+blacklist r818x
+blacklist r8187

=======================================

So basically it's asking me if I want to keep my old customized file or upgrade to the new one. I don't wanna mess this up and I really don't know which to choose.

And oh, I'm pretty new to Ubuntu. I'm trying to see if I can replace Windows with it.

---

### Post by newlinux on 2007-06-09
You could just make a copy of your customized file and overwrite the standard one if you need it later.

---

