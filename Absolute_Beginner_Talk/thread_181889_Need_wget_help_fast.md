---
title: "Need wget help fast"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by arsenic23 on 2006-05-24
I've been reading the wget -help but I'm still a little at a loss.

Can I use wget to easily download the contents of an entire directory on an ftp server.


I know I have to 
```
wget --ftp-user=something --ftp-pass=something ftp://fictional.ftp.server/dir/dir/
```
in order to get in using my login and password.  But is there a way to get that entire directory easily?

---

### Post by nalmeth on 2006-05-24
Try:

man wget

man knows a lot more than I do :)

---

### Post by arsenic23 on 2006-05-25
-r

I don't know why I had to read it so many times to see that's what I needed to do.   I think I need to find more time for sleep.  Thanks for the advice, I always forget man is much more helpfull then -help for some reason.

---

