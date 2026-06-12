---
title: "How to tell Ubuntu which Apache folder to use"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by HurricaneDan on 2007-11-27
I am trying to get an older version of apache working (not my idea mind you) but also have apache2 installed on the machine.

I know how to stop the service for apache2 but how do I start the older apache and use the files in its directory to serve pages?

Thanks,

Dan

---

### Post by kelbizzle on 2007-11-27
Here ya go dan. [Starting apache 1.3 for unix ]("http://httpd.apache.org/docs/1.3/invoking.html#unix")

---

### Post by HurricaneDan on 2007-11-29
Thanks, that is what I needed.

Now here is the 'but' though.  When I attempt to use the command /usr/local/apache/bin/httpd I get a response of 'command not found'.

I was thinking that this has to do with something not being registered by the system to recognize the older version of Apache.  Does this make sense and if so how do I go about making sure the system does see it correctly?

Dan

---

