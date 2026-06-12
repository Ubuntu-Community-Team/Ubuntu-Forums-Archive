---
title: "USN-792-1: OpenSSL vulnerabilities"
date: 2009-06-25
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-25
Referenced CVEs: 
                                       CVE-2009-1377, CVE-2009-1378, CVE-2009-1379, CVE-2009-1386, CVE-2009-1387        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-792-1              June 25, 2009 openssl vulnerabilities CVE-2009-1377, CVE-2009-1378, CVE-2009-1379, CVE-2009-1386, CVE-2009-1387 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libssl0.9.8                     0.9.8a-7ubuntu0.9  Ubuntu 8.04 LTS:   libssl0.9.8                     0.9.8g-4ubuntu3.7  Ubuntu 8.10:   libssl0.9.8                     0.9.8g-10.1ubuntu2.4  Ubuntu 9.04:   libssl0.9.8                     0.9.8g-15ubuntu3.2  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  It was discovered that OpenSSL did not limit the number of DTLS records it would buffer when they arrived with a future epoch. A remote attacker could cause a denial of service via memory resource consumption by sending a large number of crafted requests. (CVE-2009-1377)  It was discovered that OpenSSL did not properly free memory when processing DTLS fragments. A remote attacker could cause a denial of service via memory resource consumption by sending a large number of crafted requests. (CVE-2009-1378)  It was discovered that OpenSSL did not properly handle certain server certificates when processing DTLS packets. A remote DTLS server could cause a denial of service by sending a message containing a specially crafted server certificate. (CVE-2009-1379)  It was discovered that OpenSSL did not properly handle a DTLS ChangeCipherSpec packet when it occured before ClientHello. A remote attacker could cause a denial of service by sending a specially crafted request. (CVE-2009-1386)  It was discovered that OpenSSL did not properly handle out of sequence DTLS handshake messages. A remote attacker could cause a denial of service by sending a specially crafted request. (CVE-2009-1387)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-792-1)

---

