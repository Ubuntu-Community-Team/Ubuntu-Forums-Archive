---
title: "Can Apache2 be downgraded to Apache 1.3.x?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by TJ Willy on 2008-02-10
...without doing a complete reinstall of LAMP and ISPConfig?

Can apt-get handle the backwards dependencies with remove and install?

---

### Post by tyggna1 on 2008-02-10
yes--kinda.  You have to uninstall apache2, and then find the source code or an old package for the appropriate version.   I think source-code would be your best bet--since Apache is pretty good about keeping older versions there.  Just install the build-essentials package so you can compile it.
Once you get the source code, unzip it with ```
tar xvf (you may need to add a z or a j before the f, depending on the compression algorithm) filename.tar
```
Once it's unzipped, navigate to the directory, and type in:
```
./configure
```
let it run, and if it looks like it completes okay, then type make, wait, and then type make install.   If it doesn't complete and gives you a message, then install whatever package it claims is missing and try again until it gets it.

Hope that helps.   I would note--however, that apache1.x is much less secure than apache2 of any version.  Be wary if you have to use it.

---

### Post by TJ Willy on 2008-02-10
Thanks for the heads up.

I am kinda forced into it b/c of mod_frontpage.  I have several not-for-profit clients that use frontpage to save on webmastering expenses.

I would much rather figure out how to get frontpage extensions to work with apache2 and ispconfig but I have been unable to find a "working" method of getting it done.  If you can speak to this, I would love to hear it.

Cheers.

---

### Post by tyggna1 on 2008-02-10
sorry, I use django for most my web-development (provided I don't get lazy and just write out an html file).  Don't really touch the microsoft standards anymore. . .
but, since you know the .so file you need for this-- if you find any package that contains that, and then include that file in your apache path, there's a good chance that it'll work in apache2.  (yeah, I read your previous thread too).  there's probably some good documentation on how to add plugins to your apache path.  Once you get it loaded in, just don't forget to restart apache so it loads it.  If it doesn't crash--then...well...good stuff.

---

### Post by TJ Willy on 2008-02-10
haha... "other post"... yeah, figured it might just be easier to downgrade Apache. 

Thanks for the info.

---

