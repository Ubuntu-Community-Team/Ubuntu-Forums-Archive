---
title: "how to use &quot;preload daemon?&quot;"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by paark.s on 2007-05-06
or any other suggestion on how I can preload a library to start program faster.

thanks.

---

### Post by felicity on 2007-05-06
You might try using 'man preload' or 'preload --help' if you already have it installed. If you used apt-get to install it, you can always check the homepage at [http://sourceforge.net/projects/preload](http://sourceforge.net/projects/preload) and download the tar to view the included Readme.

Here is some information from the Readme of 0.4:

The easiest way to run preload is by using the provided initscript.  If you
use the RPM package, you should be fine, otherwise you may need to manually
add the service and enable it, by running commands like:

  /sbin/chkconfig --add preload

Let preload run for a couple of boots before expecting it to predict that
much.  Technically, you need to run any application at least two times
before preload starts predicting it.

---

