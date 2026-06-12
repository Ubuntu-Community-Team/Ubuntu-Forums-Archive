---
title: "USN-942-1: PostgreSQL vulnerabilities"
date: 2010-05-21
forum: Announcements &amp; News
---

### Post by rss-bot on 2010-05-21
Referenced CVEs: 
                                       CVE-2010-1169, CVE-2010-1170        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-942-1               May 21, 2010 postgresql-8.1, postgresql-8.3, postgresql-8.4 vulnerabilities CVE-2010-1169, CVE-2010-1170 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 9.04 Ubuntu 9.10 Ubuntu 10.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   postgresql-plperl-8.1           8.1.21-0ubuntu0.6.06   postgresql-pltcl-8.1            8.1.21-0ubuntu0.6.06  Ubuntu 8.04 LTS:   postgresql-plperl-8.3           8.3.11-0ubuntu8.04   postgresql-pltcl-8.3            8.3.11-0ubuntu8.04  Ubuntu 9.04:   postgresql-plperl-8.3           8.3.11-0ubuntu9.04   postgresql-pltcl-8.3            8.3.11-0ubuntu9.04  Ubuntu 9.10:   postgresql-plperl-8.4           8.4.4-0ubuntu9.10   postgresql-pltcl-8.4            8.4.4-0ubuntu9.10  Ubuntu 10.04 LTS:   postgresql-plperl-8.4           8.4.4-0ubuntu10.04   postgresql-pltcl-8.4            8.4.4-0ubuntu10.04  This update uses a new upstream release, which includes additional bug fixes. In general, a standard system update will make all the necessary changes.  Details follow:  It was discovered that the Safe.pm module as used by PostgreSQL did not properly restrict PL/perl procedures. If PostgreSQL was configured to use Perl stored procedures, a remote authenticated attacker could exploit this to execute arbitrary Perl code. (CVE-2010-1169)  It was discovered that PostgreSQL did not properly check permissions to restrict PL/Tcl procedures. If PostgreSQL was configured to use Tcl stored procedures, a remote authenticated attacker could exploit this to execute arbitrary Tcl code. (CVE-2010-1170) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-942-1)

---

