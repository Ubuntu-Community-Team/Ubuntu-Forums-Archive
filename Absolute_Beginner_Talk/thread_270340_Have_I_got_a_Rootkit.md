---
title: "Have I got a Rootkit ??"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Healey on 2006-10-03
Hi

I have just run chkrootkit and I seem to get no errors However Is I run 

chkrootkit -q

I get This :

The following suspicious files and directories were found:
/usr/lib/jvm/.java-gcj.jinfo
/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/.systemPrefs
/usr/lib/jvm/.java-1.5.0-sun.jinfo
/lib/modules/2.6.15-27-k7/volatile/.mounted

eth0: PACKET SNIFFER(/sbin/dhclient3[3399])

This command gives no errors
rkhunter --checkall --skip-keypress

So my question is do I have a problem ????

If so what can I do  ????

I am using Dapper


Regards

Healey

---

### Post by hw-tph on 2006-10-03
No, I do not think you have a problem. These are the common false positives on a Debian/Ubuntu system.

dhclient3 and wpasupplicant (which I always get listed as a suspicious sniffer programs) are both sniffers in a harmless way. The other mentioned files are suspect because the filenames begin with a dot so that they are hidden. Normally you would only want hidden files in users' home directories.


Håkan

---

### Post by Healey on 2006-10-03
Hi

Thankyou very much for reply

You have put my mind at rest

Best Regards

Healey

---

### Post by nudnik on 2006-10-03
> **hw-tph said:**
> No, I do not think you have a problem. These are the common false positives on a Debian/Ubuntu system.

dhclient3 and wpasupplicant (which I always get listed as a suspicious sniffer programs) are both sniffers in a harmless way. The other mentioned files are suspect because the filenames begin with a dot so that they are hidden. Normally you would only want hidden files in users' home directories.


Håkan

I'm getting something similar, details listed below. As you can see there are files in addition to the ones posted by the previous poster. 

They appear to be the same type of thing; are they, or do I have reason for concern?

The following suspicious files and directories were found:
/usr/lib/firefox/.autoreg
/usr/lib/jvm/.java-gcj.jinfo
/lib/modules/2.6.17-10-386/volatile/.mounted

/usr/lib/security
/usr/lib/security/classpath.security
eth0: PACKET SNIFFER(/sbin/dhclient3[3406])

---

