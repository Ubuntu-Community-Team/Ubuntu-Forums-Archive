---
title: "Trouble trying to use PHP PDO_OCI"
date: 2011-11-10
forum: Any Other OS
---

### Post by igorsantos07 on 2011-11-10
Hello!

I'm struggling trying to run PHP with Oracle using PDO - my framework requires PDO, not the "pure" Oracle extension. I'm using Mint 11, that's based on Ubuntu 11.04.
I've noticed that there's no php-oci package, as happens with MySQL or PostgreSQL. In fact, there's no Oracle package, at all.
So, the first thing I tried was compiling OCI extension. It worked fine, I've downloaded Oracle Basic and SDK files, extracted, downloaded OCI package from PECL, and compiled. The extension is working just fine, but after all I noticed it didn't included the PDO.

And then my problem began: I can't compile the PDO_OCI extension, nor I can install it through PECL.

If I try to use PECL, it complains about don't having PDO extension - but it's installed and working for a couple of databases, as I can see from phpinfo(). Also, it says that the package is deprecated in favor of "channel://http://www.php.net/pdo_oci/ext/pdo_oci".
If I try to compile it by hand, it complains about PDO files; if I add then in the folder, the compilation stops with no messages when "executing libtool commands".

Anyone can help with this? I simply need pdo_oci running in my machine.

---

### Post by Perfect Storm on 2011-11-11
Moved to Other OS/Distro Talk.

---

