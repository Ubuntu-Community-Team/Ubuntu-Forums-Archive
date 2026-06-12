---
title: "breezy ibook troubles"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by aufschreibesysteme on 2006-03-22
Hi, I have installed Breezy on my old iBook G3 (Clamshell). It works fine with plugged in Ethernet (on my local LAN-Router and DHCP) except that everytime I start it unplugged from the network the login-procedure fails after the login sound. Login screen is normal, input of login/password is possible. After return the screen turns brown, I can see the mouse arrow, hear the logion sound but then it stops doing anything. No windowmanager no menues, only brown screen and movable mouse arrow.
Plugging ethernetplug in again it works as expected.

would appreciate any hint, help, thanks

---

### Post by RHTopics on 2006-03-22
See if you can log in from a terminal screen while your unplugged from your network.  Otherwise, follow the steps while being plugged into your network.

First, press keys "control", "alt", and "F1" at the same time to switch over to text based terminal screen "tty1".

If that works, you should have a login prompt.  Try to login.  If you can login, then browse/search the "messages" files in subdirectory "/var/log" for log entries that may pertain to your login problem.

Enter "less /var/log/messages" at the command line to browse through the messages file.  Enter "tail -200 /var/log/messages | less" to look at just the last 200 lines of the messages file.

To switch back to the graphical login screen, press "control", "alt", and "F7" at the same time.

Hope that can help you towards diagnosing your problem.

---

