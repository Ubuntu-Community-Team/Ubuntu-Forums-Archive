---
title: "Java runtime Enviroment Help!"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by PfD on 2007-06-12
I want to install JRE in my pc. I see everywhere that a command like
```
sudo apt-get install sun-java6-jre
```

when i tap this i get a message that says "I could not find a name like "sun-java6-jre"
ok, not exactly this, but something similar.
what am i doing wrong?

thanx in advance.

---

### Post by Inxsible on 2007-06-12
Have you enabled the extra repositories?
 
[Enable Extra Repositories]("http://www.psychocats.net/ubuntu/sources")

---

### Post by HotShotDJ on 2007-06-12
Make sure you have Multiverse and Universe repositories enabled -- see [HERE]("http://www.psychocats.net/ubuntu/sources") if you don't know how to do that.

---

### Post by Najand on 2007-06-12
It is a multiverse package. Have you enabled them? If not, Go to
System => Administration => Software Sources and then check all options in "Ubuntu Software" page.
Then Close it and type:
```

$ sudo apt-get update
$ sudo apt-get install sun-java6-jre

```

---

### Post by PfD on 2007-06-12
Oh no I had not done this! Thank you very much! Now everything works!

---

### Post by mcavady on 2008-03-17
I had sort of the same problem but now I get this:

After unpacking 0B of additional disk space will be used.
Setting up j2sdk1.4-doc (1.4.2.02-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

Any clues on what I do next ?

---

### Post by jan quark on 2008-03-17
move on here
[http://ubuntuforums.org/showthread.php?t=727289](http://ubuntuforums.org/showthread.php?t=727289)
we are fighting with the same problem :)

---

### Post by billgoldberg on 2008-03-17
The same error popped up in another thread a few minutes ago.

Is the sun-java6-jre package in the ubuntu repo's broken?

---

### Post by mcavady on 2008-03-18
well I do not know about the repro being broken. I think that the reason is that the java development software has not been specifically written for ubuntu studio, 

I had a look at the sun java site and although there are linux package's on there they seem to be only written for other versions of linux. Could be wrong though as I am new to this and am still learning how to use linux,


 I have a friend that runs linux and may be able to help, If I get any further I hope to be able to be post some more information about this.

---

### Post by billgoldberg on 2008-03-18
> **mcavady said:**
> well I do not know about the repro being broken. I think that the reason is that the java development software has not been specifically written for ubuntu studio, 

I had a look at the sun java site and although there are linux package's on there they seem to be only written for other versions of linux. Could be wrong though as I am new to this and am still learning how to use linux,


 I have a friend that runs linux and may be able to help, If I get any further I hope to be able to be post some more information about this.

The java package in the ubuntu repo's have always worked, but their have been a few complaints about it not installing anymore this last few days.

---

### Post by mcavady on 2008-03-19
Thanks, Point taken.

---

