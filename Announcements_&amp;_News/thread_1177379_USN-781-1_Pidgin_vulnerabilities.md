---
title: "USN-781-1: Pidgin vulnerabilities"
date: 2009-06-03
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-03
Referenced CVEs: 
                                    CVE-2009-1373, CVE-2009-1374, CVE-2009-1375, CVE-2009-1376        
        

      Description: 
                                    ===========================================================Ubuntu Security Notice USN-781-1              June 03, 2009pidgin vulnerabilitiesCVE-2009-1373, CVE-2009-1374, CVE-2009-1375, CVE-2009-1376===========================================================A security issue affects the following Ubuntu releases:Ubuntu 8.04 LTSUbuntu 8.10Ubuntu 9.04This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 8.04 LTS:  pidgin                          1:2.4.1-1ubuntu2.4Ubuntu 8.10:  pidgin                          1:2.5.2-0ubuntu1.2Ubuntu 9.04:  pidgin                          1:2.5.5-1ubuntu8.1After a standard system upgrade you need to restart Pidgin to effectthe necessary changes.Details follow:It was discovered that Pidgin did not properly handle certain malformedmessages when sending a file using the XMPP protocol handler. If a userwere tricked into sending a file, a remote attacker could send a speciallycrafted response and cause Pidgin to crash, or possibly execute arbitrarycode with user privileges. (CVE-2009-1373)It was discovered that Pidgin did not properly handle certain malformedmessages in the QQ protocol handler. A remote attacker could send aspecially crafted message and cause Pidgin to crash. This issue onlyaffected Ubuntu 8.10 and 9.04. (CVE-2009-1374)It was discovered that Pidgin did not properly handle certain malformedmessages in the XMPP and Sametime protocol handlers. A remote attackercould send a specially crafted message and cause Pidgin to crash.(CVE-2009-1375)It was discovered that Pidgin did not properly handle certain malformedmessages in the MSN protocol handler. A remote attacker could send aspecially crafted message and possibly execute arbitrary code with userprivileges. (CVE-2009-1376)
        
        



[More...](http://www.ubuntu.com/usn/USN-781-1)

---

