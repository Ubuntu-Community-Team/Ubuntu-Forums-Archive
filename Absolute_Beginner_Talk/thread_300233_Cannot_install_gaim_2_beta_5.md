---
title: "Cannot install gaim 2 beta 5 :/"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-11-15
I have tried loads of different tutorials, but none seem to work. Does someone know how I can install gaim 2 beta 5 for Dapper, which will work?!

Thanks :P

---

### Post by mahy on 2006-11-15
What exactly is your problem? Are you trying to install it from source? Are you able to install other things from source?

---

### Post by wr3cktangle on 2006-11-19
i got it to work by downloading the source and extracting it somewhere and then going into that folder from the terminal and using 

```
sudo apt-get build-dep gaim

./configure

make

sudo checkinstall
```

i did have to remove the version of gaim installed from the repositories.

i'm not experienced with building from source, so this may not be the best method, but it worked for me for beta 4 and now beta 5.
i got that code from some other thread.

you can get the source here
[http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=462444](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=462444)


i hope this helps, and/or someone will suggest a better or alternative method that also works.

---

### Post by mrgnash on 2006-12-06
> **wr3cktangle said:**
> i got it to work by downloading the source and extracting it somewhere and then going into that folder from the terminal and using 

```
sudo apt-get build-dep gaim

./configure

make

sudo checkinstall
```

i did have to remove the version of gaim installed from the repositories.

i'm not experienced with building from source, so this may not be the best method, but it worked for me for beta 4 and now beta 5.
i got that code from some other thread.

you can get the source here
[http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=462444](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=462444)


i hope this helps, and/or someone will suggest a better or alternative method that also works.

That worked great for me, thanks :)

---

