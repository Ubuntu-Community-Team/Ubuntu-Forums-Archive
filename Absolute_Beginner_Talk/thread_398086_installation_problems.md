---
title: "installation problems"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by wannabuntu on 2007-03-31
hi there,
             i've been trying to install dvd styler from the post

[http://www.ubuntuforums.org/showthread.php?t=341791&highlight=dvd+styler](http://www.ubuntuforums.org/showthread.php?t=341791&highlight=dvd+styler)

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

newbie here:confused:

---

### Post by Maestro23 on 2007-03-31
..

---

### Post by wannabuntu on 2007-03-31
thanks for the link...helped a lot but i still have a problem...


the guide said to 


[COLOR="MediumTurquoise"]Configure the source. Since DVDStyler looks for libwxsvg.so.0 in /usr/lib we need to set the install path for wxsvg to /usr since the default installation path is /usr/local :
Code:

./configure --prefix="/usr"[/COLOR]

when i do that I get the error:

[COLOR="MediumTurquoise"]configure: error:

*** [Gentoo] sanity check failed! ***
*** libtool.m4 and ltmain.sh have a version mismatch! ***
*** (libtool.m4 = 1.5.22, ltmain.sh = ) ***

Please run:

  libtoolize --copy --force

if appropriate, please contact the maintainer of this
package (or your distribution) for help.[/COLOR]

what should i do? I dont understand this?

---

### Post by wannabuntu on 2007-03-31
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

### Post by LucasLinard on 2007-06-06
> **wannabuntu said:**
> hi there,
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
hi
can't help you but, there is something abou some file in wxsvg that is at the wrong version, there's a link to the right one but it doesn't wiork...

---

