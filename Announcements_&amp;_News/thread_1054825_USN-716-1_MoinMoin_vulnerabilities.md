---
title: "USN-716-1: MoinMoin vulnerabilities"
date: 2009-01-30
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-01-30
Referenced CVEs: 
CVE-2008-0780, CVE-2008-0781, CVE-2008-0782, CVE-2008-1098, CVE-2008-1099, CVE-2009-0260, CVE-2009-0312


Description: 
 =========================================================== Ubuntu Security Notice USN-716-1           January 30, 2009 moin vulnerabilities CVE-2008-0780, CVE-2008-0781, CVE-2008-0782, CVE-2008-1098, CVE-2008-1099, CVE-2009-0260, CVE-2009-0312 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   python2.4-moinmoin              1.5.2-1ubuntu2.4  Ubuntu 7.10:   python-moinmoin                 1.5.7-3ubuntu2.1  Ubuntu 8.04 LTS:   python-moinmoin                 1.5.8-5.1ubuntu2.2  Ubuntu 8.10:   python-moinmoin                 1.7.1-1ubuntu1.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  Fernando Quintero discovered than MoinMoin did not properly sanitize its input when processing login requests, resulting in cross-site scripting (XSS) vulnerabilities. With cross-site scripting vulnerabilities, if a user were tricked into viewing server output during a crafted server request, a remote attacker could exploit this to modify the contents, or steal confidential data, within the same domain. This issue affected Ubuntu 7.10 and 8.04 LTS. (CVE-2008-0780)  Fernando Quintero discovered that MoinMoin did not properly sanitize its input when attaching files, resulting in cross-site scripting vulnerabilities. This issue affected Ubuntu 6.06 LTS, 7.10 and 8.04 LTS. (CVE-2008-0781)  It was discovered that MoinMoin did not properly sanitize its input when processing user forms. A remote attacker could submit crafted cookie values and overwrite arbitrary files via directory traversal. This issue affected Ubuntu 6.06 LTS, 7.10 and 8.04 LTS. (CVE-2008-0782)  It was discovered that MoinMoin did not properly sanitize its input when editing pages, resulting in cross-site scripting vulnerabilities. This issue only affected Ubuntu 6.06 LTS and 7.10. (CVE-2008-1098)  It was discovered that MoinMoin did not properly enforce access controls, which could allow a remoter attacker to view private pages. This issue only affected Ubuntu 6.06 LTS and 7.10. (CVE-2008-1099)  It was discovered that MoinMoin did not properly sanitize its input when attaching files and using the rename parameter, resulting in cross-site scripting vulnerabilities. (CVE-2009-0260)  It was discovered that MoinMoin did not properly sanitize its input when displaying error messages after processing spam, resulting in cross-site scripting vulnerabilities. (CVE-2009-0312) 





[More...](http://www.ubuntu.com/usn/usn-716-1)

---

