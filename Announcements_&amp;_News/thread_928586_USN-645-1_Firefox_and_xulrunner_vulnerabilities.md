---
title: "USN-645-1: Firefox and xulrunner vulnerabilities"
date: 2008-09-24
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-09-24
Referenced CVEs: 
CVE-2008-0016, CVE-2008-3835, CVE-2008-3836, CVE-2008-3837, CVE-2008-4058, CVE-2008-4059, CVE-2008-4060, CVE-2008-4061, CVE-2008-4062, CVE-2008-4063, CVE-2008-4064, CVE-2008-4065, CVE-2008-4066, CVE-2008-4067, CVE-2008-4068, CVE-2008-4069


Description: 
 ===========================================================  Ubuntu Security Notice USN-645-1         September 24, 2008 firefox, firefox-3.0, xulrunner-1.9 vulnerabilities CVE-2008-0016, CVE-2008-3835, CVE-2008-3836, CVE-2008-3837, CVE-2008-4058, CVE-2008-4059, CVE-2008-4060, CVE-2008-4061, CVE-2008-4062, CVE-2008-4063, CVE-2008-4064, CVE-2008-4065, CVE-2008-4066, CVE-2008-4067, CVE-2008-4068, CVE-2008-4069 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.04:   firefox                         2.0.0.17+0nobinonly-0ubuntu0.7.4  Ubuntu 7.10:   firefox                         2.0.0.17+1nobinonly-0ubuntu0.7.10  Ubuntu 8.04 LTS:   firefox-3.0                     3.0.2+build6+nobinonly-0ubuntu0.8.04.1   xulrunner-1.9                   1.9.0.2+build6+nobinonly-0ubuntu0.8.04.1  After a standard system upgrade you need to restart Firefox and any applications that use xulrunner, such as Epiphany, to effect the necessary changes.  Details follow:  Justin Schuh, Tom Cross and Peter Williams discovered errors in the Firefox URL parsing routines. If a user were tricked into opening a crafted hyperlink, an attacker could overflow a stack buffer and execute arbitrary code. (CVE-2008-0016)  It was discovered that the same-origin check in Firefox could be bypassed. If a user were tricked into opening a malicious website, an attacker may be able to execute JavaScript in the context of a different website. (CVE-2008-3835)  Several problems were discovered in the JavaScript engine. This could allow an attacker to execute scripts from page content with chrome privileges. (CVE-2008-3836)  Paul Nickerson discovered Firefox did not properly process mouse click events. If a user were tricked into opening a malicious web page, an attacker could move the content window, which could potentially be used to force a user to perform unintended drag and drop operations. (CVE-2008-3837)  Several problems were discovered in the browser engine. This could allow an attacker to execute code with chrome privileges. (CVE-2008-4058, CVE-2008-4059, CVE-2008-4060)  Drew Yao, David Maciejak and other Mozilla developers found several problems in the browser engine of Firefox. If a user were tricked into opening a malicious web page, an attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-4061, CVE-2008-4062, CVE-2008-4063, CVE-2008-4064)  Dave Reed discovered a flaw in the JavaScript parsing code when processing certain BOM characters. An attacker could exploit this to bypass script filters and perform cross-site scripting attacks. (CVE-2008-4065)  Gareth Heyes discovered a flaw in the HTML parser of Firefox. If a user were tricked into opening a malicious web page, an attacker could bypass script filtering and perform cross-site scripting attacks. (CVE-2008-4066)  Boris Zbarsky and Georgi Guninski independently discovered flaws in the resource: protocol. An attacker could exploit this to perform directory traversal, read information about the system, and prompt the user to save information in a file. (CVE-2008-4067, CVE-2008-4068)  Billy Hoffman discovered a problem in the XBM decoder. If a user were tricked into opening a malicious web page or XBM file, an attacker may be able to cause a denial of service via application crash. (CVE-2008-4069) 





[More...](http://www.ubuntu.com/usn/usn-645-1)

---

