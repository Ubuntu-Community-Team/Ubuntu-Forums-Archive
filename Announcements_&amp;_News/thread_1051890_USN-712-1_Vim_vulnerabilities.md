---
title: "USN-712-1: Vim vulnerabilities"
date: 2009-01-27
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-01-27
Referenced CVEs: 
CVE-2008-2712, CVE-2008-4101


Description: 
=========================================================== Ubuntu Security Notice USN-712-1           January 27, 2009 vim vulnerabilities CVE-2008-2712, CVE-2008-4101 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   vim                             1:6.4-006+2ubuntu6.2   vim-runtime                     1:6.4-006+2ubuntu6.2  Ubuntu 7.10:   vim                             1:7.1-056+2ubuntu2.1   vim-runtime                     1:7.1-056+2ubuntu2.1  Ubuntu 8.04 LTS:   vim                             1:7.1-138+1ubuntu3.1   vim-runtime                     1:7.1-138+1ubuntu3.1  Ubuntu 8.10:   vim                             1:7.1.314-3ubuntu3.1   vim-runtime                     1:7.1.314-3ubuntu3.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Jan Minar discovered that Vim did not properly sanitize inputs before invoking the execute or system functions inside Vim scripts. If a user were tricked into running Vim scripts with a specially crafted input, an attacker could execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-2712)  Ben Schmidt discovered that Vim did not properly escape characters when performing keyword or tag lookups. If a user were tricked into running specially crafted commands, an attacker could execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-4101)





[More...](http://www.ubuntu.com/usn/USN-712-1)

---

