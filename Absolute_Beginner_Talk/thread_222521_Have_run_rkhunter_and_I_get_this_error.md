---
title: "Have run rkhunter and I get this error"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Healey on 2006-07-25
Hi

I am using breezy

I ran this command in a terminal and got this error 

rkhunter --checkall --skip-keypress


* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.static
/dev/.udevdb
/dev/.initramfs-tools /etc/.pwd.lock
---------------
Please inspect:  /dev/.static (directory)  /dev/.udevdb (directory)


Application advisories
* Application scan
   Checking Apache2 modules ...                               [ Not found ]
   Checking Apache configuration ...                          [ OK ]

* Application version scan
   - GnuPG 1.4.1                                              [ Old or patched v ersion ]
   - Procmail MTA 3.22                                        [ OK ]



Security advisories
* Check: Groups and Accounts
   Searching for /etc/passwd...                               [ Found ]
   Checking users with UID '0' (root)...                      [ OK ]

* Check: SSH
   Searching for sshd_config...

* Check: Events and Logging
   Search for syslog configuration...                         [ OK ]
   Checking for running syslog slave...                       [ OK ]
   Checking for logging to remote system...                   [ OK (no remote lo gging) ]


---------------------------- Scan results ----------------------------

MD5
MD5 compared: 0
Incorrect MD5 checksums: 0

File scan
Scanned files: 342
Possible infected files: 0

Application scan
Vulnerable applications: 1

Scanning took 96 seconds



What does this mean and do I need to worry ??

Best regards

Healey

---

### Post by rbalfour on 2006-07-25
> GnuPG 1.4.1 [ Old or patched v ersion ]
You need a newer version. But the rkhunter is based on installing things from the source or bleededge. So you're still okay.

> 
Scanning for hidden files... [ Warning! ]
---------------
/dev/.static
/dev/.udevdb
/dev/.initramfs-tools /etc/.pwd.lock
---------------
Please inspect: /dev/.static (directory) /dev/.udevdb (directory)

Nothing to worry about, once again bleeding edge. 

Best to watch the security update here on the forums.

---

### Post by Healey on 2006-07-25
Hi

Thanks very much for you reply

I feel a little bit better now thanks


Ref "GnuPG 1.4.1 [ Old or patched v ersion ]" Do I need to update this ??  If I do , how do I do it ?? and also what is it ??

Best Regards

Healey

---

