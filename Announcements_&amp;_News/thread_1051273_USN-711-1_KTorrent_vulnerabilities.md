---
title: "USN-711-1: KTorrent vulnerabilities"
date: 2009-01-26
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-01-26
Referenced CVEs: 
CVE-2008-5905, CVE-2008-5906


Description: 
=========================================================== Ubuntu Security Notice USN-711-1           January 26, 2009 ktorrent vulnerabilities CVE-2008-5905, CVE-2008-5906 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.10:   ktorrent                        2.2.1-0ubuntu3.1  Ubuntu 8.04 LTS:   ktorrent                        2.2.5-0ubuntu1.1  Ubuntu 8.10:   ktorrent                        3.1.2+dfsg.1-0ubuntu2.1  After a standard system upgrade you need to restart KTorrent to effect the necessary changes.  Details follow:  It was discovered that KTorrent did not properly restrict access when using the web interface plugin. A remote attacker could use a crafted http request and upload arbitrary torrent files to trigger the start of downloads and seeding. (CVE-2008-5905)  It was discovered that KTorrent did not properly handle certain parameters when using the web interface plugin. A remote attacker could use crafted http requests to execute arbitrary PHP code. (CVE-2008-5906)





[More...](http://www.ubuntu.com/usn/USN-711-1)

---

