---
title: "USN-674-1: HPLIP vulnerabilities"
date: 2008-11-19
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-11-19
Referenced CVEs: 
CVE-2008-2940, CVE-2008-2941


Description: 
=========================================================== Ubuntu Security Notice USN-674-1          November 19, 2008 hplip vulnerabilities CVE-2008-2940, CVE-2008-2941 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   hplip                           0.9.7-4ubuntu1.1  Ubuntu 7.10:   hplip                           2.7.7.dfsg.1-0ubuntu5.1  Ubuntu 8.04 LTS:   hplip                           2.8.2-0ubuntu8.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that the hpssd tool of hplip did not validate privileges in the alert-mailing function. A local attacker could exploit this to gain privileges and send e-mail messages from the account of the hplip user. This update alters hplip behaviour by preventing users from setting alerts and by moving alert configuration to a root-controlled /etc/hp/alerts.conf file. (CVE-2008-2940)  It was discovered that the hpssd tool of hplip did not correctly handle certain commands. A local attacker could use a specially crafted packet to crash hpssd, leading to a denial of service. (CVE-2008-2941)





[More...](http://www.ubuntu.com/usn/USN-674-1)

---

