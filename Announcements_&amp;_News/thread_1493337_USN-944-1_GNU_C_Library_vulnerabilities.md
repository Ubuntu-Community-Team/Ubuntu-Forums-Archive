---
title: "USN-944-1: GNU C Library vulnerabilities"
date: 2010-05-25
forum: Announcements &amp; News
---

### Post by rss-bot on 2010-05-25
Referenced CVEs: 
                                       CVE-2008-1391, CVE-2010-0296, CVE-2010-0830        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-944-1               May 25, 2010 glibc, eglibc vulnerabilities CVE-2008-1391, CVE-2010-0296, CVE-2010-0830 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 9.04 Ubuntu 9.10 Ubuntu 10.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libc6                           2.3.6-0ubuntu20.6  Ubuntu 8.04 LTS:   libc6                           2.7-10ubuntu6  Ubuntu 9.04:   libc6                           2.9-4ubuntu6.2  Ubuntu 9.10:   libc6                           2.10.1-0ubuntu17  Ubuntu 10.04 LTS:   libc6                           2.11.1-0ubuntu7.1  After a standard system update you need to restart all services to make the necessary changes.  Details follow:  Maksymilian Arciemowicz discovered that the GNU C library did not correctly handle integer overflows in the strfmon function.  If a user or automated system were tricked into processing a specially crafted format string, a remote attacker could crash applications, leading to a denial of service. (Ubuntu 10.04 was not affected.) (CVE-2008-1391)  Jeff Layton and Dan Rosenberg discovered that the GNU C library did not correctly handle newlines in the mntent family of functions.  If a local attacker were able to inject newlines into a mount entry through other vulnerable mount helpers, they could disrupt the system or possibly gain root privileges. (CVE-2010-0296)  Dan Rosenberg discovered that the GNU C library did not correctly validate certain ELF program headers.  If a user or automated system were tricked into verifying a specially crafted ELF program, a remote attacker could execute arbitrary code with user privileges. (CVE-2010-0830) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-944-1)

---

