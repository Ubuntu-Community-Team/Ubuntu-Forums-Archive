---
title: "Error while Installing any packages"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by varunjjacob on 2007-03-08
Hi guys,

Been using Ubuntu for about 2-3 weeks now.. just starting to get the hang of it... I am getting this error each time that I try to install any package.. even the video codecs... dpkg: parse error, in file `/var/lib/dpkg/available' near line 1308 package `xscreensaver-data':
 `Replaces' field, reference to `xscreensaver': version contains ` '
E: Sub-process /usr/bin/dpkg returned an error code (2)
No idea what all this is about... have any of you guys got this error??? 
I have tried installing using easyubuntu.. and the update manager.. but i keep getting the same error.. and yes I have uncommented the lines in that file.... 


Please Help me out guys,
Thanks in Advance 
Varun

---

### Post by Del Boy on 2007-03-08
Try running

```
sudo dselect update
```

---

### Post by varunjjacob on 2007-03-08
Hi,

I tried using that but this is the error that I getting now....
Fetched 3B in 3s (1B/s)
Failed to fetch 
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg)  Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
I think it downloads some packages but it is not able to get the other ones esp the video codec one

---

