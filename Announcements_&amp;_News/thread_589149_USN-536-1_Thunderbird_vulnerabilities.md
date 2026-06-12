---
title: "USN-536-1: Thunderbird vulnerabilities"
date: 2007-10-23
forum: Announcements &amp; News
---

### Post by rss-bot on 2007-10-23
Referenced CVEs:
CVE-2006-2894, CVE-2007-1095, CVE-2007-2292, CVE-2007-3511, CVE-2007-5334, CVE-2007-5337, CVE-2007-5338, CVE-2007-5339, CVE-2007-5340


Description:
 ===========================================================  Ubuntu Security Notice USN-536-1           October 23, 2007 mozilla-thunderbird, thunderbird vulnerabilities CVE-2006-2894, CVE-2007-1095, CVE-2007-2292, CVE-2007-3511, CVE-2007-5334, CVE-2007-5337, CVE-2007-5338, CVE-2007-5339, CVE-2007-5340 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 6.10 Ubuntu 7.04 Ubuntu 7.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   mozilla-thunderbird             1.5.0.13+1.5.0.14b-0ubuntu0.6.06  Ubuntu 6.10:   mozilla-thunderbird             1.5.0.13+1.5.0.14b-0ubuntu0.6.10  Ubuntu 7.04:   mozilla-thunderbird             1.5.0.13+1.5.0.14b-0ubuntu0.7.04  Ubuntu 7.10:   mozilla-thunderbird             2.0.0.8~pre071022+nobinonly-0ubuntu0.7.10  After a standard system upgrade you need to restart Thunderbird to affect the necessary changes.  Details follow:  Various flaws were discovered in the layout and JavaScript engines. By tricking a user into opening a malicious web page, an attacker could execute arbitrary code with the user's privileges. (CVE-2007-5339, CVE-2007-5340)  Flaws were discovered in the file upload form control. By tricking a user into opening a malicious web page, an attacker could force arbitrary files from the user's computer to be uploaded without their consent. (CVE-2006-2894, CVE-2007-3511)  Michal Zalewski discovered that the onUnload event handlers were incorrectly able to access information outside the old page content. A malicious web site could exploit this to modify the contents, or steal confidential data (such as passwords), of the next loaded web page. (CVE-2007-1095)  Stefano Di Paola discovered that Thunderbird did not correctly request Digest Authentications. A malicious web site could exploit this to inject arbitrary HTTP headers or perform session splitting attacks against proxies. (CVE-2007-2292)  Eli Friedman discovered that XUL could be used to hide a window's titlebar. A malicious web site could exploit this to enhance their attempts at creating phishing web sites. (CVE-2007-5334)  Georgi Guninski discovered that Thunderbird would allow file-system based web pages to access additional files. By tricking a user into opening a malicious web page from a gnome-vfs location, an attacker could steal arbitrary files from the user's computer. (CVE-2007-5337)  It was discovered that the XPCNativeWrappers were not safe in certain situations. By tricking a user into opening a malicious web page, an attacker could run arbitrary JavaScript with the user's privileges. (CVE-2007-5338)  Please note that JavaScript is disabled by default for emails, and it is not recommended to enable it. 





[More...](http://www.ubuntu.com/usn/usn-536-1)

---

