---
title: "USN-744-1: LittleCMS vulnerabilities"
date: 2009-03-23
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-23
Referenced CVEs: 
CVE-2009-0581, CVE-2009-0723, CVE-2009-0733


Description: 
=========================================================== Ubuntu Security Notice USN-744-1             March 23, 2009 lcms vulnerabilities CVE-2009-0581, CVE-2009-0723, CVE-2009-0733 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   liblcms1                        1.13-1ubuntu0.2  Ubuntu 7.10:   liblcms1                        1.16-5ubuntu3.2   python-liblcms                  1.16-5ubuntu3.2  Ubuntu 8.04 LTS:   liblcms1                        1.16-7ubuntu1.2   python-liblcms                  1.16-7ubuntu1.2  Ubuntu 8.10:   liblcms1                        1.16-10ubuntu0.2   python-liblcms                  1.16-10ubuntu0.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Chris Evans discovered that LittleCMS did not properly handle certain error conditions, resulting in a large memory leak. If a user or automated system were tricked into processing an image with malicious ICC tags, a remote attacker could cause a denial of service. (CVE-2009-0581)  Chris Evans discovered that LittleCMS contained multiple integer overflows. If a user or automated system were tricked into processing an image with malicious ICC tags, a remote attacker could crash applications linked against liblcms1, leading to a denial of service, or possibly execute arbitrary code with user privileges. (CVE-2009-0723)  Chris Evans discovered that LittleCMS did not properly perform bounds checking, leading to a buffer overflow. If a user or automated system were tricked into processing an image with malicious ICC tags, a remote attacker could execute arbitrary code with user privileges. (CVE-2009-0733)





[More...](http://www.ubuntu.com/usn/USN-744-1)

---

