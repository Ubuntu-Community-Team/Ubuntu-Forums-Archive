---
title: "USN-758-1: udev vulnerabilities"
date: 2009-04-15
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-04-15
Referenced CVEs: 
                                       CVE-2009-1185, CVE-2009-1186        
         
 
        Description: 
                                        =========================================================== Ubuntu Security Notice USN-758-1             April 15, 2009 udev vulnerabilities CVE-2009-1185, CVE-2009-1186 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   udev                            079-0ubuntu35.1  Ubuntu 7.10:   udev                            113-0ubuntu17.2  Ubuntu 8.04 LTS:   udev                            117-8ubuntu0.2  Ubuntu 8.10:   udev                            124-9ubuntu0.2  After a standard system upgrade you need to reboot your computer to effect the necessary changes.  Details follow:  Sebastian Krahmer discovered that udev did not correctly validate netlink message senders.  A local attacker could send specially crafted messages to udev in order to gain root privileges. (CVE-2009-1185)  Sebastian Krahmer discovered a buffer overflow in the path encoding routines in udev.  A local attacker could exploit this to crash udev, leading to a denial of service. (CVE-2009-1186) 
        
         
 
 

[More...](http://www.ubuntu.com/usn/usn-758-1)

---

