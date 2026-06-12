---
title: "USN-576-1: Firefox vulnerabilities"
date: 2008-02-08
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-02-08
Referenced CVEs:
CVE-2008-0412, CVE-2008-0413, CVE-2008-0414, CVE-2008-0415, CVE-2008-0416, CVE-2008-0417, CVE-2008-0418, CVE-2008-0419, CVE-2008-0420, CVE-2008-0591, CVE-2008-0592, CVE-2008-0593, CVE-2008-0594


Description:
 ===========================================================  Ubuntu Security Notice USN-576-1          February 08, 2008 firefox vulnerabilities CVE-2008-0412, CVE-2008-0413, CVE-2008-0414, CVE-2008-0415, CVE-2008-0416, CVE-2008-0417, CVE-2008-0418, CVE-2008-0419, CVE-2008-0420, CVE-2008-0591, CVE-2008-0592, CVE-2008-0593, CVE-2008-0594 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   firefox                         1.5.dfsg+1.5.0.15~prepatch080202a-0ubuntu1  Ubuntu 6.10:   firefox                         2.0.0.12+0nobinonly+2-0ubuntu0.6.10  Ubuntu 7.04:   firefox                         2.0.0.12+1nobinonly+2-0ubuntu0.7.4  Ubuntu 7.10:   firefox                         2.0.0.12+2nobinonly+2-0ubuntu0.7.10  After a standard system upgrade you need to restart firefox to effect the necessary changes.  Details follow:  Various flaws were discovered in the browser and JavaScript engine. By tricking a user into opening a malicious web page, an attacker could execute arbitrary code with the user's privileges. (CVE-2008-0412, CVE-2008-0413)  Flaws were discovered in the file upload form control. A malicious website could force arbitrary files from the user's computer to be uploaded without consent. (CVE-2008-0414)  Various flaws were discovered in the JavaScript engine. By tricking a user into opening a malicious web page, an attacker could escalate privileges within the browser, perform cross-site scripting attacks and/or execute arbitrary code with the user's privileges. (CVE-2008-0415)  Various flaws were discovered in character encoding handling. If a user were ticked into opening a malicious web page, an attacker could perform cross-site scripting attacks. (CVE-2008-0416)  Justin Dolske discovered a flaw in the password saving mechanism. By tricking a user into opening a malicious web page, an attacker could corrupt the user's stored passwords. (CVE-2008-0417)  Gerry Eisenhaur discovered that the chrome URI scheme did not properly guard against directory traversal. Under certain circumstances, an attacker may be able to load files or steal session data. Ubuntu is not vulnerable in the default installation. (CVE-2008-0418)  David Bloom discovered flaws in the way images are treated by the browser. A malicious website could exploit this to steal the user's history information, crash the browser and/or possibly execute arbitrary code with the user's privileges. (CVE-2008-0419)  Flaws were discovered in the BMP decoder. By tricking a user into opening a specially crafted BMP file, an attacker could obtain sensitive information. (CVE-2008-0420)  Michal Zalewski discovered flaws with timer-enabled security dialogs. A malicious website could force the user to confirm a security dialog without explicit consent. (CVE-2008-0591)  It was discovered that Firefox mishandled locally saved plain text files. By tricking a user into saving a specially crafted text file, an attacker could prevent the browser from displaying local files with a .txt extension. (CVE-2008-0592)  Martin Straka discovered flaws in stylesheet handling after a 302 redirect. By tricking a user into opening a malicious web page, an attacker could obtain sensitive URL parameters. (CVE-2008-0593)  Emil Ljungdahl and Lars-Olof Moilanen discovered that a web forgery warning dialog wasn't displayed under certain circumstances. A malicious website could exploit this to conduct phishing attacks against the user. (CVE-2008-0594) 





[More...](http://www.ubuntu.com/usn/usn-576-1)

---

