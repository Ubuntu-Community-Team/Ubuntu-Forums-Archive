---
title: "USN-675-1: Pidgin vulnerabilities"
date: 2008-11-24
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-11-24
Referenced CVEs: 
CVE-2008-2927, CVE-2008-2955, CVE-2008-2957, CVE-2008-3532


Description: 
=========================================================== Ubuntu Security Notice USN-675-1          November 24, 2008 pidgin vulnerabilities CVE-2008-2927, CVE-2008-2955, CVE-2008-2957, CVE-2008-3532 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.10:   pidgin                          1:2.2.1-1ubuntu4.3  Ubuntu 8.04 LTS:   pidgin                          1:2.4.1-1ubuntu2.2  After a standard system upgrade you need to restart Pidgin to effect the necessary changes.  Details follow:  It was discovered that Pidgin did not properly handle certain malformed messages in the MSN protocol handler. A remote attacker could send a specially crafted message and possibly execute arbitrary code with user privileges. (CVE-2008-2927)  It was discovered that Pidgin did not properly handle file transfers containing a long filename and special characters in the MSN protocol handler. A remote attacker could send a specially crafted filename in a file transfer request and cause Pidgin to crash, leading to a denial of service. (CVE-2008-2955)  It was discovered that Pidgin did not impose resource limitations in the UPnP service. A remote attacker could cause Pidgin to download arbitrary files  and cause a denial of service from memory or disk space exhaustion. (CVE-2008-2957)  It was discovered that Pidgin did not validate SSL certificates when using a secure connection. If a remote attacker were able to perform a man-in-the-middle attack, this flaw could be exploited to view sensitive information. This update alters Pidgin behaviour by asking users to confirm the validity of a certificate upon initial login. (CVE-2008-3532)





[More...](http://www.ubuntu.com/usn/USN-675-1)

---

