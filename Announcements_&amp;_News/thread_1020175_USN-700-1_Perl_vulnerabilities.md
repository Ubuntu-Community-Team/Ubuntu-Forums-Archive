---
title: "USN-700-1: Perl vulnerabilities"
date: 2008-12-23
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-12-23
Referenced CVEs: 
CVE-2007-4829, CVE-2008-1927, CVE-2008-5302, CVE-2008-5303


Description: 
 =========================================================== Ubuntu Security Notice USN-700-1          December 24, 2008 libarchive-tar-perl, perl vulnerabilities CVE-2007-4829, CVE-2008-1927, CVE-2008-5302, CVE-2008-5303 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libarchive-tar-perl             1.26-2ubuntu0.1   libperl5.8                      5.8.7-10ubuntu1.2  Ubuntu 7.10:   libarchive-tar-perl             1.31-1ubuntu0.1   libperl5.8                      5.8.8-7ubuntu3.4   perl-modules                    5.8.8-7ubuntu3.4  Ubuntu 8.04 LTS:   libarchive-tar-perl             1.36-1ubuntu0.1   libperl5.8                      5.8.8-12ubuntu0.3   perl-modules                    5.8.8-12ubuntu0.3  Ubuntu 8.10:   perl-modules                    5.10.0-11.1ubuntu2.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Jonathan Smith discovered that the Archive::Tar Perl module did not correctly handle symlinks when extracting archives.  If a user or automated system were tricked into opening a specially crafted tar file, a remote attacker could over-write arbitrary files.  (CVE-2007-4829)  Tavis Ormandy and Will Drewry discovered that Perl did not correctly handle certain utf8 characters in regular expressions.  If a user or automated system were tricked into using a specially crafted expression, a remote attacker could crash the application, leading to a denial of service.  Ubuntu 8.10 was not affected by this issue.  (CVE-2008-1927)  A race condition was discovered in the File::Path Perl module's rmtree function.  If a local attacker successfully raced another user's call of rmtree, they could create arbitrary setuid binaries.  Ubuntu 6.06 and 8.10 were not affected by this issue.  (CVE-2008-5302)  A race condition was discovered in the File::Path Perl module's rmtree function.  If a local attacker successfully raced another user's call of rmtree, they could delete arbitrary files.  Ubuntu 6.06 was not affected by this issue.  (CVE-2008-5303) 





[More...](http://www.ubuntu.com/usn/usn-700-1)

---

