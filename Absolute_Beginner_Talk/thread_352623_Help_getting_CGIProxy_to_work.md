---
title: "Help getting CGIProxy to work"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by kjacks on 2007-02-03
I've just installed CGIProxy on my 6.10 LAMP server but I cannot get it to work.  When I go to [http://localhost/cgi-bin/nph-proxy.cgi](http://localhost/cgi-bin/nph-proxy.cgi) i just get a blank, white, screen.  I'm stumped since I'm not getting the "404 Not Found" error.

If I type in [http://localhost/cgi.bin/nph-proxy.cgi/www.google.com](http://localhost/cgi.bin/nph-proxy.cgi/www.google.com) Firefox prompts me to download a file named "www.google.com"

I placed the CGIProxy file in /usr/lib/cgi-bin/ 

I made a link: sudo ln -s /usr/lib/cgi-bin /var/www/cgi-bin

I changed permissions: sudo chmod 755 /usr/lib/cgi-bin nph-proxy.cgi

Any help you guys could give would be great!

---

### Post by shareMenaPeace on 2007-02-03
Try to seek for an answer in the Server Forum
[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

Cheers

---

### Post by breaking on 2008-03-08
Try with the last version:
[http://rapidshare.com/files/97988487/cgiproxy.2.1beta16.zip.html](http://rapidshare.com/files/97988487/cgiproxy.2.1beta16.zip.html)

---

