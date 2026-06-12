---
title: "DWL 122 install question."
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by jfg on 2005-09-27
Hello,

I am just trying to install a wireless USB adapter. Yes, the DWL 122. I have searched the forum, followed instructions, re followed instructions and still get errors and it still doesnt work. Lots of the instructions are "Just add this to this"; As I am quite new to Linux, I beleive I need to take a step back and be led by the hand. Not fun, I know, but I learn fast.
If anyone has an Idea on how to set it up from the very start, please let me know.

And while I'm here, why is there no "ADD" button on the network??

Thank you for your time.

---

### Post by az on 2005-09-27
[QUOTE=jfg]Hello,

I am just trying to install a wireless USB adapter. Yes, the DWL 122. I have searched the forum, followed instructions, re followed instructions and still get errors and it still doesnt work. Lots of the instructions are "Just add this to this"; As I am quite new to Linux, I beleive I need to take a step back and be led by the hand. Not fun, I know, but I learn fast.
If anyone has an Idea on how to set it up from the very start, please let me know.

And while I'm here, why is there no "ADD" button on the network??

Thank you for your time.[/QUOTE]
There is no add button because any network device  that is capable of being used is already there.  The problem is the device is not properly detected.

Install the linux-wlan-ng package and try again.  If it still does not work, here is the bug report about that:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=15346](http://bugzilla.ubuntu.com/show_bug.cgi?id=15346)
And there is a script here that you can use to make your device work:
[http://lists.ubuntu.com/archives/ubuntu-devel/2005-September/010439.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-September/010439.html)

Please let me know if just installing linux-wlan-ng works for you.  It is on your cd.  (actually, it should be cached on your harddrive)

---

### Post by jfg on 2005-09-28
Well, after more researche I jsut decided to purchase a wireless card that is more friendly with Linux. Not sure which one (got it down to two), but it should make my job easier.

Thank you for the response and I'm pretty sure I'll have more.

JF

---

