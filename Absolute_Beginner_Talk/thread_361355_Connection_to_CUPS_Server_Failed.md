---
title: "Connection to CUPS Server Failed"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by ZimmtheElder on 2007-02-14
First post from a rank amatuer...but learning.  I've set up my Ubuntu Dapper to network with my widnows XP desktop machine, and after some fiddling, each can now see the other.  My problem is with printing.  I can see the printers on the XP, but when I enter the Systems Settings (KDE 3.5.5) I get the following error:

Connection to CUPS Server failed.  Check that the CUPS server is correctly installed and running.  Error: the IPP request failed for an unknown reason.

I've uninstalled and reinstalled CUPS, stopped and restarted it, and I can't get rid of the error.  Curiously enough, I set the system up originally last weekend and it printed without a problem.  Then I had the bright idea of upgrading to Edgy.  After reinstalling Dapper (reformatting the hard drive) I can't get rid of this error.

---

### Post by kebes on 2007-02-14
Open a web-browser and go to this location:

[http://localhost:631/](http://localhost:631/)

This should bring you to the CUPS web-admin page. Here you can try re-adding your printer, check its status, bring it back online, etc.


Sometimes this web-interface works better than using the control panel applets, for fixing strange problems. Hope that helps.

Also, you can double-check that CUPS is running by using the command:
pgrep cups -l
(If it returns nothing, then CUPS isn't loaded!)

---

### Post by ZimmtheElder on 2007-02-14
Thanks for the suggestions, but no dice...pgrep shows that it's running.  On the web interface I have printcap and printing both set to CUPS.  I'm wondering what to do with that IPP message?  Could that be important?

---

### Post by kebes on 2007-02-14
Unfortunately that "IPP request failed" is a very generic error that doesn't help much. (Or at least it's never helped me.)

Did you try re-creating the printer (from scratch) using the web-admin?

I'm no expert, but I got a very similar error message once, and the fix was to use the web-interface to delete the printer, and create a new one.



If I understand correctly, you're trying to access a printer over the network (the printer is physically connected to a Windows XP box?). Did you install any firewall rules or app (e.g. firestarter) that may be interfering?

---

### Post by ZimmtheElder on 2007-02-14
Thanks, Kebes...yes, you understand the configuration correctly.  Curiously enough, I was able to fool around with enuff parameters that it finally worked.  I ignored the IPP error and went in as Guest, and the scan worked.  After hooking up my "GatewayPrinter" the system renamed it to GaaatwyPrintrrrrr"...go figure.  When I printed, I got the CUPS Printing System not available error, but it printed.

I'm declaring success and retiring from the field of battle.

---

