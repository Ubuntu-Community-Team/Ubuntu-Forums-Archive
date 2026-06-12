---
title: "Not authenticated update?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by harerama on 2006-09-10
Update icon appeared at the right top of the screen when I tried install update. It says.

Warning you are about to install software that can not be authenticated! Doing this could allow a malicious individual to damage or take control of your system.

libdvdcss2 is the software that will be updated

What's going on? 

Thanks

---

### Post by jorn on 2006-09-10
I'm not sure. Can it has something to do with restricted software that is't supportet by Ubuntu that you have downloaded in the first place and now beeing updated?

---

### Post by masnevets on 2006-09-10
That means you haven't added the GPG key for that repository. There should be instructions on how to do so at the website of said repository.

---

### Post by stig on 2006-09-10
> **harerama said:**
> Warning you are about to install software that can not be authenticated! Doing this could allow a malicious individual to damage or take control of your system.

I've got the same update warning but 8 files are listed and it does not include libdvdcss2.

They are: dnsutils, bind9-host, libisc11, libdns21, libisccc0, libisccfg1, libbind9-0, liblwres9

The only "unusual" software I have is Scribus. Is there a way to find out what application such updates refer to so I can be sure they are OK?

---

### Post by stig on 2006-09-11
I finally found the notice shown below on the Ubuntu security notices web page:
[http://www.ubuntu.com/usn/usn-343-1](http://www.ubuntu.com/usn/usn-343-1)
so I guessed it was OK to download the updates even though they were not authenticated.

But I still don't understand why a security update should be flagged up by my Ubuntu Dapper as "Warning you are about to install software that can not be authenticated! Doing this could allow a malicious individual to damage or take control of your system." It doesn't boost confidence! (And it does not seem to relate to any unusual software on my system.)

Ubuntu Security Notice USN-343-1         September 07, 2006
bind9 vulnerabilities
CVE-2006-4095, CVE-2006-4096
===========================================================

A security issue affects the following Ubuntu releases:

Ubuntu 5.04
Ubuntu 5.10
Ubuntu 6.06 LTS

This advisory also applies to the corresponding versions of
Kubuntu, Edubuntu, and Xubuntu.

The problem can be corrected by upgrading your system to the
following package versions:

Ubuntu 5.04:
  bind9                                    1:9.2.4-1ubuntu1.1

Ubuntu 5.10:
  bind9                                    1:9.3.1-2ubuntu1.1

Ubuntu 6.06 LTS:
  bind9                                    1:9.3.2-2ubuntu1.1

In general, a standard system upgrade is sufficient to effect the
necessary changes.

Details follow:

bind did not sufficiently verify particular requests and responses
from other name servers and users. By sending a specially crafted
packet, a remote attacker could exploit this to crash the name server.

---

