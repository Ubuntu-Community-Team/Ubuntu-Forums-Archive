---
title: "PHP script - What should firefox do with...?"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by redpop on 2006-10-26
I have been toying with ubuntu for a few weeks now.  I have installed apache1.3 and php4 (old school I know)!  when I try to open an html page with  php code and .php extension, I get a window asking me what to do with the file. My Options are open with apache or firefox. The latter loops me back to  the You have choosen to open....what to do? screen.

I used synaptic and not sure what out of the box changes I've overlooked.

I've traversed quite a few threads, but not sure what changes apply to me.  Just getting started with linux/unix OS jargon and such. 

Thanks, Redpop

lifelong Windows user itching to change!

---

### Post by ciscosurfer on 2006-10-26
I haven't read [this thread]("http://ubuntuforums.org/showthread.php?t=279155&highlight=php"), but it may help.

Check the [threads located here]("http://ubuntuforums.org/forumdisplay.php?f=7") as well.

In addition, you may find [this page on the UDSF]("http://doc.gwos.org/index.php/ServerGuide") helpful.

I would lastly add [the following link]("https://help.ubuntu.com/community/ApacheMySQLPHP").

Good luck!

---

### Post by sirlancelot on 2006-10-26
First, I recommend upgrading at least to Apache 2, it contains a load of features that make it so much easier to install modules like php.

If you insist on using the outdated Apache, try looking at this (I haven't tried it, as I run Apache 2): [http://www.e-gineer.com/v1/instructions/install-php4x-for-apache1xx-on-linux.htm]("http://www.e-gineer.com/v1/instructions/install-php4x-for-apache1xx-on-linux.htm")

---

### Post by redpop on 2006-10-26
Ahhhh!  Thats what LAMP stands for.  I've have read that Apache 2 support for PHP was still experiencing some problems. But sometimes yesterdays news is old news and there appears to be no problem with Apache 2.  I believe the previously mentioned link "the following link", should be helpful.

I'll  check back with the status

Thanks Again...

---

### Post by Kurt` on 2006-10-26
Apache's 1.x branch isn't "out-dated"; think of it rather as "insanely-stable". :P

Many hundreds of thousands of production servers still run 1.3.x :)

---

### Post by redpop on 2006-10-26
I have installed apache2 and php4 along with (libapache2-mod-php4). I have a .php html file in my home directory that shows mime/type application/x-php.  When I try to open it now, I get Cannot open phptest.php and switches the mime/type to text/html. I'm feeling like I took a step back!

Any suggestions to this point...

The help has been greatly appreciated!

---

