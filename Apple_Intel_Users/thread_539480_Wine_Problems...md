---
title: "Wine Problems.."
date: 2007-08-31
forum: Apple Intel Users
---

### Post by Cheka on 2007-08-31
I've just tried to install wine as per 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I'm running a 64 bit version of the latest kernel (2.6.22.4).

When i try and find wine i get the following errors.....

cheka@chekmac:~$ wine
bash: /usr/bin/wine: cannot execute binary file
cheka@chekmac:~$ wineprefixcreate 
/usr/bin/wine: 1: Syntax error: "(" unexpected
cheka@chekmac:~$ 

Any help would be greatly appreciated as i have no idea what's wrong.

Thanks for your help

---

### Post by cyberdork33 on 2007-08-31
> **Cheka said:**
> I've just tried to install wine as per 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

I'm running a 64 bit version of the latest kernel (2.6.22.4).

When i try and find wine i get the following errors.....

cheka@chekmac:~$ wine
bash: /usr/bin/wine: cannot execute binary file
cheka@chekmac:~$ wineprefixcreate 
/usr/bin/wine: 1: Syntax error: "(" unexpected
cheka@chekmac:~$ 

Any help would be greatly appreciated as i have no idea what's wrong.

Thanks for your help
might just be a permissions problem. Try sudo. If it works, then you should just have to modify permissions to get it working for your user.

---

### Post by Cheka on 2007-08-31
Hey,

Thanks for the reply - I've fixed the problem now..

It appered when i compiled my custom version of the kernel i had disabled 32 compatibility mode. Seems to work now.

Thanks

---

