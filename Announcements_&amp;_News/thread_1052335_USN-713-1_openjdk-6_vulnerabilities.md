---
title: "USN-713-1: openjdk-6 vulnerabilities"
date: 2009-01-27
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-01-27
Referenced CVEs: 
CVE-2008-5347, CVE-2008-5348, CVE-2008-5349, CVE-2008-5350, CVE-2008-5351, CVE-2008-5352, CVE-2008-5353, CVE-2008-5354, CVE-2008-5358, CVE-2008-5359, CVE-2008-5360


Description: 
 =========================================================== Ubuntu Security Notice USN-713-1           January 27, 2009 openjdk-6 vulnerabilities CVE-2008-5347, CVE-2008-5348, CVE-2008-5349, CVE-2008-5350, CVE-2008-5351, CVE-2008-5352, CVE-2008-5353, CVE-2008-5354, CVE-2008-5358, CVE-2008-5359, CVE-2008-5360 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.10:   icedtea6-plugin                 6b12-0ubuntu6.1   openjdk-6-jdk                   6b12-0ubuntu6.1   openjdk-6-jre                   6b12-0ubuntu6.1   openjdk-6-jre-headless          6b12-0ubuntu6.1   openjdk-6-jre-lib               6b12-0ubuntu6.1  After a standard system upgrade you need to restart any Java applications to effect the necessary changes.  Details follow:  It was discovered that Java did not correctly handle untrusted applets. If a user were tricked into running a malicious applet, a remote attacker could gain user privileges, or list directory contents. (CVE-2008-5347, CVE-2008-5350)  It was discovered that Kerberos authentication and RSA public key processing were not correctly handled in Java.  A remote attacker could exploit these flaws to cause a denial of service. (CVE-2008-5348, CVE-2008-5349)  It was discovered that Java accepted UTF-8 encodings that might be handled incorrectly by certain applications.  A remote attacker could bypass string filters, possible leading to other exploits. (CVE-2008-5351)  Overflows were discovered in Java JAR processing.  If a user or automated system were tricked into processing a malicious JAR file, a remote attacker could crash the application, leading to a denial of service. (CVE-2008-5352, CVE-2008-5354)  It was discovered that Java calendar objects were not unserialized safely. If a user or automated system were tricked into processing a specially crafted calendar object, a remote attacker could execute arbitrary code with user privileges. (CVE-2008-5353)  It was discovered that the Java image handling code could lead to memory corruption.  If a user or automated system were tricked into processing a specially crafted image, a remote attacker could crash the application, leading to a denial of service. (CVE-2008-5358, CVE-2008-5359)  It was discovered that temporary files created by Java had predictable names.  If a user or automated system were tricked into processing a specially crafted JAR file, a remote attacker could overwrite sensitive information.  (CVE-2008-5360) 





[More...](http://www.ubuntu.com/usn/usn-713-1)

---

