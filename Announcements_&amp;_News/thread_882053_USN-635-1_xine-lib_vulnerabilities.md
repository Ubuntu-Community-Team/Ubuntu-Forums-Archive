---
title: "USN-635-1: xine-lib vulnerabilities"
date: 2008-08-06
forum: Announcements &amp; News
---

### Post by rss-bot on 2008-08-06
Referenced CVEs: 
CVE-2008-0073, CVE-2008-0225, CVE-2008-0238, CVE-2008-0486, CVE-2008-1110, CVE-2008-1161, CVE-2008-1482, CVE-2008-1686, CVE-2008-1878


Description: 
 ===========================================================  Ubuntu Security Notice USN-635-1            August 06, 2008 xine-lib vulnerabilities CVE-2008-0073, CVE-2008-0225, CVE-2008-0238, CVE-2008-0486, CVE-2008-1110, CVE-2008-1161, CVE-2008-1482, CVE-2008-1686, CVE-2008-1878 ===========================================================  A security issue affects the following Ubuntu releases:  Ubuntu 6.06 LTS Ubuntu 7.04 Ubuntu 7.10 Ubuntu 8.04 LTS  This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu.  The problem can be corrected by upgrading your system to the following package versions:  Ubuntu 6.06 LTS:   libxine-dev                     1.1.1+ubuntu2-7.9   libxine-main1                   1.1.1+ubuntu2-7.9  Ubuntu 7.04:   libxine-main1                   1.1.4-2ubuntu3.1  Ubuntu 7.10:   libxine1                        1.1.7-1ubuntu1.3  Ubuntu 8.04 LTS:   libxine1                        1.1.11.1-1ubuntu3.1  After a standard system upgrade you need to restart applications linked against xine-lib to effect the necessary changes.  Details follow:  Alin Rad Pop discovered an array index vulnerability in the SDP parser. If a user or automated system were tricked into opening a malicious RTSP stream, a remote attacker may be able to execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-0073)  Luigi Auriemma discovered that xine-lib did not properly check buffer sizes in the RTSP header-handling code. If xine-lib opened an RTSP stream with crafted SDP attributes, a remote attacker may be able to execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-0225, CVE-2008-0238)  Damian Frizza and Alfredo Ortega discovered that xine-lib did not properly validate FLAC tags. If a user or automated system were tricked into opening a crafted FLAC file, a remote attacker may be able to execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-0486)  It was discovered that the ASF demuxer in xine-lib did not properly check the length if the ASF header. If a user or automated system were tricked into opening a crafted ASF file, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-1110)  It was discovered that the Matroska demuxer in xine-lib did not properly verify frame sizes. If xine-lib opened a crafted ASF file, a remote attacker could cause a denial of service or possibly execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-1161)  Luigi Auriemma discovered multiple integer overflows in xine-lib. If a user or automated system were tricked into opening a crafted FLV, MOV, RM, MVE, MKV or CAK file, a remote attacker may be able to execute arbitrary code with the privileges of the user invoking the program. (CVE-2008-1482)  It was discovered that xine-lib did not properly validate its input when processing Speex file headers. If a user or automated system were tricked into opening a specially crafted Speex file, an attacker could create a denial of service or possibly execute arbitrary code as the user invoking the program. (CVE-2008-1686)  Guido Landi discovered a stack-based buffer overflow in xine-lib when processing NSF files. If xine-lib opened a specially crafted NSF file with a long NSF title, an attacker could create a denial of service or possibly execute arbitrary code as the user invoking the program. (CVE-2008-1878) 





[More...](http://www.ubuntu.com/usn/usn-635-1)

---

