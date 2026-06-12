---
title: "Boot Problem - Dual boot ubuntu - Mac OS"
date: 2011-01-30
forum: Apple Hardware Users
---

### Post by cliffhang on 2011-01-30
Hi, I'm new to this forum but I have used linux for some time now.
Now I am trying to install Ubuntu on my macbook, to dual boot it with Leopard.

The first thing i did was to install rEFIt boot selector
Then I splitted my hard drive with boot camp assistant.
Then i burned a live CD and restarted, but I never could boot from it, so after a while I found on the internet how to fix the blank screen problem, by selecting acpi=off.
Ok, now I could successfully install the OS no problems there. So after the restart I selected to start linux in rEFIt and got into GRUB, there i booted up Ubuntu, and got the same blank screen as in the Live CD before.

So I googled.. and the only solution I found was to change "quiet splash" into "nomodeset"
and when I did that, then came all the white lines (loading.. this and that) and again the damn blank screen again.

So any suggestions? plz..

Using:
MacBook Model 5,2
Ubuntu 9.10 (cause i did not know how to set acpi=off in 10.10)

**Solution**
In GRUB i typed "nomodeset acpi=off" instead of "quiet splash"

---

### Post by NoBugs! on 2011-01-30
Have you tried
[https://help.ubuntu.com/community/MacBook5-2/Maverick](https://help.ubuntu.com/community/MacBook5-2/Maverick)

---

### Post by cliffhang on 2011-01-30
No, I used this a lot though [https://help.ubuntu.com/community/MacBook5-2/Karmic](https://help.ubuntu.com/community/MacBook5-2/Karmic)
I selected 9.10 because in 10.10 I never got to the install menu :(

Maybe I should try 10.10 again if I don't solve this soon..

---

