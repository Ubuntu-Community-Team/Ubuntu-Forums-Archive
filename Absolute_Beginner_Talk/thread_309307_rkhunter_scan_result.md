---
title: "rkhunter scan result"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-29
I used rkhunter (on Dapper) to scan my computer. All is fine. It did however inform me that the ownership configuration for a certain file could be improved:

```
* Application version scan
gpg: WARNING: unsafe ownership on configuration file `/home/me/.gnupg/gpg.conf'
   - GnuPG 1.4.2.2                                            [ OK ]
   - OpenSSL 0.9.8a   
```

Question1: How do I check the current ownership configuration for this file?
Question2: To what should I change it and how?

Also, it spat this out:

```
* Filesystem checks
   Checking /dev for suspicious files...                      [ OK ]
   Scanning for hidden files...                               [ Warning! ]
---------------
 /dev/.static
/dev/.udev
/dev/.initramfs
/dev/.initramfs-tools /etc/.pwd.lock
/etc/.java
---------------
Please inspect:  /dev/.static (directory)  /dev/.udev (directory)  /dev/.initram fs (directory)  /etc/.java (directory)

```

Question: Is this something I need to be worried about? I am assuming not since in the results it says this:

```
---------------------------- Scan results ----------------------------

MD5
MD5 compared: 0
Incorrect MD5 checksums: 0

File scan
Scanned files: 342
Possible infected files: 0

Application scan
Vulnerable applications: 0

Scanning took 191 seconds

-----------------------------------------------------------------------

```

Thank you in advance.

---

### Post by dwblas on 2006-11-29
All of the warnings are probably because root owns the dirs or files.  For /dev/*, I think this is necessary, but for /etc/.java and the /home dir files, you should change the owner to a regular user.  Key in 'man chown', or your file manager/file-browser might have a gui for chown.  I use mc, and use it's gui.

---

