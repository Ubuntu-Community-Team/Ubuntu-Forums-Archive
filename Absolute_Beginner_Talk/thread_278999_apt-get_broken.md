---
title: "apt-get broken?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Lunchmeat on 2006-10-17
I accidentally deleted some important modules (as in the general sound help thread), and am now only left with a terminal interface... Every time i try and apt-get install gdm ubuntu-desktop etc.. it gives me a 403 error while trying to connect to the gb.archives server. I can ping the server, but no modules will install! 
Short of resinstalling ubuntu, is there anything i can do to get this back online?

thanks!

---

### Post by Ben Sprinkle on 2006-10-17
```

sudo dpkg --config -a

```
Or:
```

sudo dpkg -a

```
I forgot which, see if that helps. :)

---

### Post by Lunchmeat on 2006-10-18
I'm not sure what that is meant to do, but as far as i can tell it does nothing? I've looked in the dpkg help files without  ilumination too, though i'm not familiar with it at all.

any other ideas? i'm really stuck and stressed here...

---

### Post by Lunchmeat on 2006-10-18
I have now reinstalled Ubuntu, so all works, but i am still getting the error!! 

Here is a copy 'n paste of a bit of it:

oli@Oscar:~$ sudo apt-get update
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Errhttp://security.ubuntu.com dapper-security/main Packages
  403 Forbidden
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/multiverse Packages
Errhttp://security.ubuntu.com dapper-security/restricted Packages
  403 Forbidden
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages
Errhttp://security.ubuntu.com dapper-security/main Sources
  403 Forbidden


Any ideas?

Thanks,

---

