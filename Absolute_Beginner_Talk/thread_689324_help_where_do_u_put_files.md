---
title: "help where do u put files????"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by shfd0169 on 2008-02-06
hello all

i'm new to this im trying to setup my att aircard the file i downloaded are on my desktop.  my question is where do i put them.  also the instruction state you "the kernel source must be download into **/usr/src.linux/** is this where the .zip and .tar files go?? 

thanks

---

### Post by Gen2ly on 2008-02-06
The network card software will need to find the kernel source to compile against (i.e. verify) the the proper components are already installed in the kernel.  In Ubuntu this will likely already be set up.  As to where to put that source package, it can go anywhere but the sources directory next to the sources for the kernel isn't a bad idea.

---

### Post by bodhi.zazen on 2008-02-06
Yea, I understand, the linux file system is a bit of a shock at first.

See this link for an overview of the organization :

[http://ubuntuforums.org/showthread.php?&t=258611](http://ubuntuforums.org/showthread.php?&t=258611)

OK, I put any personal files in a /data partition or in my home directory.

When I download source or .deb from outside the repos, I make a directory ~/src/applicaion_name

~ is short hand for /home/user_name

The ~/src/application_name keep it all organized.

So, move the archive there and extract it. You can then move it with :

```
gksu nautilus
```

I hope you are following a how-to or tutorial, what are you trying to do, there may be an easier way. link ?

---

