---
title: "USN-851-1: Elinks vulnerabilities"
date: 2009-10-21
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-10-21
Referenced CVEs: 
                                       CVE-2006-5925, CVE-2008-7224        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-851-1           October 21, 2009 elinks vulnerabilities CVE-2006-5925, CVE-2008-7224 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   elinks                          0.10.6-1ubuntu3.4   elinks-lite                     0.10.6-1ubuntu3.4  After a standard system upgrade you need to restart Elinks to effect the necessary changes.  Details follow:  Teemu Salmela discovered that Elinks did not properly validate input when processing smb:// URLs. If a user were tricked into viewing a malicious website and had smbclient installed, a remote attacker could execute arbitrary code with the privileges of the user invoking the program. (CVE-2006-5925)  Jakub Wilk discovered a logic error in Elinks, leading to a buffer overflow. If a user were tricked into viewing a malicious website, a remote attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-7224) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/USN-851-1)

---

