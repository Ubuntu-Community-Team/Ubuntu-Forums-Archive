---
title: "package management"
date: 2005-05-24
forum: Absolute Beginner Talk
---

### Post by Sionide on 2005-05-24
One of the things I find a little annoying, is that the Ubuntu "approved" packages on Synaptic aren't often that up to date. For example, Gaim - version 1.3.0 has been released but Ubuntu didn't tell me so. I'm still using 1.1.4

I'm sure there's a way to change this? I just don't know what it is...

---

### Post by Kyral on 2005-05-24
Have you enabled all the repositories? 'Cause I'm using 1.3.0 as I got it through Apt-Get.

I'm just gonna paste my /etc/apt/sources.list here 'cause I'm feelin' lazy

```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb ftp://ftp.nerim.net/debian-marillat/ stable main
deb ftp://ftp.nerim.net/debian-marillat/ unstable main
deb ftp://ftp.nerim.net/debian-marillat/ testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
#deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
``` 

Replace your Sources.list with that and run sudo apt-get update

---

### Post by poofyhairguy on 2005-05-24
[QUOTE=Sionide]
I'm sure there's a way to change this? I just don't know what it is...[/QUOTE]

Yep. The forum has a project devoted to that.

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by poofyhairguy on 2005-05-24
um, kyrle...using those marillat lines is asking for trouble. plus it is not needed.

Please, everybody take note!!! marillat is a thing of ubuntu's past!

---

### Post by Sionide on 2005-05-24
So according to the backports thing, using the repos lines;

deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse restricted

...should do it?

I'm pretty certain anything ftp:// isn't gonna be liked on my system due to the way I connect to the Internet :(

Edit: Tried it and holy moly that repos is sooo slow :(

---

### Post by Gustav on 2005-05-24
> **Sionide]So according to the backports thing, using the repos lines said:**
> http://backports.ubuntuforums.org/ubp[/url] hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse restricted

...should do it?

I'm pretty certain anything ftp:// isn't gonna be liked on my system due to the way I connect to the Internet :(

Edit: Tried it and holy moly that repos is sooo slow :(
 Use one of the other mirrors they are much faster.

They are:

[ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/)
[http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)
[http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/)

---

### Post by Kyral on 2005-05-24
[QUOTE=poofyhairguy]um, kyrle...using those marillat lines is asking for trouble. plus it is not needed.

Please, everybody take note!!! marillat is a thing of ubuntu's past![/QUOTE]

Hehe, I didn't put them there, the Add-On Script thing did  :P 

I've never had trouble with them anyway. But if you insist

---

### Post by Sionide on 2005-05-25
[QUOTE=Gustav]Use one of the other mirrors they are much faster.

They are:

[ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/)
[http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)
[http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/)[/QUOTE]
 Do I add them all or will it only work with one of the mirrors at a time?

---

### Post by Xian on 2005-05-25
As Gustav said, use one of the other mirrors.
You only need a single working source for that repo.

---

