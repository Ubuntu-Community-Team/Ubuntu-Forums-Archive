---
title: "Apache &amp; PHP Blank Page"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by TannerLD on 2007-06-05
Hello all,

After attempting to work with apache2 and php, I discovered that it was not displaying php pages for some reason. When I goto them in Firefox, it simply shows a blank page. Now I did a phpinfo(); page just to test, and that does not work either, but it works in the cli. How can I fix this?

Thanks
-Tanner

---

### Post by rich.bradshaw on 2007-06-06
I used this to get going,


[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


and it all works fine... Make sure you have all the relevant packages installed.

---

### Post by TannerLD on 2007-06-06
If it helps at all, I have found this in my error.log for apache.

[Tue Jun 05 21:55:10 2007] [notice] child pid 9210 exit signal Segmentation fault (11), possible coredump in /tmp

-Tanner

---

### Post by brien on 2007-06-07
Heya Tanner,

I just ran across this exact issue myself this morning. Can you provide the output of this command:
> ls /etc/php5/conf.d/*.ini; cat /etc/php5/conf.d/*.ini

in my situation the problem was caused by a module specific to cli php (it was php-gtk2 module) that was loading up with apache2 php and causing a seg fault since it's only meant to run under cli php.

to find out which module may be causing the problem, move (with 'sudo mv') all of those .ini files listed in /etc/php5/conf.d and move them into a different directory, i made a "inifiles" directory under the conf.d directory and then moved them all in there. after you have moved all the .ini files from conf.d, restart apache2

> sudo /etc/init.d/apache2 restart

test your phpinfo(); script and it should now work (hopefully). if so, move *one* of the .ini files back into conf.d directory, then restart apache2 again. test phpinfo(); script again, if that works, repeat... bla bla bla you get the picture. when you move an ini file, restart apache2, and then see the segfault again, you know that the last .ini file you moved is causing the problem. look at that .ini file and post the name and the contents in this thread.

if the module causing the problem is not needed, it may just be worth uninstalling it.

--brien.

---

### Post by TannerLD on 2007-06-08
Hello,

I did install php-gtk. After following your instructions and removing it; eureka it works. Many thanks.

-Tanner

---

### Post by brien on 2007-06-09
awesome!

--brien

---

