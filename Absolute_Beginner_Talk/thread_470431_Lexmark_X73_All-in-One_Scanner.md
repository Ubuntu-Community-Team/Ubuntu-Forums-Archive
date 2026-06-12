---
title: "Lexmark X73 All-in-One Scanner"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by finchair on 2007-06-11
After looking through the forums here I didn't find the answer to my question.  I was receiving an Failed to open gt68xx:libusb error when I tried to run the "Xsane Image Scanner"

How do I setup Ubuntu 7.04 (Feisty Fawn) to use the scanner on my Lexmark x73?

I found the answer at [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/) ( SANE GT68xx Backend Homepage)  This site has a lot of useful information for various scanners and good links to the firmware files for them.

1. Go to ->  [http://www.meier-geinitz.de/sane/gt68xx-backend/](http://www.meier-geinitz.de/sane/gt68xx-backend/)

2. Scroll down until you find the entry for the Vendor: Lexmark and Product X73

3.  Download the file "OSLO3071b2.usb"

4.  Place the file in the usr/local/share/sane/gt68xx/ or /usr/share/sane/gt68xx/ directory.  (I placed mine in /usr/share/sane/gt68xx/)

5.  Logout and log back into X.

Sane should see and be able to use your x73 scanner.

HTHs,
finchair :-)

---

### Post by southernman on 2007-06-12
Bump in the name of community spirit! 

Nice job, finchair! :)

---

### Post by MenZa on 2007-06-12
Ahh, great job. I suggest you add this article to the wiki: [http://help.ubuntu.com/community/](http://help.ubuntu.com/community/).

This requires a Launchpad account, but the chances that others will see it (and use it) are much greater there, than on this forum where posts are bumped down pretty much immediately.

---

### Post by domness on 2008-05-15
Aww cheers! I was just searching for help on this.. Working perfectly :)

---

