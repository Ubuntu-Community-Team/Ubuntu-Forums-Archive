---
title: "can't find installed Wordpress"
date: 2010-03-07
forum: Art &amp; Design
---

### Post by SVEN1 on 2010-03-07
Just installed Wordpress from the Synaptic Package Manager.
I searched the Applications menu, it's not there. Did a file search can't find it.

Any ideas where it went to??
Thanks

---

### Post by Niva on 2010-03-07
I think you've definitely posted in the wrong forum.

I'm curious what you're trying to do with Wordpress from the applications menu with?  Are you trying to set up an installation on your own server?  If you've already set your server up it's easier to go to the public_html directory and simply dump the wordpress files there which you can download straight from the wordpress site itself.  I recommend doing this because the ones on the Ubuntu Synaptic manager are already an older version.  

Hope this helps.

---

### Post by era86 on 2010-03-08
[http://acassis.wordpress.com/2008/10/30/installing-wordpress-on-ubuntu/](http://acassis.wordpress.com/2008/10/30/installing-wordpress-on-ubuntu/)

This tutorial helped me get it started.  Are you looking to deploy this?  I believe the package default in Ubuntu installs msyql and apache2.  You still ahve to configure everything yourself, but you should be able to access the new WP blog by going to [http://127.0.0.1/blog](http://127.0.0.1/blog).  This assumes you have apache2 running as a service.

Goodluck!

---

