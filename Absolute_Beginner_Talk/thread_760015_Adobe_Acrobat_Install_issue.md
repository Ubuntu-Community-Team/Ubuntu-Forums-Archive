---
title: "Adobe Acrobat Install issue"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by moored99 on 2008-04-19
So I went to Adobe website and downloaded the adobe rpm and tried to install, then I found that I have to install Alien to convert .rpm to .deb which means that I have to install Alien in Synaptic Package manager cant find it there how do I install Alien?

---

### Post by PeterJS on 2008-04-19
Alien is in the ubuntu repositories:
[http://packages.ubuntu.com/hardy/alien](http://packages.ubuntu.com/hardy/alien)

But converting RPMs to DEBs is hit or miss at best, you'd be better off getting adobe debs from Medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by moored99 on 2008-04-19
ok I instlaled Medibuntu and went back into Synaptic searched for Adobe and marked for install and this failed with following. what am I doing wrong.

W: Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.2-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.2-0medibuntu1_i386.deb)
  404 Not Found [IP: 91.121.38.148 80]


W: Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_8.1.2-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_8.1.2-0medibuntu1_i386.deb)
  404 Not Found [IP: 91.121.38.148 80]


W: Failed to fetch [http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_8.1.2-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_8.1.2-0medibuntu1_i386.deb)
  404 Not Found [IP: 91.121.38.148 80]

---

### Post by PeterJS on 2008-04-19
That's odd, the forums converted the url and I could download the deb from there... Try to download them manually from your post above, if that works installing again. Medibuntu's been known to have network hiccups, try it again and see if ti works.

---

### Post by moored99 on 2008-04-19
Manual download revealed.


Not Found

The requested URL /pool/non-free/a/acroread/acroread_8.1.2-0medibuntu1_i386.deb was not found on this server.
Apache/2.2.3 (Debian) DAV/2 SVN/1.4.2 PHP/5.2.5-0.dotdeb.2 with Suhosin-Patch mod_ruby/1.2.6 Ruby/1.8.5(2006-08-25) mod_ssl/2.2.3 OpenSSL/0.9.8c Server at packages.medibuntu.org Port 80

---

