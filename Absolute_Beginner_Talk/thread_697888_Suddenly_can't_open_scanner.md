---
title: "Suddenly can't open scanner"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by bighorse on 2008-02-15
Suddenly xsane cannot access my scanner.  (Scanimage and sane-find-scanner can all locate the the scanner and properly identify it (Microtek Scanmaker 4800) ),  The xsane error is "Access to resource has been denied."

Running version 7.10 with the current xsane package (0.00-0.991-3ubunt) and the scanner has been working properly up until I temporarily moved it to another system to troubleshoot the same error condition.  When reconnecting to the original system the problem suddenly appeared.

File /etc/group shows the following entry for the scanner:  "scanner:x:104:hplip,tom: which is unchanged from the working setting.  I was under the impression that this was the permissions file.  Help!

---

### Post by Mark_in_Hollywood on 2008-02-18
Please unplug the scanner, reboot, plug the scanner back in. If your computer has usb 2.0 ports only, you (and I hate to suggest this, but) may need to buy a usb 1.1 card and run this scanner that way. I know, I know, don't ask: it sounds crazy to me, too, but my Brother HL-1440 USB 1.1 printer wouldn't run when plugged into the usb 2.0 port. Go Figure!

I know, I know, that shouldn't resolve the problem. It should be a software tweak, but I'm telling you what I did and that's all I know.

I see that the Sane.org website shows support for this scanner as good.

Here is a link to some archived forum stuff about Microtek's goods:

[http://ubuntuforums.org/archive/index.php/t-647334.html](http://ubuntuforums.org/archive/index.php/t-647334.html)

I hope it will help.

Also, open a terminal and type

lsusb

post the output of that here.

Also, (I know I'm getting long winded here):

[http://fixunix.com/ubuntu/342591-scanner-access-problems.html](http://fixunix.com/ubuntu/342591-scanner-access-problems.html)

and follow the post.

---

### Post by alienexplorers on 2008-05-17
The 1.0.19 driver is bad.  If you revert to the libsane-sm3840.so.1.0.15 driver everything will work OK.

---

