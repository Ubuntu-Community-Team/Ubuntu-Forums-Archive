---
title: "USN-700-2: Perl regression"
date: 2009-01-15
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-01-15
Description: 
 =========================================================== Ubuntu Security Notice USN-700-2           January 15, 2009 perl regression [https://launchpad.net/bugs/315991](https://launchpad.net/bugs/315991) ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   perl                            5.8.8-12ubuntu0.4  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  USN-700-1 fixed vulnerabilities in Perl.  Due to problems with the Ubuntu 8.04 build, some Perl .ph files were missing from the resulting update. This update fixes the problem.  We apologize for the inconvenience.  Original advisory details:   Jonathan Smith discovered that the Archive::Tar Perl module did not  correctly handle symlinks when extracting archives.  If a user or  automated system were tricked into opening a specially crafted tar file,  a remote attacker could over-write arbitrary files.  (CVE-2007-4829)    Tavis Ormandy and Will Drewry discovered that Perl did not correctly  handle certain utf8 characters in regular expressions.  If a user or  automated system were tricked into using a specially crafted expression,  a remote attacker could crash the application, leading to a denial  of service.  Ubuntu 8.10 was not affected by this issue.  (CVE-2008-1927)    A race condition was discovered in the File::Path Perl module's rmtree  function.  If a local attacker successfully raced another user's call  of rmtree, they could create arbitrary setuid binaries.  Ubuntu 6.06  and 8.10 were not affected by this issue.  (CVE-2008-5302)    A race condition was discovered in the File::Path Perl module's rmtree  function.  If a local attacker successfully raced another user's call of  rmtree, they could delete arbitrary files.  Ubuntu 6.06 was not affected  by this issue.  (CVE-2008-5303) 





[More...](http://www.ubuntu.com/usn/usn-700-2)

---

