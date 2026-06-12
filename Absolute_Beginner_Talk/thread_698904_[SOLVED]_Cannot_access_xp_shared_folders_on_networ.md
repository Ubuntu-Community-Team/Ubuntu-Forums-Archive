---
title: "[SOLVED] Cannot access xp shared folders on network..."
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by pete_zahuat on 2008-02-16
I'm having a little problem here (see title above).  When I first installed gutsy 7.10 I was able to access shared folders on a xp computer with no problems at all.  Now I cannot see the xp computer name anymore in my network folder.  Is there a way access them again?  Do I need to install something in order to access the folders?

---

### Post by michaelzap on 2008-02-16
I just recently had this problem also with a Samba network drive. It was driving me nuts for a while, and I never did figure out why it wasn't visible from Ubuntu by share name. I just worked around it by accessing it using its static ip address, which works fine.

I can access other network shares by share name (mounted in my fstab or via smb://). But nothing shows up in my Windows Network display in Nautilus at all. Not even the shares that are properly mounted by name at boot.

I don't think that it used to be this way, so maybe an update broke something.

---

### Post by dupper on 2008-02-17
Happened the same thing to me and the solution was also the same: connecting to the IP addresses...

---

### Post by pete_zahuat on 2008-02-17
I tried doing the ip address but still no luck.

---

### Post by michaelzap on 2008-02-17
Did you type it into the Nautilus address bar, like so?

smb://192.168.0.120

---

### Post by pete_zahuat on 2008-02-17
Just did that and a message popped up saying that folders could not be displayed.

---

### Post by michaelzap on 2008-02-17
Do you have Firestarter installed? Try turning off the firewall to test. Are you able to access these shares from other machines/systems?

---

### Post by pete_zahuat on 2008-02-17
I disabled the firewall and was able to see the shared folders on my network, but when I clicked on the name, my computer seemed liked it was loading something for about 20 seconds then it said "folder contents could not be displayed on windows network".

---

### Post by pete_zahuat on 2008-02-17
bump

---

### Post by michaelzap on 2008-02-17
Make sure that you have Samba installed and setup properly and that the Windows shares are working:

[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by pete_zahuat on 2008-02-17
Got it working now!  Thanks for the help!

---

