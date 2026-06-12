---
title: "java options"
date: 2006-06-04
forum: Apple PPC Users
---

### Post by eidex on 2006-06-04
hi, i have installed ibm's java 1.5 devkit on my ibook g4 but cant use mobilebanking ([www.netbanking.at)](www.netbanking.at)), the mozilla-firefox plugin causes a crash of firefox and konqueror has troubles after authentication.

i found this article on the web: [http://www.ppczone.org/news.php?id=271](http://www.ppczone.org/news.php?id=271)

is it possible to run this version of suns java on my ibook?

---

### Post by ssam on 2006-06-05
have you looked at [https://wiki.ubuntu.com/JavaPPC](https://wiki.ubuntu.com/JavaPPC)

---

### Post by davygravy on 2006-06-05
GIJ is the opensource Java platform and can be downloaded via apt-get as simply gij. You can also install it through Synaptic.

 I have GIJ installed and it seems to work pretty well...

---

### Post by eidex on 2006-06-05
[QUOTE=ssam]have you looked at [https://wiki.ubuntu.com/JavaPPC](https://wiki.ubuntu.com/JavaPPC)[/QUOTE]

i did follow the wiki, when i open the java test page ([http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)) the page shows me this dancing thing with the used plugin/os, but sometimes it crashes giving the following error:
```
(firefox-bin:5198): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Plugin: Java VM process has died.
Java Plug-in ERROR
INTERNAL ERROR on Browser End: JavaVM5::SendRequest: Got an erroneous ack. 17 16           384021

```

any ideas?

---

### Post by eidex on 2006-06-15
i solved the problem by downloading a newer version of ibm's JDK 1.5, mine was a few months old and everything works fine now :)

---

### Post by eidex on 2006-08-05
strange thing, java worked great but suddenly starts to crash firefox again when opening [www.netbanking.at:](www.netbanking.at:)

```
Plugin: Java VM process has died.
Java Plug-in ERROR
INTERNAL ERROR on Browser End: JavaVM5::SendRequest: Got an erroneous ack. 9 16384021

System error?:: Success

```

any ideas? i only installed gnash but that should not interfere with java..

---

