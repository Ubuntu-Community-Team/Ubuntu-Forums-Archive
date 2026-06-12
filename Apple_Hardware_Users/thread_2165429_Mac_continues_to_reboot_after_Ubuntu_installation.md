---
title: "Mac continues to reboot after Ubuntu installation"
date: 2013-08-04
forum: Apple Hardware Users
---

### Post by boxman2 on 2013-08-04
I have installed Ubuntu 12.04 LTS onto a Macbook Pro 2006 (Mactel).  The installation was not a dual boot installation, but a single installation of Ubuntu.  The computers CD drive is not working so I had to install form a USB stick, but I was able to test Ubuntu from the USB stick without any problems and then performed the installation.  The installation indicated that it succeeded.  When I power the computer back up after installation, I get the GNU GRUB version 1.99-21ubuntu3.9 menu.  There are four choices on the menu as follows:  

Ubuntu, with Linux 3.5.0-23-generic
Ubuntu, with Linux 3.4.0-23-generic (recovery mode)
Memory test (memtest86+)
Memory test (memetest86+, serial console 115200)

When I choose the first choice, the screen goes to a black screen with a cursor blinking in the corner for a few seconds and then shuts down and reboots until it comes back up with the GRUB menu again.  If I pick the first choice again (or the second choice) it follows the same behavior continually cylcing back to the GRUB screen.  

This is my first experience with Linux and I'm primarily a windows user, so I don't have any idea where to even look to solve the problem.  I did try re-installing the installation a second time and still have the same problem.  Any help with solving the problem would be appreciated.

---

### Post by coffeecat on 2013-08-05
*Thread moved to **Apple Users**.*

---

### Post by saunite on 2013-08-05
If you go to the recovery mode, does it show anything different? Or is EXACTLY the same behavior?

---

### Post by r3dbeard on 2013-08-06
I recently did the same thing and had a similar issue. For me I think it just came down to a bad download/install. I recently (as in this weekend) installed from scratch on my Macbook Pro (late 2008). Unless you're 100% committed to LTS releases I would recommend giving 12.10 a try. Many of the features that require tweaking in 12.04 work "out of the box" in 12.10. I would also recommend hard-wiring to the internet during the install to get the updates at the same time. Mine still lags for about 15-30 seconds after the startup '*gong'  *and until I ran updates on the fully-installed system it took a bit at the (very distorted) splash screen as well. pm me if I can help further.

---

### Post by boxman2 on 2013-08-06
When I choose recovery mode, I don't get exactly the same behavior, I get the screen dump of the loading activities up until a certain point and then it seems to freeze and reboot back to the grub menu.  It is not consistent as to which screen dump line it stops on, but most often it stops on a line that lists the following:  

usbcore: registered new interface driver appletouch

After it hangs on that line for a few seconds it then reboots automatically back to the grub menu

Also, I did get linux to start once after just choosing the non recovery mode prompt several times in a row (don't know how many), but when I logged out and powered off it goes back to the same behavior.

---

