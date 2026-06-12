---
title: "Corrupted admin password file(s)"
date: 2013-11-11
forum: Any Other OS
---

### Post by bcschmerker on 2013-11-11
On 10 November 2013, my Asus® CM1630-06 as upgraded, running Microsoft® Windows® 7.0.8001 (MultiProcessor Kernel 6.1.7601), hit a snag:  It failed to accept the password I had reserved for an Administrator account.  (The Standard User account this system is unaffected for programs not requiring Superuser priveleges.)  Resetting a password in Ubuntu® 12.04.4-LTS can be accomplished by booting into single-user mode from GRUB, but Windows® has no such option.  What software can best accomplish a password reset on an admin account in the absence of a Password Recovery Disc (USB) or equivalent remote service?

---

### Post by bcschmerker on 2013-11-16
**Update:**  The recommended procedure not working as advertised in [Offline NT Password and Registry Editor]("http://pogostick.net/~pnh/ntpasswd/"), I had to temporarily promote my Standard User account to affect the changes required, then demote it once the regular Admin account was fixed.  Quirky, Microsoft® Windows® 6-up can be.  Just someting to watch for in the event one of our Ubuntu® community runs into a similar issue as a result of Registry issues uninstalling no-longer-needed software. ):P

***Caveat venditor!***  Be advised that, under certain conditions, emergency measures such as described this Thread can cause Registry issues in Microsoft® Windows® 6-up, most likely with the SAM and Security hives which carry the data for User Accounts, Local Groups, &c.  As of 16 December 2013, I am researching the problem of System Error 87 attempting C:\Windows\System32\Net.exe localgroup administrators - all other Local Groups read OK.

---

