---
title: "How to convert RPM into Debian-Ubuntu using Alien"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-10-10
I have a BIG problem with Gnome-PPP. I am trying to use another dialer:

[http://www.linux-kheops.com/pub/vppp/vpppGB.html](http://www.linux-kheops.com/pub/vppp/vpppGB.html)

it is an RPM file.

The "unofficial" ([http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)) UbuntuGuide says 

 "How to install .rpm to .deb Converter (Alien)

    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install alien

    * Install alien with examples"

When I sudo, I get:

Package alien is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alien has no installation candidate

Where oh! Where has my little package gone? 
Where oh! Where can it be?

---

### Post by drpepper on 2006-10-10
This might sound daft, but did you add the extra repositories it asked in the guide?

---

### Post by Marsolin on 2006-10-10
You should also check out [Wajig]("http://linuxappfinder.com/package/wajig"). It's an easy way to use apt-get or alien.

Type "wajig listcommands" after installing it to see what it can do.

---

### Post by az on 2006-10-10
That application looks very old (2003?)  You probably should use the source version.

---

### Post by Marsolin on 2006-10-10
Edit: deleted

---

### Post by Mark_in_Hollywood on 2006-10-10
[COLOR="Blue"]I'm responding to all the posters as of 3:39pm pacific daylight time, on 10.10.06 as follows, in blue color:[/COLOR]

This might sound daft, but did you add the extra repositories it asked in the guide?

[COLOR="Blue"]I will double check[/COLOR]

You should also check out Wajig. It's an easy way to use apt-get or alien.

Type "wajig listcommands" after installing it to see what it can do.

[COLOR="Blue"]Thanks, but I have enough to learn without adding more complexities[/COLOR]

That application looks very old (2003?) You probably should use the source version.

[COLOR="Blue"]What does age have to do with it? AND how will using the souce code help? Yikes![/COLOR]

Edit: deleted

[COLOR="Blue"]Doh! Ouch![/COLOR]

---

### Post by Marsolin on 2006-10-10
> **Mark_in_Hollywood said:**
> Edit: deleted

[COLOR="Blue"]Doh! Ouch![/COLOR]

No ouch about it.  I deleted it myself because I misread an earlier post.

---

### Post by PriceChild on 2006-10-10
> **azz said:**
> That application looks very old (2003?)  You probably should use the source version.I'll agree with azz on this one.

If you aren't going to use an official ubuntu package, then you should build your own preferably to using an rpm.

using alien removes information which may break your system, or just that app.

Sometimes this is useful, for example at one point i aliened cedega rpm packages due to incorrect dependencies on the latest debs.

---

