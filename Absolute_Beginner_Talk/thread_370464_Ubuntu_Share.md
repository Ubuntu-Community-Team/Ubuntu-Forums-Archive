---
title: "Ubuntu Share"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by alanrr_sr on 2007-02-25
I would like to have a directory where every user of my system has write and read permission.
If someone copy anything on that directory, it will be automatically read/write anyone (or rw for  group)
How is the easy way to do that??? 

I could create a samba share and everyone could use it, but a non networked solution would be better. Create a partition is not a option anymore, and ask people to chmod everytime would be annoying.

What is the best solution??

---

### Post by mlissner on 2007-02-26
You're in luck. Your system comes with a directory with just that power. It's located in:
```
/tmp
```

That is, in fact, just the purpose of that directory. However, if you want to create another, the thing you're looking for is the "sticky bit".

---

### Post by Bachstelze on 2007-02-26
Be careful with /tmp though, it is cleaned at each reboot. Basically, if you want to make a dir read/writable by everyone, CHMOD it to 777.

---

### Post by mlissner on 2007-02-26
Well I'll be damned. I never picked up on that because I just always used it for...Ahem...temporary stuff...

I reiterate, the thing you're looking for is the [sticky bit]("http://www.linuxdevcenter.com/pub/a/linux/lpt/22_06.html"). Good grief.

---

### Post by alanrr_sr on 2007-02-26
I did not get... maybe I understood something wrong...

I would like that Jane has the permission to create a file in /home/media , for example... but john, 5 minutes later, would like to change that file, and he is able too.

I wouldn't like to change default umask change.
With stick bit, I would have something like:
drwxrwxrwt   2 root     root       96 2007-02-26 22:29 test

When joe writes something there, we will get: (ls test -la)
drwxrwxrwt 2 root     root      96 2007-02-26 22:29 .
-rw-r--r-- 1 joe joe   6 2007-02-26 22:29 hello.test

But if jane wanna change something in hello.test, she would get a permission denied,. and that is not desired.

Any others solutions?

I can setup a samba share, and force a user in test. Everyone that write something there, should use the samba share (with mode 755, example)...
But this is a good solution?

Thanks again:KS

---

### Post by mlissner on 2007-02-26
Ah. OK. So the sticky bit isn't what you're after if you want them to be able to edit each other's files. 

My thought is to make a script run as a chron job that runs this (untested) script:
```
#!/bin/bash
chmod -R 777 * /SHARED DIRECTORY
exit 0

```

That would simply change the permissions of everything in that directory to 777 as often as it was run. If you made it a chron job every five minutes or so, you'd be set without resetting their umask value. Just make sure it's a chron job for root, or else it won't run when other people are logged in (I believe).

The other trick you might think about though is putting these people in the same user group and then adjusting their umask as necessary so they can read each other's stuff if it's in a directory where they both have access. It's a bit tricky though depending on the permissions of their home directory, but that sounds like a more elegant solution to me. That is what groups are for afterall.

---

