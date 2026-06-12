---
title: "USN-685-1: Net-SNMP vulnerabilities"
date: 2008-12-03
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-12-03
Referenced CVEs: 
CVE-2008-0960, CVE-2008-2292, CVE-2008-4309


Description: 
 =========================================================== Ubuntu Security Notice USN-685-1          December 03, 2008 net-snmp vulnerabilities CVE-2008-0960, CVE-2008-2292, CVE-2008-4309 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libsnmp-perl                    5.2.1.2-4ubuntu2.3   libsnmp9                        5.2.1.2-4ubuntu2.3  Ubuntu 7.10:   libsnmp-perl                    5.3.1-6ubuntu2.2   libsnmp10                       5.3.1-6ubuntu2.2  Ubuntu 8.04 LTS:   libsnmp-perl                    5.4.1~dfsg-4ubuntu4.2   libsnmp15                       5.4.1~dfsg-4ubuntu4.2  Ubuntu 8.10:   libsnmp15                       5.4.1~dfsg-7.1ubuntu6.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Wes Hardaker discovered that the SNMP service did not correctly validate HMAC authentication requests.  An unauthenticated remote attacker could send specially crafted SNMPv3 traffic with a valid username and gain access to the user's views without a valid authentication passphrase. (CVE-2008-0960)  John Kortink discovered that the Net-SNMP Perl module did not correctly check the size of returned values.  If a user or automated system were tricked into querying a malicious SNMP server, the application using the Perl module could be made to crash, leading to a denial of service. This did not affect Ubuntu 8.10. (CVE-2008-2292)  It was discovered that the SNMP service did not correctly handle large GETBULK requests.  If an unauthenticated remote attacker sent a specially crafted request, the SNMP service could be made to crash, leading to a denial of service. (CVE-2008-4309) 





[More...](http://www.ubuntu.com/usn/usn-685-1)

---

