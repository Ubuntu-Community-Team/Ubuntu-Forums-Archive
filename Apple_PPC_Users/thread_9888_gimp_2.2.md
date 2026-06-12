---
title: "gimp 2.2"
date: 2005-01-02
forum: Apple PPC Users
---

### Post by tiiim on 2005-01-02
is there a way of geting gimp 2.2 on the powerpc platform yet?

Its not on the updates and i guess it wont exist there until the next release of Ubuntu?

I did go to Debian side and download it but it wont install unless there is the other files which i could download but its nice to do it through apt cos' it saves the hassle. 

Is it really wrong to use the Debian source tree as well the Ubuntu or is that a bad idea? If not how do i get my system install the Gimp file from Debian and download the updates and upgrade the current packages? Or should i just wait to the official ubuntu realease in which case when is that...?

Tim :confused:

---

### Post by adamw on 2005-01-27
I'm in the same predicament.  I've tried installing the missing packages which GIMP 2.2's configure file was complaining about.  However, I've gotten to the point in the configure file where configure is failing because it needs GLIB version 2.4.5 or higher.  Does anyone know how to get this version of GLIB on warty?  (Warty's GLIB is version 2.0 it seems, and I can get the latest GLIB 2.6.1 to build from source, but not sure how to make GIMP recognize the updated version...)

---

### Post by robsta on 2005-02-21
If you need it urgently you can add hoary apt lines to your sources.list, install The Gimp and then switch back to warty. Hoary is already in beta phase, the used gtk+ release itself is stable already. I've ran such a machine for some time and it worked well. YMMV, as usual.

- Rob

---

