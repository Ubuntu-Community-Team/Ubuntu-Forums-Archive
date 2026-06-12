---
title: "Verifying cygwin download: setup.exe"
date: 2011-06-03
forum: Any Other OS
---

### Post by john_spiral on 2011-06-03
Hi,

Can anyone shed some light on how to authenticate a download (setup.exe) from a site ([http://www.cygwin.com/install.html](http://www.cygwin.com/install.html)) that offers both a signature for a file (setup.exe.sig) and a  PGP public key.

I tried the below tutorial from Nicraft:

[http://www.cyberciti.biz/tips/howto-verify-integrity-of-the-tar-balls-with-gpg-command.html](http://www.cyberciti.biz/tips/howto-verify-integrity-of-the-tar-balls-with-gpg-command.html)

But it resulted in the below failure:

[mb@mike ~]$ gpg --verify pubring.asc setup.exe
gpg: verify signatures failed: unexpected data

I followed the below sequence:

gpg pubring.asc

spat out:

pub  1024D/676041BA 2008-06-13 Cygwin <cygwin@cygwin.com>
sub  1024g/A1DB7B5C 2008-06-13

then I tried the below:

gpg --keyserver pgpkeys.mit.edu --recv-key 676041BA

gpg: requesting key 676041BA from hkp server pgpkeys.mit.edu
gpg: key 676041BA: "Cygwin <cygwin@cygwin.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

then 

gpg --fingerprint 676041BA

pub   1024D/676041BA 2008-06-13
      Key fingerprint = 1169 DF9F 2273 4F74 3AA5  9232 A9A2 62FF 6760 41BA
uid                  Cygwin <cygwin@cygwin.com>
sub   1024g/A1DB7B5C 2008-06-13

then

gpg --verify pubring.asc setup.exe

gpg --verify pubring.asc setup.exe
gpg: verify signatures failed: unexpected data

:-(

I now see why Ubuntu uses md5/sha1 hashes a far easier method!

Any help will be much appreciated.

---

