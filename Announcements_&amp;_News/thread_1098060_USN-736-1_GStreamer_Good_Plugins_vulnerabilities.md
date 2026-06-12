---
title: "USN-736-1: GStreamer Good Plugins vulnerabilities"
date: 2009-03-16
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-03-16
Referenced CVEs: 
CVE-2009-0386, CVE-2009-0387, CVE-2009-0397


Description: 
=========================================================== Ubuntu Security Notice USN-736-1             March 16, 2009 gst-plugins-good0.10 vulnerabilities CVE-2009-0386, CVE-2009-0387, CVE-2009-0397 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 7.10 Ubuntu 8.04 LTS Ubuntu 8.10  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 7.10:   gstreamer0.10-plugins-good      0.10.6-0ubuntu4.2  Ubuntu 8.04 LTS:   gstreamer0.10-plugins-good      0.10.7-3ubuntu0.2  Ubuntu 8.10:   gstreamer0.10-plugins-good      0.10.10.4-1ubuntu1.1  In general, a standard system upgrade is sufficient to effect the necessary changes.  Details follow:  It was discovered that GStreamer Good Plugins did not correctly handle malformed Composition Time To Sample (ctts) atom data in Quicktime (mov) movie files. If a user were tricked into opening a crafted mov file, an attacker could execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-0386)  It was discovered that GStreamer Good Plugins did not correctly handle malformed Sync Sample (aka stss) atom data in Quicktime (mov) movie files. If a user were tricked into opening a crafted mov file, an attacker could cause a denial of service via application crash, or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-0387)  It was discovered that GStreamer Good Plugins did not correctly handle malformed Time-to-sample (aka stts) atom data in Quicktime (mov) movie files. If a user were tricked into opening a crafted mov file, an attacker could execute arbitrary code with the privileges of the user invoking the program. (CVE-2009-0397)





[More...](http://www.ubuntu.com/usn/USN-736-1)

---

