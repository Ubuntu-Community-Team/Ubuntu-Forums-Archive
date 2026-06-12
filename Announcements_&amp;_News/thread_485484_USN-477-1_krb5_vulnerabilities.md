---
title: "USN-477-1: krb5 vulnerabilities"
date: 2007-06-26
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-06-26
Referenced CVEs:
CVE-2007-2442, CVE-2007-2443, CVE-2007-2798


Description:
 ===========================================================  Ubuntu Security Notice USN-477-1              June 26, 2007 krb5 vulnerabilities CVE-2007-2442, CVE-2007-2443, CVE-2007-2798 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libkadm55                                1.4.3-5ubuntu0.4  Ubuntu 6.10:   libkadm55                                1.4.3-9ubuntu1.3  Ubuntu 7.04:   libkadm55                                1.4.4-5ubuntu3.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Wei Wang discovered that the krb5 RPC library did not correctly handle certain error conditions.  A remote attacker could cause kadmind to free an uninitialized pointer, leading to a denial of service or possibly execution of arbitrary code with root privileges. (CVE-2007-2442)  Wei Wang discovered that the krb5 RPC library did not correctly check the size of certain communications.  A remote attacker could send a specially crafted request to kadmind and execute arbitrary code with root privileges. (CVE-2007-2443)  It was discovered that the kadmind service could be made to overflow its stack.  A remote attacker could send a specially crafted request and execute arbitrary code with root privileges. (CVE-2007-2798) 





[More...](http://www.ubuntu.com/usn/usn-477-1)

---

