---
title: "USN-651-1: Ruby vulnerabilities"
date: 2008-10-09
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-10-09
Referenced CVEs: 
CVE-2008-2376, CVE-2008-3443, CVE-2008-3655, CVE-2008-3656, CVE-2008-3657, CVE-2008-3790, CVE-2008-3905


Description: 
 =========================================================== Ubuntu Security Notice USN-651-1           October 10, 2008 ruby1.8 vulnerabilities CVE-2008-2376, CVE-2008-3443, CVE-2008-3655, CVE-2008-3656, CVE-2008-3657, CVE-2008-3790, CVE-2008-3905 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libruby1.8                      1.8.4-1ubuntu1.6   ruby1.8                         1.8.4-1ubuntu1.6  Ubuntu 7.04:   libruby1.8                      1.8.5-4ubuntu2.3   ruby1.8                         1.8.5-4ubuntu2.3  Ubuntu 7.10:   libruby1.8                      1.8.6.36-1ubuntu3.3   ruby1.8                         1.8.6.36-1ubuntu3.3  Ubuntu 8.04 LTS:   libruby1.8                      1.8.6.111-2ubuntu1.2   ruby1.8                         1.8.6.111-2ubuntu1.2  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Akira Tagoh discovered a vulnerability in Ruby which lead to an integer overflow. If a user or automated system were tricked into running a malicious script, an attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-2376)  Laurent Gaffie discovered that Ruby did not properly check for memory allocation failures. If a user or automated system were tricked into running a malicious script, an attacker could cause a denial of service. (CVE-2008-3443)  Keita Yamaguchi discovered several safe level vulnerabilities in Ruby. An attacker could use this to bypass intended access restrictions. (CVE-2008-3655)  Keita Yamaguchi discovered that WEBrick in Ruby did not properly validate paths ending with ".". A remote attacker could send a crafted HTTP request and cause a denial of service. (CVE-2008-3656)  Keita Yamaguchi discovered that the dl module in Ruby did not check the taintness of inputs. An attacker could exploit this vulnerability to bypass safe levels and execute dangerous functions. (CVE-2008-3657)  Luka Treiber and Mitja Kolsek discovered that REXML in Ruby did not always use expansion limits when processing XML documents. If a user or automated system were tricked into open a crafted XML file, an attacker could cause a denial of service via CPU consumption. (CVE-2008-3790)  Jan Lieskovsky discovered several flaws in the name resolver of Ruby. A remote attacker could exploit this to spoof DNS entries, which could lead to misdirected traffic. This is a different vulnerability from CVE-2008-1447. (CVE-2008-3790) 





[More...](http://www.ubuntu.com/usn/usn-651-1)

---

