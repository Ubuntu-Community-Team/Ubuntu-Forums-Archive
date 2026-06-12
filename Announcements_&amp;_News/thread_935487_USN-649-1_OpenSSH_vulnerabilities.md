---
title: "USN-649-1: OpenSSH vulnerabilities"
date: 2008-10-01
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-10-01
Referenced CVEs: 
CVE-2008-1657, CVE-2008-4109


Description: 
 =========================================================== Ubuntu Security Notice USN-649-1           October 01, 2008 openssh vulnerabilities CVE-2008-1657, CVE-2008-4109 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   openssh-server                  1:4.2p1-7ubuntu3.5  Ubuntu 7.04:   openssh-server                  1:4.3p2-8ubuntu1.5  Ubuntu 7.10:   openssh-server                  1:4.6p1-5ubuntu0.6  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that the ForceCommand directive could be bypassed. If a local user created a malicious ~/.ssh/rc file, they could execute arbitrary commands as their user id.  This only affected Ubuntu 7.10. (CVE-2008-1657)  USN-355-1 fixed vulnerabilities in OpenSSH.  It was discovered that the fixes for this issue were incomplete.  A remote attacker could attempt multiple logins, filling all available connection slots, leading to a denial of service.  This only affected Ubuntu 6.06 and 7.04. (CVE-2008-4109) 





[More...](http://www.ubuntu.com/usn/usn-649-1)

---

