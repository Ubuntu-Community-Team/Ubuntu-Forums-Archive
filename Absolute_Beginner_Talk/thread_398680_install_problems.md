---
title: "install problems"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by wannabuntu on 2007-04-01
hi there,
i've been trying to install dvd styler from the post

[http://www.ubuntuforums.org/showthre...ght=dvd+styler](http://www.ubuntuforums.org/showthre...ght=dvd+styler)

but when i put in

./configure --prefix="/usr"

it gives me this error

configure: error:

*** [Gentoo] sanity check failed! ***
*** libtool.m4 and ltmain.sh have a version mismatch! ***
*** (libtool.m4 = 1.5.22, ltmain.sh = ) ***

Please run:

libtoolize --copy --force

if appropriate, please contact the maintainer of this
package (or your distribution) for help.


what should i do to install dvd styler???

i also dont understand the 'make' and 'checkinstall' commands do they need a parameter?

newbie here

---

### Post by dmjones500 on 2007-04-01
> **wannabuntu said:**
> i also dont understand the 'make' and 'checkinstall' commands do they need a parameter?

I'm afraid I'm not sure about the first half of your question.

As for make and checkinstall, normally the process works as follows:

```
./configure *<options>*
make
checkinstall
*<follow prompts>*
```


Neither command normally requires arguments.  Checkinstall will provide prompts for you to choose certain options etc.

---

