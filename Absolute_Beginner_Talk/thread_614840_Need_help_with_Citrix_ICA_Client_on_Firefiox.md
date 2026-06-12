---
title: "Need help with Citrix ICA Client on Firefiox"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by brooks.maxwell on 2007-11-16
This might actually be help with security certificates, but it all starts with Citrix.  It took quite a while to figure out how to get Citrix ICAClient up and running on my computer but I did.  Anyway, Now that I have the Citrix ICA Client installed and working, when I try to connect to one of the published apps through Citrix, I get an error saying that I have not chosen to trust the security certificate.  It doesn't give me the option of trusting, and i can't find where I need to go to overwrite it.  Can anyone help?

---

### Post by infurnus on 2007-11-17
[http://ubuntuforums.org/showthread.php?t=376735&page=8](http://ubuntuforums.org/showthread.php?t=376735&page=8)

I have the same problem still have not found a solution. I've tried iin wine i can make it farther but my apps hang too bad and wine crashes.

my error was:
"The Citrix ICA client version installed from this workstation does not meet minimum requirements for security and support. Please report this non-compliancy to your local technical support to upgrade your system with ICA client 10.0 or later"

---

### Post by uberweber on 2008-01-06
Thank God for Google!  I was having the exact same problem after installing the CITRIX ICA client. After poking around I found a solution at the Stanford Linear Accelerator CITRIX support page:

[URL="http://www2.slac.stanford.edu/computing/windows/services/citrix/faq_xp.htm#Error:%20not%20proper%20encryption%20level%20to%20access%20session"]http://www2.slac.stanford.edu/computing/windows/services/citrix/faq_xp.htm#Error:%20not%20proper%20encryption%20level%20to%20access%20session
[/URL]

Basically, the CITRIX client has out of date certs so you need to download these 2 files:

[http://www2.slac.stanford.edu/computing/windows/services/citrix/downloads/thawte-server-ca.crt]("http://www2.slac.stanford.edu/computing/windows/services/citrix/downloads/thawte-server-ca.crt")

[http://www2.slac.stanford.edu/computing/windows/services/citrix/downloads/ThawteRoot.crt]("http://www2.slac.stanford.edu/computing/windows/services/citrix/downloads/ThawteRoot.crt")

and put them in:

~/ICAClient/linuxx866/keystore/cacert

BE CAREFUL, the path for your particular installation may not include 'linuxxx866' depending on your system architecture.  I hope I've provided enough information to reproduce my solution....and I really hope this helps you guys.  Ubuntu + forums rock!

---

