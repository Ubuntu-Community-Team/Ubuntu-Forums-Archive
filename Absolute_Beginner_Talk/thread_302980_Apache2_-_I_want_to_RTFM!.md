---
title: "Apache2 - I want to RTFM!"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by JimTDI on 2006-11-19
Hi everyone!

I've installed Apache2 - and can see the default page on port 80.  Now I'd like to read the docs - which I also installed (both through Synaptic) - can someone please tell me where the Apache2 manual was installed to on my hard drive?  I'd really like to RTFM!  :p

---

### Post by DaveBorealis on 2006-11-19
Hello,

You could try ```
$ locate Apache2 | less
```

and see what shows up.

Dave

[edit] That's from a terminal window.  'info locate' or 'man locate' will have more information on 'locate'.

---

### Post by JimTDI on 2006-11-21
I tried that, and NOTHING shows up - even tried without piping it thru less.  I did notice that when I get to the Apache2 default screen there is a link that says:

The Apache documentation has been included with this distribution.

If I clicked on the link I got some kind of error about /manual not installed (or something similar).  I reinstalled the Apache2-doc package - now I can see the user manual from the default Apache2 page.  So... now to go read!  :-)

Thanks for your reply!!

---

### Post by adamkane on 2006-11-21
I can't look for them at the moment.

You can use this for the time being:
[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

Also this has lots of relevant info as well:
[http://www.php.net/docs.php](http://www.php.net/docs.php)

---

### Post by JimTDI on 2006-11-24
Thanks for the links!  I got the docs to work as well...

---

