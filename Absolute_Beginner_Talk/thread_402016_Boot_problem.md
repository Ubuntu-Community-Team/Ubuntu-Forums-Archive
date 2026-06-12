---
title: "Boot problem"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by owerio on 2007-04-05
Hello. With Super Grub Disk I cant fix the grub after a windows install. Then I boot the Ubuntu with Super Grub Disk and used the method on Ubuntu Wiki.


> How to Restore the Grub Menu after a Re-Ghosting:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD. 

First I used the hd0,0 but it didnt helped then used hd0 and it worked. But this time windows is on Grub menu but it doesnt boot. I get an eroor message. Fixmbr also didnt worked.

I dont want to install again windows and ubuntu again. Cause it is the only way that I use for grub problems. I dont know how I fix the issue? How can I bring back windows boot?

---

### Post by antoz on 2007-04-05
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 

The above link may be of some help

---

