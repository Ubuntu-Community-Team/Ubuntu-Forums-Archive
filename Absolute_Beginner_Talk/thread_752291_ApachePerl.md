---
title: "Apache/Perl"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by Oxnigarth on 2008-04-11
Hello.

I have just recently switched from windows to linux and everything seems to be going fine. But there is one thing that has been bugging me for a while and since I do not know a lot of people who use linux I guess this is the best way to find out.

On windows I used to program using the IIS with files .asp using Perlscript and I would like to know if there is a way to do the same process in linux, by this I mean creating some sort of file which is supported by apache and that when I write Perl script code a browser can interpret it.

I have already installed Apache2 on my computer.

I hope someone can tell me if this is possible and if it is how can I do it.

Thanks,
Ox.

---

### Post by Oldsoldier2003 on 2008-04-11
> **Oxnigarth said:**
> Hello.

I have just recently switched from windows to linux and everything seems to be going fine. But there is one thing that has been bugging me for a while and since I do not know a lot of people who use linux I guess this is the best way to find out.

On windows I used to program using the IIS with files .asp using Perlscript and I would like to know if there is a way to do the same process in linux, by this I mean creating some sort of file which is supported by apache and that when I write Perl script code a browser can interpret it.

I have already installed Apache2 on my computer.

I hope someone can tell me if this is possible and if it is how can I do it.

Thanks,
Ox.

```
sudo a2enmod cgi
``` will enable cgi so you can run perl/cgi scripts

---

