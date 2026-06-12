---
title: "USN-661-1: Linux kernel regression"
date: 2008-10-30
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-10-30
Description: 
===========================================================Ubuntu Security Notice USN-661-1           October 30, 2008linux regressionhttps://launchpad.net/bugs/264019===========================================================A security issue affects the following Ubuntu releases:Ubuntu 8.10This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 8.10:  linux-image-2.6.27-7-generic    2.6.27-7.15  linux-image-2.6.27-7-server     2.6.27-7.15  linux-image-2.6.27-7-virtual    2.6.27-7.15  procps                          1:3.2.7-9ubuntu2.1After a standard system upgrade you need to reboot your computer toeffect the necessary changes.Details follow:Version 2.6.27 of the Linux kernel changed the order of options inTCP headers. While this change was RFC-compliant, it was found thatsome old routers and consumer DSL modems would not route traffic forthese systems when TCP timestamps were enabled. As a workaround, TCPtimestamps were disabled via sysctl.This update restores the previous ordering of TCP options, andreenables TCP timestamps. We apologize for the inconvenience.





[More...](http://www.ubuntu.com/usn/usn-661-1)

---

