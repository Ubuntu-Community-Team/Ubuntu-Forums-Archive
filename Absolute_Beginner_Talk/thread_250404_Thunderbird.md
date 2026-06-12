---
title: "Thunderbird"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by wsun on 2006-09-04
Hi all, I've decided to install most of the software I need manually by downloading it from the website and then untarring it and installing. For thunderbird I have the following "problem" I installed it fine by doing 
tar xzvf filename and then ./thunderbird  but my problem is, I assumed it would be ok for me to delete the thunderbird folder after I was done installing. So I'm trying to figure out where is the default place that people install programs into? And could someone tell me how to do this?
Thanks a lot

---

### Post by amo-ej1 on 2006-09-04
Hi,

Well there are two places custom software can be placed, The normal place is in /usr/local/ which was originally made for this kind of things. Some people place it in /opt/ but if i'm not mistaken that's still some Solaris heritage.

On the other hand, it would not advise you to install software that is packaged by ubuntu by hand. It will be a terrible mess trying to keep you system up to date with library conflicts and outdated (vulnerable) software installed.  You would have to keep track of each individual piece of software yourself. When ubunut offers no installation candidate for a package that is you only option but in any other case (except the kernel package maybe) i'd install it from the ubuntu repository ... there is a reason why people invented linux distributions ;-)

---

### Post by diggity on 2006-09-04
Personally, I would install something like Thunderbird through Synaptic, but if you want to go the "manual" route, most distros install in the **/usr/share** directory or the **/usr/lib** directory. It really doesn't matter since all you are really doing is extracting the files. They could theoretically be anywhere.

---

### Post by wsun on 2006-09-04
thanks guys, I guess I will use the package managers then

---

