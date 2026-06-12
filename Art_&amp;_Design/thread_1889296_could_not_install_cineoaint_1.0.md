---
title: "could not install cineoaint 1.0"
date: 2011-12-01
forum: Art &amp; Design
---

### Post by trad76 on 2011-12-01
ha all ,,,

i downloaded cinepaint 1.0 but it's give me a hell time to install it !

can i find some help please :)
Ubuntu 10.04.3

[http://sourceforge.net/projects/cinepaint/files/CinePaint/](http://sourceforge.net/projects/cinepaint/files/CinePaint/)

---

### Post by prokoudine on 2011-12-01
I managed to compile it even without Oyranos, but the application fails to find its own plug-ins and resources, so I cannot even load or save anything, and I'm not motivated to report given the project leader's track record.

Anyway, compilation boils down to the old './configure && make && sudo make install' routine withe the only exception that you really want specifying --prefix=YOUR_INSTALL_PATH_OF_CHOICE, otherwise Cinepaint won't find even its own libraries.

---

### Post by DMKryl on 2011-12-01
> **prokoudine said:**
> I managed to compile it even without Oyranos, but the application fails to find its own plug-ins and resources, so I cannot even load or save anything, and I'm not motivated to report given the project leader's track record.

Anyway, compilation boils down to the old './configure && make && sudo make install' routine withe the only exception that you really want specifying --prefix=YOUR_INSTALL_PATH_OF_CHOICE, otherwise Cinepaint won't find even its own libraries.

Why cinepaint CMYK mode was never fused with gimp?

---

### Post by prokoudine on 2011-12-04
> **DMKryl said:**
> Why cinepaint CMYK mode was never fused with gimp?

Where on Earth did you find CMYK in Cinepaint? :D

---

### Post by jcolyn on 2011-12-04
> **prokoudine said:**
> Where on Earth did you find CMYK in Cinepaint? :D

CMYK is in fact supported in Cinpaint.. I haven't used it lately but it does support it..

---

### Post by prokoudine on 2011-12-07
> **jcolyn said:**
> CMYK is in fact supported in Cinpaint.. I haven't used it lately but it does support it..

*sigh*

The question was "where", not "pretty please tell me once again it's there without providing any details" :D

I have it running here and now, and no &#8212; it's not there for sure.

P.S. I've even just compiled the forked version with newer code. Surely you don't mean the decompose thing?

---

