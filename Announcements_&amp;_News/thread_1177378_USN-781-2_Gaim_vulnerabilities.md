---
title: "USN-781-2: Gaim vulnerabilities"
date: 2009-06-03
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-03
Referenced CVEs: 
                                    CVE-2009-1373, CVE-2009-1376        
        

      Description: 
                                    ===========================================================Ubuntu Security Notice USN-781-2              June 03, 2009gaim vulnerabilitiesCVE-2009-1373, CVE-2009-1376===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSThis advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  gaim                            1:1.5.0+1.5.1cvs20051015-1ubuntu10.2After a standard system upgrade you need to restart Gaim to effectthe necessary changes.Details follow:It was discovered that Gaim did not properly handle certain malformedmessages when sending a file using the XMPP protocol handler. If a userwere tricked into sending a file, a remote attacker could send a speciallycrafted response and cause Gaim to crash, or possibly execute arbitrarycode with user privileges. (CVE-2009-1373)It was discovered that Gaim did not properly handle certain malformedmessages in the MSN protocol handler. A remote attacker could send aspecially crafted message and possibly execute arbitrary code with userprivileges. (CVE-2009-1376)
        
        



[More...](http://www.ubuntu.com/usn/USN-781-2)

---

