---
title: "Mozilla browser appears out of nowhere!"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by bcs on 2006-12-23
Hello,
I just looked in my "Applications"-->"Internet" directory, and for some reason Mozilla Web Browser and Mozilla Web Composer apps are now in that directory.  They definitely were not there when I installed Ubuntu (about a week ago), and I have not consciously installed them.  The only thing that I have done recently that may be related is I installing Eclipse and Sun-Java1.5-JDK...could Mozilla somehow been installed when I installed those (and added 

```

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

``` 

to sources.list)??

I *assume* its not a big deal either way, I am just curious how it happened...Thanks!

---

### Post by Sef on 2006-12-23
> could Mozilla somehow been installed when I installed those (and added

Code:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe multiverse

to sources.list)??

No.  Likely if you used Synaptic you accidently clicked on mozilla.

---

### Post by bcs on 2006-12-23
OK, thanks; that makes sense.   Weird, I just tried to uninstall it via "Add/Remove Apps" and it doesn;t appear in the list of installed apps...so be it.  Thanks for the help!

---

