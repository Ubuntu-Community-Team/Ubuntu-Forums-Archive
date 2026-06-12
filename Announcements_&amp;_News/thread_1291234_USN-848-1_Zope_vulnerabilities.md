---
title: "USN-848-1: Zope vulnerabilities"
date: 2009-10-14
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-10-14
Referenced CVEs: 
                                    CVE-2009-0668, CVE-2009-0669        
        

      Description: 
                                    ===========================================================Ubuntu Security Notice USN-848-1           October 14, 2009zope3 vulnerabilitiesCVE-2009-0668, CVE-2009-0669===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 8.04 LTSUbuntu 8.10Ubuntu 9.04This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  zope3                           3.2.1-1ubuntu1.2Ubuntu 8.04 LTS:  zope3                           3.3.1-5ubuntu2.2Ubuntu 8.10:  zope3                           3.3.1-7ubuntu0.2Ubuntu 9.04:  zope3                           3.4.0-0ubuntu3.3In general, a standard system upgrade is sufficient to effect thenecessary changes.Details follow:It was discovered that the Zope Object Database (ZODB) database server(ZEO) improperly filtered certain commands when a database is shared amongmultiple applications or application instances. A remote attacker couldsend malicious commands to the server and execute arbitrary code.(CVE-2009-0668)It was discovered that the Zope Object Database (ZODB) database server(ZEO) did not handle authentication properly when a database is sharedamong multiple applications or application instances. A remote attackercould use this flaw to bypass security restrictions. (CVE-2009-0669)It was discovered that Zope did not limit the number of new object ids aclient could request. A remote attacker could use this flaw to consume ahuge amount of resources, leading to a denial of service. (No CVEidentifier)
        
        



[More...](http://www.ubuntu.com/usn/USN-848-1)

---

