---
title: "Error when installing Apache"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by MatsB on 2006-08-19
I'm trying to install Apache from source files.

admin@cacti:~/cacti-install/httpd-2.0.58$ sudo ./configure --prefix=/www .enable-so

configure: WARNING: you should use --build, --host, --target
checking for chosen layout... Apache
checking for working mkdir -p... yes
checking build system type... Invalid configuration `.enable-so': machine `.enable' not recognized
configure: error: /bin/sh build/config.sub .enable-so failed

Any ideas why this fails?

---

### Post by matthewv on 2006-08-19
Is there any reason that you can't use the version of apache2 in the repositories. That way you won't have any compile errors...

For the above error, are you sure you have all of apache's listed dependencies and -dev packages, and that you have build-essential installed?

---

### Post by MatsB on 2006-08-19
> **matthewv said:**
> Is there any reason that you can't use the version of apache2 in the repositories. That way you won't have any compile errors...

For the above error, are you sure you have all of apache's listed dependencies and -dev packages, and that you have build-essential installed?

Not really I just wanted to do the installation the hard way so learn Linux a little better. I'm pretty sure I have all dependencies and -dev packages plus build-essential installed.

Do you know what the "–enable-so" does and do I need it? 
If I run just ./configure --prefix=/www then it seems to work.

---

