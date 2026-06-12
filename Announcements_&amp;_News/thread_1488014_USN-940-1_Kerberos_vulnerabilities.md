---
title: "USN-940-1: Kerberos vulnerabilities"
date: 2010-05-19
forum: Announcements &amp; News
---

### Post by rss-bot on 2010-05-19
Referenced CVEs: 
                                    CVE-2007-5902, CVE-2007-5971, CVE-2007-5972, CVE-2010-1320, CVE-2010-1321        
        

      Description: 
                                    ===========================================================Ubuntu Security Notice USN-940-1               May 19, 2010krb5 vulnerabilitiesCVE-2007-5902, CVE-2007-5971, CVE-2007-5972, CVE-2010-1320,CVE-2010-1321===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 8.04 LTSUbuntu 9.04Ubuntu 9.10This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  krb5-kdc                        1.4.3-5ubuntu0.11  libkrb53                        1.4.3-5ubuntu0.11Ubuntu 8.04 LTS:  krb5-admin-server               1.6.dfsg.3~beta1-2ubuntu1.5  krb5-kdc                        1.6.dfsg.3~beta1-2ubuntu1.5Ubuntu 9.04:  krb5-admin-server               1.6.dfsg.4~beta1-5ubuntu2.4  krb5-kdc                        1.6.dfsg.4~beta1-5ubuntu2.4Ubuntu 9.10:  krb5-admin-server               1.7dfsg~beta3-1ubuntu0.6  krb5-kdc                        1.7dfsg~beta3-1ubuntu0.6In general, a standard system update will make all the necessary changes.Details follow:It was discovered that Kerberos did not correctly free memory in theGSSAPI and kdb libraries. If a remote attacker were able to manipulatean application using these libraries carefully, the service couldcrash, leading to a denial of service. (Only Ubuntu 6.06 LTS wasaffected.) (CVE-2007-5902, CVE-2007-5971, CVE-2007-5972)Joel Johnson, Brian Almeida, and Shawn Emery discovered that Kerberosdid not correctly verify certain packet structures.  An unauthenticatedremote attacker could send specially crafted traffic to cause the KDC orkadmind services to crash, leading to a denial of service. (CVE-2010-1320,CVE-2010-1321)
        
        



[More...](http://www.ubuntu.com/usn/USN-940-1)

---

