---
title: "USN-937-1: TeX Live vulnerabilities"
date: 2010-05-06
forum: Announcements &amp; News
---

### Post by rss-bot on 2010-05-06
Referenced CVEs: 
                                    CVE-2009-1284, CVE-2010-0739, CVE-2010-0827, CVE-2010-1440        
        

      Description: 
                                    ===========================================================Ubuntu Security Notice USN-937-1               May 06, 2010texlive-bin vulnerabilitiesCVE-2009-1284, CVE-2010-0739, CVE-2010-0827, CVE-2010-1440===========================================================A security issue affects the following Ubuntu releases:Ubuntu 8.04 LTSUbuntu 9.04Ubuntu 9.10Ubuntu 10.04 LTSThis advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 8.04 LTS:  texlive-base-bin                2007.dfsg.1-2ubuntu0.1Ubuntu 9.04:  texlive-base-bin                2007.dfsg.2-4ubuntu2.1Ubuntu 9.10:  texlive-base-bin                2007.dfsg.2-7ubuntu1.1Ubuntu 10.04 LTS:  texlive-binaries                2009-5ubuntu0.1In general, a standard system update will make all the necessary changes.Details follow:It was discovered that TeX Live incorrectly handled certain long .bibbibliography files. If a user or automated system were tricked intoprocessing a specially crafted bib file, an attacker could cause a denialof service via application crash. This issue only affected Ubuntu 8.04 LTS,9.04 and 9.10. (CVE-2009-1284)Marc Schoenefeld, Karel Šrot and Ludwig Nussel discovered that TeX Liveincorrectly handled certain malformed dvi files. If a user or automatedsystem were tricked into processing a specially crafted dvi file, anattacker could cause a denial of service via application crash, or possiblyexecute arbitrary code with the privileges of the user invoking theprogram. (CVE-2010-0739, CVE-2010-1440)Dan Rosenberg discovered that TeX Live incorrectly handled certainmalformed dvi files. If a user or automated system were tricked intoprocessing a specially crafted dvi file, an attacker could cause a denialof service via application crash, or possibly execute arbitrary code withthe privileges of the user invoking the program. (CVE-2010-0827)
        
        



[More...](http://www.ubuntu.com/usn/USN-937-1)

---

