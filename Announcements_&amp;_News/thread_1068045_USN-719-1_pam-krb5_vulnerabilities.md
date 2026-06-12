---
title: "USN-719-1: pam-krb5 vulnerabilities"
date: 2009-02-12
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-02-12
Referenced CVEs: 
CVE-2009-0360, CVE-2009-0361


Description: 
=========================================================== Ubuntu Security Notice USN-719-1          February 12, 2009 libpam-krb5 vulnerabilities CVE-2009-0360, CVE-2009-0361 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   libpam-krb5                     3.10-1ubuntu0.8.04.1  Ubuntu 8.10:   libpam-krb5                     3.10-1ubuntu0.8.10.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that pam_krb5 parsed environment variables when run with setuid applications. A local attacker could exploit this flaw to bypass authentication checks and gain root privileges. (CVE-2009-0360)  Derek Chan discovered that pam_krb5 incorrectly handled refreshing existing credentials when used with setuid applications. A local attacker could exploit this to create or overwrite arbitrary files, and possibly gain root privileges. (CVE-2009-0361)





[More...](http://www.ubuntu.com/usn/USN-719-1)

---

