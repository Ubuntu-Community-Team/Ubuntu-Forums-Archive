---
title: "Non-GPL repository activation for Emerald?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by waggygee on 2007-07-10
I tried to activate the Non-GPL repositories for my emerald, at the bottom of the Emerald themer it tells me to add 'svn ls https://svn.generation.no/emerald-themes' to the shell and accept the server certificate. My question is how? I am not very experianced with the terminal.


georg@georg-desktop:~$  svn ls [https://svn.generation.no/emerald-themes](https://svn.generation.no/emerald-themes)

Error validating server certificate for 'https://svn.generation.no:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
 - The certificate hostname does not match.
 - The certificate has expired.
Certificate information:
 - Hostname: [www.generation.no](www.generation.no)
 - Valid: from Fri, 23 Jan 2004 15:37:06 GMT until Sat, 22 Jan 2005 15:37:06 GMT
 - Issuer: Webserver, The Next Generation, Elverum, Hedmark, NO
 - Fingerprint: e1:71:1c:fa:d2:2f:de:56:00:cf:73:e3:d8:9b:eb:99:a4:e5:9d:12
(R)eject, accept (t)emporarily or accept (p)ermanently? svn: PROPFIND request failed on '/emerald-themes'
svn: PROPFIND of '/emerald-themes': Server certificate verification failed: certificate has expired, certificate issued for a different hostname, issuer is not trusted ([https://svn.generation.no](https://svn.generation.no))


This is what I got after entering that command into the terminal, I notice it says something about me typing (p) to accept permanently, I typed 'p' and was told it was not a command, What am I doing wrong? And how do I do it right?

---

