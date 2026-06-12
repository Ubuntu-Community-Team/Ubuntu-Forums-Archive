---
title: "USN-835-1: neon vulnerabilities"
date: 2009-09-21
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-09-21
Referenced CVEs: 
                                    CVE-2008-3746, CVE-2009-2474        
        

      Description: 
                                    ===========================================================Ubuntu Security Notice USN-835-1         September 21, 2009neon, neon27 vulnerabilitiesCVE-2008-3746, CVE-2009-2474===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 8.04 LTSUbuntu 8.10Ubuntu 9.04This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  libneon25                       0.25.5.dfsg-5ubuntu0.1Ubuntu 8.04 LTS:  libneon27                       0.27.2-1ubuntu0.1  libneon27-gnutls                0.27.2-1ubuntu0.1Ubuntu 8.10:  libneon27                       0.28.2-2ubuntu0.1  libneon27-gnutls                0.28.2-2ubuntu0.1Ubuntu 9.04:  libneon27                       0.28.2-6.1ubuntu0.1  libneon27-gnutls                0.28.2-6.1ubuntu0.1In general, a standard system upgrade is sufficient to effect thenecessary changes.Details follow:Joe Orton discovered that neon did not correctly handle SSL certificateswith zero bytes in the Common Name.  A remote attacker could exploit thisto perform a man in the middle attack to view sensitive information oralter encrypted communications.
        
        



[More...](http://www.ubuntu.com/usn/usn-835-1)

---

