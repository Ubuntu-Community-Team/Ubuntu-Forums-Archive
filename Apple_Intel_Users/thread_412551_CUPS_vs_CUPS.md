---
title: "CUPS vs CUPS"
date: 2007-04-18
forum: Apple Intel Users
---

### Post by zigford on 2007-04-18
Hi Yall,

I'm a recent OSX/MAC convert but still use Ubuntu on my home PC's and Server.  I have an Ubuntu server with a HP PSC 1210 attached by usb.
Printer is shared as a http based ipp cups printer.  I can print to it from any Windows box, but am out of luck with osx

I know how to add the printer, ie: System Preferences-->Print Fax-->(Hold down option key)Click More Printers-->Select Advanced, http ipp-->http://ns:631/printers/HP_PSC_1210-->Generic

Now I can print documents and according to osx the document printed fine.  Also when I connect to the ubuntu cups web page, it says the document completed, but nothing comes out.

What gives? Winblows works.  Its making me sad.

Anyone come accross this and have a solution?

Thanks

---

### Post by zigford on 2007-04-18
bummp

---

### Post by zigford on 2007-04-18
Well, I fixed it.

For anyone having the same problem:

Turn browsing on in your cups server config:

> /etc/cups/cups.d/browse.conf
ServerName ns.jspeed.private
MaxLogSize 0
MaxJobs 10
BrowseProtocols cups
BrowseAddress @LOCAL
BrowseAllow from All
Browsing on


Good Luck

---

