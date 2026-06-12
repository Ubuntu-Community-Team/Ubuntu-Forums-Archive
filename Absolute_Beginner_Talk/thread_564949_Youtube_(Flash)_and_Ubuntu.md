---
title: "Youtube (Flash) and Ubuntu"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-10-01
I just installed the new Flash 9 and I still haven't been able to watch a single YouTube video on Ubuntu.

What am I doing wrong?  How do I get it so I can watch YouTube with Firefox on Ubuntu?

---

### Post by skymera on 2007-10-01
how have you installed it?

---

### Post by dmber on 2007-10-01
yup.  i just went through the installer from the Flash site.  

i installed it using the terminal.

edit: i thought you asked *if* i had, not how i had.  :)

---

### Post by rsambuca on 2007-10-01
Did you install the plugin?  Type in 

about:plugins

in the location bar of FF and see if it shows up.

---

### Post by dmber on 2007-10-01
it's there.

---

### Post by rsambuca on 2007-10-01
What happens when you try to play a flash video?

---

### Post by dmber on 2007-10-01
I've only really tried it with Youtube.  But when I try to play one, the first frame shows up, then Firefox freezes (turns dark grey) and I have to force quit.

---

### Post by shad0w_walker on 2007-10-01
Are you by any chance using Compiz/Beryl/Compiz fusion? If so, try disabling it and trying the videos again.

---

### Post by executor on 2007-10-01
tid test it, did not work for me, in opera, opera find the libflashplayer.so file, but it dos not work, back to the old verson 9

---

### Post by swoll1980 on 2007-10-01
Are you using gutsy

---

### Post by dmber on 2007-10-01
> **shad0w_walker said:**
> Are you by any chance using Compiz/Beryl/Compiz fusion? If so, try disabling it and trying the videos again.
i am using compiz fusion.  i will try it again in a bit -- i actually switched over to os x to do some other work for a bit.

thanks for the idea.

(i'm on feisty.)

---

### Post by Gremlinzzz on 2007-10-01
you can test your version of flashplayer here.
[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

---

### Post by odiseo77 on 2007-10-01
at dmber and executor: Besides testing any site with flash with beryl/compiz disabled, I'd suggest [adding extra repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") to Ubuntu, then open a terminal and type:

```
sudo apt-get install flashplugin-nonfree
```

That should do it.

Greetings.

---

### Post by tdrusk on 2007-10-01
Flash does this to me in firefox and konqueror. I have found the best workaround is to use opera. It's supposed to be fixed in Gutsy.

---

