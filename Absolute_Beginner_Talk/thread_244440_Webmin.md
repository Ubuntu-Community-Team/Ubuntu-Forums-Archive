---
title: "Webmin"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2006-08-26
A while back this app was removed from the repository due to security issues (i think).

Any idea if this has been sorted out?

I am away from my computer and would luv to use this again, but only have SSH access until middle of the week when I return home. ;) 


If its safe to use can any1 give me a command to use at cli?


tnx.

---

### Post by bluefrog on 2006-09-24
all the webmin modules are in the universe repo afaik.

James

---

### Post by Abhi Kalyan on 2006-12-01
Webmin is still inaccessable from the repository,
Any idea how to get it?

---

### Post by Scorpuk on 2006-12-01
I ended up installing it from the DEB package.

Goto [www.webmin.com](www.webmin.com) and download the DEB package and follow their instructions:

> Installing the Debian Package
If you are using the DEB version of webmin, run the command dpkg --install webmin_1.310_all.deb and the install will be done automatically to /usr/share/webmin, the administration username set to root and the password to your current root password. You should now be able to login to Webmin at the URL [http://localhost:10000/](http://localhost:10000/) . 


I did have a problem where it didnt use my logon password as the root password so I eventually got help from these forums with the following command:

```
sudo /usr/libexec/webmin/changepass.pl /etc/webmin root enterpasswordhere
```

Just change enterpasswordhere with whatever you want.

Thanks to SlowYaRoll for the password help btw. :)

---

### Post by Abhi Kalyan on 2006-12-01
Thank you Scorpuk,
that was grand doing the thing now.
Thank you Once Again
Cheers!!

---

### Post by Abhi Kalyan on 2006-12-01
WOW Webmin Rocks!!

---

