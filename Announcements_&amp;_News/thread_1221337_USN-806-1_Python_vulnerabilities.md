---
title: "USN-806-1: Python vulnerabilities"
date: 2009-07-23
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-07-23
Referenced CVEs: 
                                       CVE-2008-4864, CVE-2008-5031        
         
 
        Description: 
                                       =========================================================== Ubuntu Security Notice USN-806-1              July 23, 2009 python2.4, python2.5 vulnerabilities CVE-2008-4864, CVE-2008-5031 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   python2.4                       2.4.3-0ubuntu6.3   python2.4-minimal               2.4.3-0ubuntu6.3  Ubuntu 8.04 LTS:   python2.4                       2.4.5-1ubuntu4.2   python2.4-minimal               2.4.5-1ubuntu4.2   python2.5                       2.5.2-2ubuntu6   python2.5-minimal               2.5.2-2ubuntu6  Ubuntu 8.10:   python2.4                       2.4.5-5ubuntu1.1   python2.4-minimal               2.4.5-5ubuntu1.1  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  It was discovered that Python incorrectly handled certain arguments in the imageop module. If an attacker were able to pass specially crafted arguments through the crop function, they could execute arbitrary code with user privileges. For Python 2.5, this issue only affected Ubuntu 8.04 LTS. (CVE-2008-4864)  Multiple integer overflows were discovered in Python's stringobject and unicodeobject expandtabs method. If an attacker were able to exploit these flaws they could execute arbitrary code with user privileges or cause Python applications to crash, leading to a denial of service. (CVE-2008-5031)
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-806-1)

---

