---
title: "USN-632-1: Python vulnerabilities"
date: 2008-08-01
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-08-01
Referenced CVEs: 
CVE-2008-1679, CVE-2008-1721, CVE-2008-1887, CVE-2008-2315, CVE-2008-2316, CVE-2008-3142, CVE-2008-3143, CVE-2008-3144


Description: 
 ===========================================================  Ubuntu Security Notice USN-632-1            August 01, 2008 python2.4, python2.5 vulnerabilities CVE-2008-1679, CVE-2008-1721, CVE-2008-1887, CVE-2008-2315, CVE-2008-2316, CVE-2008-3142, CVE-2008-3143, CVE-2008-3144 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   python2.4                       2.4.3-0ubuntu6.2   python2.4-minimal               2.4.3-0ubuntu6.2  Ubuntu 7.04:   python2.4                       2.4.4-2ubuntu7.2   python2.4-minimal               2.4.4-2ubuntu7.2   python2.5                       2.5.1-0ubuntu1.2   python2.5-minimal               2.5.1-0ubuntu1.2  Ubuntu 7.10:   python2.4                       2.4.4-6ubuntu4.2   python2.4-minimal               2.4.4-6ubuntu4.2   python2.5                       2.5.1-5ubuntu5.2   python2.5-minimal               2.5.1-5ubuntu5.2  Ubuntu 8.04 LTS:   python2.4                       2.4.5-1ubuntu4.1   python2.4-minimal               2.4.5-1ubuntu4.1   python2.5                       2.5.2-2ubuntu4.1   python2.5-minimal               2.5.2-2ubuntu4.1  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  It was discovered that there were new integer overflows in the imageop module.  If an attacker were able to trick a Python application into processing a specially crafted image, they could execute arbitrary code with user privileges. (CVE-2008-1679)  Justin Ferguson discovered that the zlib module did not correctly handle certain archives.  If an attacker were able to trick a Python application into processing a specially crafted archive file, they could execute arbitrary code with user privileges. (CVE-2008-1721)  Justin Ferguson discovered that certain string manipulations in Python could be made to overflow.  If an attacker were able to pass a specially crafted string through the PyString_FromStringAndSize function, they could execute arbitrary code with user privileges. (CVE-2008-1887)  Multiple integer overflows were discovered in Python's core and modules including hashlib, binascii, pickle, md5, stringobject, unicodeobject, bufferobject, longobject, tupleobject, stropmodule, gcmodule, and mmapmodule.  If an attacker were able to exploit these flaws they could execute arbitrary code with user privileges or cause Python applications to crash, leading to a denial of service. (CVE-2008-2315, CVE-2008-2316, CVE-2008-3142, CVE-2008-3143, CVE-2008-3144). 





[More...](http://www.ubuntu.com/usn/usn-632-1)

---

