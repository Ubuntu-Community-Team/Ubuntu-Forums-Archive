---
title: "USN-490-1: Firefox vulnerabilities"
date: 2007-07-19
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-07-19
Referenced CVEs:
CVE-2007-3089, CVE-2007-3285, CVE-2007-3656, CVE-2007-3734, CVE-2007-3735, CVE-2007-3736, CVE-2007-3737, CVE-2007-3738


Description:
 ===========================================================  Ubuntu Security Notice USN-490-1              July 19, 2007 firefox vulnerabilities CVE-2007-3089, CVE-2007-3285, CVE-2007-3656, CVE-2007-3734, CVE-2007-3735, CVE-2007-3736, CVE-2007-3737, CVE-2007-3738 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   firefox                       1.5.dfsg+1.5.0.13~prepatch070716-0ubuntu1  Ubuntu 6.10:   firefox                       2.0.0.5+0dfsg-0ubuntu0.6.10  Ubuntu 7.04:   firefox                       2.0.0.5+1-0ubuntu1  After a standard system upgrade you need to restart Firefox to effect the necessary changes.  Details follow:  Various flaws were discovered in the layout and JavaScript engines. By tricking a user into opening a malicious web page, an attacker could execute arbitrary code with the user's privileges. (CVE-2007-3734, CVE-2007-3735)  Flaws were discovered in the JavaScript methods addEventListener and setTimeout which could be used to inject script into another site in violation of the browser's same-origin policy.  A malicious web site could exploit this to modify the contents, or steal confidential data (such as passwords), of other web pages. (CVE-2007-3736)  Ronen Zilberman and Michal Zalewski discovered timing attacks in the JavaScript engine's use of about:blank frames.  A malicious web site could exploit this to modify the contents, or steal confidential data (such as passwords), of other web pages. (CVE-2007-3089)  A flaw was discovered in the JavaScript event handling code.  By tricking a user into opening a malicious web page, an attacker could execute arbitrary code with the user's privileges. (CVE-2007-3737)  Ronald van den Heetkamp discovered that filename URLs including an encoded null byte could confuse the extension matching code.  By tricking a user into opening a malicious web page, an attacker could execute arbitrary helper programs. (CVE-2007-3285)  Michal Zalewski discovered flaws in the same-origin handling of cached "wyciwyg://" documents.  A malicious web site could exploit this to modify the contents, or steal confidential data (such as passwords), of other web pages. (CVE-2007-3656)  Various flaws were discovered in the XPCNativeWrapper method. By tricking a user into opening a malicious web page, an attacker could execute arbitrary code with the user's privileges. (CVE-2007-3738). 





[More...](http://www.ubuntu.com/usn/usn-490-1)

---

