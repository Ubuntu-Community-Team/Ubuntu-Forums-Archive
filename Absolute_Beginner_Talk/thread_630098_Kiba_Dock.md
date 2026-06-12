---
title: "Kiba Dock"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by jordanae on 2007-12-03
When I go to install the Kiba Dock I put in the part of the code:

mkdir kiba-dock
cd kiba-dock
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/) kiba-dock
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/) kiba-plugins
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/) kiba-dbus-plugins

And I get this:

jordan@HP-Pavilion:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net...trunk/akamaru/](https://kibadock.svn.sourceforge.net...trunk/akamaru/) akamaru

Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
- The certificate is not issued by a trusted authority. Use the
fingerprint to validate the certificate manually!
Certificate information:
- Hostname: *.svn.sourceforge.net
- Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
- Issuer: Equifax Secure Certificate Authority, Equifax, US
- Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74 :36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))

How do I finish the installation?

---

### Post by Partyboi2 on 2007-12-03
The way I got around that was to (t)emporarily accept the Server certificate

---

