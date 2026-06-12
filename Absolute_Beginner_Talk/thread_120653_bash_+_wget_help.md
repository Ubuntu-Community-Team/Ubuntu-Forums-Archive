---
title: "bash + wget help"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-01-23
I leave wget to download a series of files.  Sometimes, the links have changed or is suppose to forward some other page.  Well, wget doesn't understand this.  So it keeps on hammering the server.

How do I get wget to quit if it come across a certain message?  Say the message "111 Error" appears in console, and the script is programmed to exit if it comes across this message.  Does anyone know how to do this?

---

### Post by slashem on 2006-01-23
Type this : [COLOR="Blue"]man wget[/COLOR]

From the manual:

-t number
       --tries=number
           Set number of retries to number.  Specify 0 or inf for infinite retrying.  The default is to retry 20 times, with the exception of fatal errors like &#8216;&#8216;connection refused&#8217;&#8217; or &#8216;&#8216;not
           found&#8217;&#8217; (404), which are not retried.

---

### Post by cwaldbieser on 2006-01-23
[QUOTE=tux101]I leave wget to download a series of files.  Sometimes, the links have changed or is suppose to forward some other page.  Well, wget doesn't understand this.  So it keeps on hammering the server.

How do I get wget to quit if it come across a certain message?  Say the message "111 Error" appears in console, and the script is programmed to exit if it comes across this message.  Does anyone know how to do this?[/QUOTE]
You might also try using curl-- I think it understands redirects.

---

### Post by tux101 on 2006-01-24
Again, that doesn't stop it from hammering the server in a series of download.

If I told curl to download file1.foo to file100.foo, and the file series only goes up to file50.foo, it would start hammering from file51.foo to file100.foo.  It doesn't how know to stop.

Please help again.

---

