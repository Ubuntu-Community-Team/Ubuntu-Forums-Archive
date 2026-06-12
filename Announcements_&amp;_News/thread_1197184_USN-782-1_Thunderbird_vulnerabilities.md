---
title: "USN-782-1: Thunderbird vulnerabilities"
date: 2009-06-25
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-06-25
Referenced CVEs: 
                                       CVE-2009-1303, CVE-2009-1305, CVE-2009-1306, CVE-2009-1307, CVE-2009-1308, CVE-2009-1309, CVE-2009-1392, CVE-2009-1833, CVE-2009-1836, CVE-2009-1838, CVE-2009-1841        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-782-1              June 25, 2009 thunderbird vulnerabilities CVE-2009-1303, CVE-2009-1305, CVE-2009-1306, CVE-2009-1307, CVE-2009-1308, CVE-2009-1309, CVE-2009-1392, CVE-2009-1833, CVE-2009-1836, CVE-2009-1838, CVE-2009-1841 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 8.04 LTS Ubuntu 8.10 Ubuntu 9.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 8.04 LTS:   thunderbird                     2.0.0.22+build1+nobinonly-0ubuntu0.8.04.1  Ubuntu 8.10:   thunderbird                     2.0.0.22+build1+nobinonly-0ubuntu0.8.10.1  Ubuntu 9.04:   thunderbird                     2.0.0.22+build1+nobinonly-0ubuntu0.9.04.1  After a standard system upgrade you need to restart Thunderbird to effect the necessary changes.  Details follow:  Several flaws were discovered in the JavaScript engine of Thunderbird. If a user had JavaScript enabled and were tricked into viewing malicious web content, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-1303, CVE-2009-1305, CVE-2009-1392, CVE-2009-1833, CVE-2009-1838)  Several flaws were discovered in the way Thunderbird processed malformed URI schemes. If a user were tricked into viewing a malicious website and had JavaScript and plugins enabled, a remote attacker could execute arbitrary JavaScript or steal private data. (CVE-2009-1306, CVE-2009-1307, CVE-2009-1309)  Cefn Hoile discovered Thunderbird did not adequately protect against embedded third-party stylesheets. If JavaScript were enabled, an attacker could exploit this to perform script injection attacks using XBL bindings. (CVE-2009-1308)  Shuo Chen, Ziqing Mao, Yi-Min Wang, and Ming Zhang discovered that Thunderbird did not properly handle error responses when connecting to a proxy server. If a user had JavaScript enabled while using Thunderbird to view websites and a remote attacker were able to perform a man-in-the-middle attack, this flaw could be exploited to view sensitive information. (CVE-2009-1836)  It was discovered that Thunderbird could be made to run scripts with elevated privileges. If a user had JavaScript enabled while having certain non-default add-ons installed and were tricked into viewing a malicious website, an attacker could cause a chrome privileged object, such as the browser sidebar, to run arbitrary code via interactions with the attacker controlled website. (CVE-2009-1841) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-782-1)

---

