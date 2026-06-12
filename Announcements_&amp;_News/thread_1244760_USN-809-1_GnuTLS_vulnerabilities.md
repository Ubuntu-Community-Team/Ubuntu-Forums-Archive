---
title: "USN-809-1: GnuTLS vulnerabilities"
date: 2009-08-19
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-08-19
Referenced CVEs: 
                                       CVE-2009-2409, CVE-2009-2730        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-809-1            August 19, 2009 gnutls12, gnutls13, gnutls26 vulnerabilities CVE-2009-2409, CVE-2009-2730, [https://launchpad.net/bugs/305264](https://launchpad.net/bugs/305264) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libgnutls12                     1.2.9-2ubuntu1.7  Ubuntu 8.04 LTS:   libgnutls13                     2.0.4-1ubuntu2.6  Ubuntu 8.10:   libgnutls26                     2.4.1-1ubuntu0.4  Ubuntu 9.04:   libgnutls26                     2.4.2-6ubuntu0.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Moxie Marlinspike and Dan Kaminsky independently discovered that GnuTLS did not properly handle certificates with NULL characters in the certificate name. An attacker could exploit this to perform a man in the middle attack to view sensitive information or alter encrypted communications. (CVE-2009-2730)  Dan Kaminsky discovered GnuTLS would still accept certificates with MD2 hash signatures. As a result, an attacker could potentially create a malicious trusted certificate to impersonate another site. This issue only affected Ubuntu 6.06 LTS and Ubuntu 8.10. (CVE-2009-2409)  USN-678-1 fixed a vulnerability and USN-678-2 a regression in GnuTLS. The  upstream patches introduced a regression when validating certain certificate  chains that would report valid certificates as untrusted. This update  fixes the problem, and only affected Ubuntu 6.06 LTS and Ubuntu 8.10 (Ubuntu  8.04 LTS and 9.04 were fixed at an earlier date). In an effort to maintain a  strong security stance and address all known regressions, this update  deprecates X.509 validation chains using MD2 and MD5 signatures. To accomodate  sites which must still use a deprected RSA-MD5 certificate, GnuTLS has been  updated to stop looking when it has found a trusted intermediary certificate.  This new handling of intermediary certificates is in accordance with other SSL  implementations.  Original advisory details:   Martin von Gagern discovered that GnuTLS did not properly verify  certificate chains when the last certificate in the chain was self-signed.  If a remote attacker were able to perform a man-in-the-middle attack, this  flaw could be exploited to view sensitive information. (CVE-2008-4989) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-809-1)

---

