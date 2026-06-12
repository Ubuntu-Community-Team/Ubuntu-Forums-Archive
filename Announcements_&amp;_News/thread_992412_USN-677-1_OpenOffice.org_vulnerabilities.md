---
title: "USN-677-1: OpenOffice.org vulnerabilities"
date: 2008-11-24
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-11-24
Referenced CVEs: 
CVE-2008-2237 CVE-2008-2238 CVE-2008-4937


Description: 
=========================================================== Ubuntu Security Notice USN-677-1          November 24, 2008 openoffice.org, openoffice.org-amd64 vulnerabilities CVE-2008-2237, CVE-2008-2238, CVE-2008-4937 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   openoffice.org-core             2.0.2-2ubuntu12.7-2  Ubuntu 7.10:   openoffice.org-core             1:2.3.0-1ubuntu5.5  Ubuntu 8.04 LTS:   openoffice.org-common           1:2.4.1-1ubuntu2.1   openoffice.org-core             1:2.4.1-1ubuntu2.1  Ubuntu 8.10:   openoffice.org-core             1:2.4.1-11ubuntu2.1  After a standard system upgrade you need to restart OpenOffice.org to effect the necessary changes.  Details follow:  Multiple memory overflow flaws were discovered in OpenOffice.org's handling of WMF and EMF files. If a user were tricked into opening a specially crafted document, a remote attacker might be able to execute arbitrary code with user privileges. (CVE-2008-2237, CVE-2008-2238)  Dmitry E. Oboukhov discovered that senddoc, as included in OpenOffice.org, created temporary files in an insecure way. Local users could exploit a race condition to create or overwrite files with the privileges of the user invoking the program. This issue only affected Ubuntu 8.04 LTS. (CVE-2008-4937) 





[More...](http://www.ubuntu.com/usn/usn-677-1)

---

