---
title: "apt-get with proxies"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by rajaram_s on 2008-03-21
Hey... this apt-get install doesnt seem to work for me with proxies. I tried some of the old posts and threads, like changing the sources.list with the script that was given, changing the proxy settings for the computer etc., They worked to the extent that I am able to install updates to my computer. But this sudo apt-get command doesnt seem to work. How do I proceed?

---

### Post by Trail on 2008-03-21
```
export http_proxy='http://123.456.789.123:80'
``` works for me.

---

### Post by ilrudie on 2008-03-21
if you are using BASH which I believe is the Ubuntu default shell:
```
export HTTP_PROXY=http://username:password@proxy:port
```where username gets replaced with your user name, password with your password etc...

This is just a temporary change.  The next time you start a terminal you will have to export this property again.  You should be able to add this to your .bashrc file but I have not tried it to make sure.

---

### Post by bodhi.zazen on 2008-03-21
You may want to see this thread for using apt with a proxy :

[http://ubuntuforums.org/showthread.php?t=83401](http://ubuntuforums.org/showthread.php?t=83401)

---

