---
title: "Ubuntu Security Notice USN-770-1"
date: 2009-05-04
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-05-04
Referenced CVEs: 
                                    USN-770-1: ClamAV vulnerability        
        

      Description: 
                                    ===========================================================                      Ubuntu Security Notice USN-770-1               May 04, 2009clamav vulnerability                                                   [https://launchpad.net/bugs/365823](https://launchpad.net/bugs/365823)                   ===========================================================                                                                  A security issue affects the following Ubuntu releases:                                                                       Ubuntu 9.04                                                                                                                                         This advisory also applies to the corresponding versions of                                                         Kubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 9.04:  clamav-milter                   0.95.1+dfsg-1ubuntu1.2In general, a standard system upgrade is sufficient to effect thenecessary changes.Details follow:A flaw was discovered in the clamav-milter initscript which caused theownership of the current working directory to be changed to the 'clamav'user. This update attempts to repair the incorrect ownership for standardsystem directories, but it is recommended that the following command beperformed to report any other directories that may be affected:  $ sudo find -H / -type d -user clamav \! -group clamav 2>/dev/nullSystems configured to run clamav as a user other than the default 'clamav'user will need to adjust the above command accordingly.
        
        



[More...](http://www.ubuntu.com/usn/USN-770-1)

---

