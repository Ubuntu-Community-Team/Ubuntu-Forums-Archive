---
title: "How to realize Automatic Updates (like in windows)?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by Sanych on 2006-05-04
Hi All.

The situation:

I want to make one machine (which will act as update server) to download updates from the internet using Ubuntu automatic update service. And all other machines have to download updates ONLY from my "update server".

Walkaround:

I was trying to build trivial repository like described in Wiki. On updates server I've installed pbuilder, copy all packages from /var/cache/apt/archives to web accesible directory /var/www/archive/binary and ran 

dpkg-scansources source /dev/null | gzip -9c > source/Sources.gz
dpkg-scanpackages binary /dev/null | gzip -9c > binary/Packages.gz

Ok. 

After that, on one of the rest machines in /etc/apt/sources.list I left only one string:

deb [http://updateserverip/archive](http://updateserverip/archive) binary/

And Ubuntu found all updates on my server. Except...

Problem:

Not all of packages was installed. Update manager said there are errors:

It was unable to find few packages on my server - 404 error. 
For example package login - on my server in /var/www/archive/binary it has name like login_1%3a4.0.3-37ubuntu8_i386.deb. But when update manager try to access it - it gives me error that file login_1**x**mystery_numbers_0.3-37..... not found.

**[updated]**
The error looks like this:
*W: Failed to fetch xttp://ip/archive/binary/login_1-0x1.9485a06874835p-64.0.3-37ubuntu8_i386.deb 404 Not Found*


Any advices?
Thanks.

---

### Post by TrendyDark on 2006-05-04
I think you would have to make it so that your "update server" would cache all the update files and then set the others update repository to the server you have. I would have no idea how to do such, but that sounds about like what you'd have to do.

---

### Post by Sanych on 2006-05-04
Thanks for reply!

[QUOTE=TrendyDark]I think you would have to make it so that your "update server" would cache all the update files [/QUOTE]

It is done. Update server caches all updates.

[QUOTE=TrendyDark]then set the others update repository to the server you have. [/QUOTE]

What do you mean by "others update repository"?

---

### Post by bluecherry on 2006-05-06
Maybe try to replace % by - or something?

Seems update manager is interpreting the char %xxx as hex(xxx) or dec2hex(xxx)?

Who knows, maybe you should give it a try.

Grtz,
BlueCHerry

---

### Post by Sanych on 2006-05-06
[QUOTE=bluecherry]Maybe try to replace % by - or something?

Seems update manager is interpreting the char %xxx as hex(xxx) or dec2hex(xxx)?[/QUOTE]

I've solved this problem using sshfs :)
And in sources.list wrote just file://my_repo binary/

and all was ok

I think the reason was in transfering updates via http.

---

