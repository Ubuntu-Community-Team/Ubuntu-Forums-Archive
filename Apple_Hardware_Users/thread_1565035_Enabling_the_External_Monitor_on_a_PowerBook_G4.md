---
title: "Enabling the External Monitor on a PowerBook G4"
date: 2010-08-31
forum: Apple Hardware Users
---

### Post by shawnhcorey on 2010-08-31
My video cable has gone completely flaky.  At times, it displays random snow on my screen.  I have an external monitor but its video chips has been turned off.  How do I turn it back on?

---

### Post by dngfng on 2010-08-31
Just had a quick brows according to this:

> 
**No external monitor on G4 iBook**

 Since  Ubuntu moved to xrandr, the external VGA-output is no longer properly  detected.  It is no longer possible to use Ubuntu with an external  monitor on an iBook. 
 [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

According to this its not supported any more - however I wouldn't bet any money on this being accurate information maybe some one else has first hand experience.

Also it might help if you posted some more information regarding the Ubuntu version you are using etc...

---

### Post by shawnhcorey on 2010-08-31
I don't have an iBook; I have a PowerBook.  They are different.

---

### Post by linuxopjemac on 2010-09-01
You have to fiddle around with your xorg.conf file.

Inspiration:
[http://mac.linux.be/content/xorgconf-powerbook-g4-alu-167ghz-and-external-monitor-0](http://mac.linux.be/content/xorgconf-powerbook-g4-alu-167ghz-and-external-monitor-0)

You have to make double entries for Device, Monitor and Screen sections.

If you succeed, please share it with us and tell us the computer you have and the monitor you are using.

---

