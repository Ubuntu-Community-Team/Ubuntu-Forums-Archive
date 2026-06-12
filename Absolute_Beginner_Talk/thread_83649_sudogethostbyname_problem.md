---
title: "sudo/gethostbyname problem"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by DudleySmith on 2005-10-29
My PC has a WLAN card, a Netgear WG311v2.  On installation I therefore have no network, and Ubuntu thinks I have no NIC.  So I have downloaded ndiswrapper and the suggested drivers to get it sorted (and cut them onto a CD).  But I can't get any further because there seems to be some verification issue that is stopping me running sudo commands (which nixes most things as far as I can tell).

When I try a sudo command I get an error complaining that the lookup for my domain name (my surname) is failing because gethostbyname() is failing.

I can't add my domain to /etc/hosts (which is what the shell suggests on boot) because it will only open as read-only from File Browser, and I can't do a sudo gedit type command.

My motherboard has an onboard NIC (disabled normally, and when I installed Ubuntu), but when I reenable it, I can't see how to tell Ubuntu about it.

I've been using DOS and Windows for 13 years, but this has me foxed.  Does anyone have any thoughts as to how to proceed?

Thank you for your time.

---

### Post by darth_vector on 2005-10-29
hi,

not sounding good. try booting into safe mode, creating a new user and adding them to the sudoers file. then reboot, login as them and proceed with fixing the other stuff.

---

### Post by Topsiho on 2005-10-29
Hello,

I solved this problem yesterday and hope you can do it also :) :

1. **reboot into recovery mode**,  I became root, which was just what I needed.

2. When root you can go to /etc/hosts and edit this using an editor from the command line. I used vim but that is not so easy to use if you never did this before. But maybe you know another command line editor, which if necessary you can install from the command line too, such as joe or whatever.

3. Next reboot again, this time normally and try if you can sudo now.

If not I am afraid I cannot help you further, only thing is that your /etc/hosts file should be OKidoki :)

Topsiho

---

