---
title: "USN-723-1: Git vulnerabilities"
date: 2009-02-18
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-02-18
Referenced CVEs: 
CVE-2008-3546, CVE-2008-5516, CVE-2008-5517, CVE-2008-5916


Description: 
===========================================================Ubuntu Security Notice USN-723-1          February 18, 2009git-core vulnerabilitiesCVE-2008-3546, CVE-2008-5516, CVE-2008-5517, CVE-2008-5916===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 7.10Ubuntu 8.04 LTSUbuntu 8.10This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  git-core                        1.1.3-1ubuntu1.1Ubuntu 7.10:  git-core                        1:1.5.2.5-2ubuntu0.1  gitweb                          1:1.5.2.5-2ubuntu0.1Ubuntu 8.04 LTS:  git-core                        1:1.5.4.3-1ubuntu2.1  gitweb                          1:1.5.4.3-1ubuntu2.1Ubuntu 8.10:  git-core                        1:1.5.6.3-1.1ubuntu2.1  gitweb                          1:1.5.6.3-1.1ubuntu2.1In general, a standard system upgrade is sufficient to effect thenecessary changes.Details follow:It was discovered that Git did not properly handle long file paths. If a userwere tricked into performing commands on a specially crafted Git repository, anattacker could possibly execute arbitrary code with the privileges of the userinvoking the program. (CVE-2008-3546)It was discovered that the Git web interface (gitweb) did not correctly handleshell metacharacters when processing certain commands. A remote attacker couldsend specially crafted commands to the Git server and execute arbitrary codewith the privileges of the Git web server. This issue only applied to Ubuntu7.10 and 8.04 LTS. (CVE-2008-5516, CVE-2008-5517)It was discovered that the Git web interface (gitweb) did not properly restrictthe diff.external configuration parameter. A local attacker could exploit thisissue and execute arbitrary code with the privileges of the Git web server.This issue only applied to Ubuntu 8.04 LTS and 8.10. (CVE-2008-5916)





[More...](http://www.ubuntu.com/usn/USN-723-1)

---

