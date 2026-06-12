---
title: "USN-839-1: Samba vulnerabilities"
date: 2009-10-01
forum: Announcements &amp; News
---

### Post by rss-bot on 2009-10-01
Referenced CVEs: 
                                    CVE-2009-1886, CVE-2009-1888, CVE-2009-2813, CVE-2009-2906, CVE-2009-2948        
        

      Description: 
                                    ===========================================================Ubuntu Security Notice USN-839-1           October 01, 2009samba vulnerabilitiesCVE-2009-1886, CVE-2009-1888, CVE-2009-2813, CVE-2009-2906,CVE-2009-2948===========================================================A security issue affects the following Ubuntu releases:Ubuntu 6.06 LTSUbuntu 8.04 LTSUbuntu 8.10Ubuntu 9.04This advisory also applies to the corresponding versions ofKubuntu, Edubuntu, and Xubuntu.The problem can be corrected by upgrading your system to thefollowing package versions:Ubuntu 6.06 LTS:  samba                           3.0.22-1ubuntu3.9  smbfs                           3.0.22-1ubuntu3.9Ubuntu 8.04 LTS:  samba                           3.0.28a-1ubuntu4.9  smbfs                           3.0.28a-1ubuntu4.9Ubuntu 8.10:  samba                           2:3.2.3-1ubuntu3.6  smbclient                       2:3.2.3-1ubuntu3.6  smbfs                           2:3.2.3-1ubuntu3.6Ubuntu 9.04:  samba                           2:3.3.2-1ubuntu3.2  smbfs                           2:3.3.2-1ubuntu3.2In general, a standard system upgrade is sufficient to effect thenecessary changes.Details follow:J. David Hester discovered that Samba incorrectly handled users that lackhome directories when the automated [homes] share is enabled. Anauthenticated user could connect to that share name and gain access to thewhole filesystem. (CVE-2009-2813)Tim Prouty discovered that the smbd daemon in Samba incorrectly handledcertain unexpected network replies. A remote attacker could send maliciousreplies to the server and cause smbd to use all available CPU, leading to adenial of service. (CVE-2009-2906)Ronald Volgers discovered that the mount.cifs utility, when installed as asetuid program, would not verify user permissions before opening acredentials file. A local user could exploit this to use or read thecontents of unauthorized credential files. (CVE-2009-2948)Reinhard Nißl discovered that the smbclient utility contained format stringvulnerabilities in its file name handling. Because of security features inUbuntu, exploitation of this vulnerability is limited. If a user orautomated system were tricked into processing a specially crafted filename, smbclient could be made to crash, possibly leading to a denial ofservice. This only affected Ubuntu 8.10. (CVE-2009-1886)Jeremy Allison discovered that the smbd daemon in Samba incorrectly handledpermissions to modify access control lists when dos filemode is enabled. Aremote attacker could exploit this to modify access control lists. Thisonly affected Ubuntu 8.10 and Ubuntu 9.04. (CVE-2009-1886)
        
        



[More...](http://www.ubuntu.com/usn/USN-839-1)

---

