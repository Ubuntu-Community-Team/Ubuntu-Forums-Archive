---
title: "Kiba dock on gutsy gibbon help"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by Fleece Flamingo on 2008-01-03
So, following this thread [here]("http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba") I am at step 3 ```
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/ akamaru
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/ kiba-dock
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/ kiba-plugins
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/ kiba-dbus-plugins
```

When I type that in I get this message to approve the certificate, I choose permanently and it fails

```
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/ akamaru
Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? p
svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted (https://kibadock.svn.sourceforge.net)

```

So what I want to know is how do I approve it? By the way I just installed Ubuntu today and I love it so any help is appreciated :)!

---

### Post by Fleece Flamingo on 2008-01-03
bump plz

---

