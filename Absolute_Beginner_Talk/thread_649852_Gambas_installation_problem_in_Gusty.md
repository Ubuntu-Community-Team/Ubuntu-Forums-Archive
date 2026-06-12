---
title: "Gambas installation problem in Gusty"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by LinuxIsInnovation on 2007-12-25
I am using Ubuntu Gutsy amd64. 
Whn I mark gambas2 for installation in synaptic, this is exactly what I get:

**Could not mark all packages for installation or upgrade**
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

gambas2:
 Depends: gambas2-gb-compress-bzlib2 (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-compress-zlib (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-crypt (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-firebird  but it is not installable
 Depends: gambas2-gb-db-mysql (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-postgresql (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-odbc (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-db-sqlite (>=1.9.49-1) but it is not installable or
     gambas2-gb-db-sqlite2 (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-form (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-form-mdi (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-gtk (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-gtk-svg  but it is not installable
 Depends: gambas2-gb-image (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-info (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-ldap (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-net-curl (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-net-smtp (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-opengl (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-pcre (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-pdf (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-qt-ext (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-qt-kde-html (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-qt-opengl  but it is not installable
 Depends: gambas2-gb-sdl (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-settings (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-vb  but it is not installable
 Depends: gambas2-gb-v4l (>=1.9.49-1) but it is not installable
 Depends: gambas2-gb-web  but it is not installable
 Depends: gambas2-gb-xml (>=1.9.49-1) but it is not installable
 Depends: gambas2-ide (>=1.9.49-1) but it is not installable



I have checked that all my dependencies are enabled. What do I do? Any alternative for gambas which i can get in the repos? I cannot handle tar balls since Im still a Linux n00b :D

---

### Post by LinuxIsInnovation on 2007-12-26
Bump
Anyone? :D

---

### Post by gupta_sumesh63 on 2007-12-26
I am not sure but I read somewhere that Gambas does not work in 64-bit. I am really not sure about it. I installed it yesterday through terminal : Sudo apt-get install gambas2
It went like a charm.
Do sudo apt-get update and see if it shows any errors?

For installing anything in ubuntu please check this link
> [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

### Post by LinuxIsInnovation on 2007-12-26
That too gives the same output as above, but with this additional line:

E: Broken packages

---

### Post by gupta_sumesh63 on 2007-12-26
Do
> sudo apt-get install -f 
in the terminal. It will list out the broken packages which can be removed safely.
then try to reinstall gambas2 through terminal.

---

### Post by LinuxIsInnovation on 2007-12-26
Actully, I donot have broken packages. When I attempt to install Gambas2, it shows broken packages. Maybe it means that the libraries for gambas will cause broken packages in my system

---

### Post by gupta_sumesh63 on 2007-12-26
Ok .
try another thing.
In terminal type
> sudo dpkg --configure -a
Then try to install gambas2

---

### Post by LinuxIsInnovation on 2007-12-27
> **gupta_sumesh63 said:**
> Ok .
try another thing.
In terminal type

Then try to install gambas2


I did this but I'm getting the same error again.

---

### Post by kevinfishburne on 2008-04-03
Add:

deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) gutsy main

to your /etc/apt/sources.list, then refresh Synaptic and install gambas2. Looks like the Gutsy repositories are jacked up. I'm still playing around with it, but so far none of the example programs will run properly. I'm thinking the AMD64 version of Gambas is still fairly buggy.

---

