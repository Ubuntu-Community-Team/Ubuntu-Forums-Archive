---
title: "Glow Maps in Blender"
date: 2009-05-07
forum: Art &amp; Design
---

### Post by chips24 on 2009-05-07
how do i make a glow map in blender?
 
 i already understand specular (reflection) maps, bump maps, alpha maps and textures...
 
im trying to accuratly model earth.
 
thanks

---

### Post by hessiess on 2009-05-07
To create glow in Blender you need to:
a) Use the compositor
b) Create a second mesh with a `glow' material
c) a mixture of the above

For example, this uses method c:

[IMG]http://hessiess.dyndns.org/files/earth.png[/IMG]
[http://hessiess.dyndns.org/files/earth.blend]("http://hessiess.dyndns.org/files/earth.blend")

---

### Post by chips24 on 2009-05-12
i have not yet been able to retrieve the file, glow maps include city lights... right?

---

### Post by hessiess on 2009-05-12
> **chips24 said:**
> i have not yet been able to retrieve the file, glow maps include city lights... right?

Sorry, thought you meant glow as in atmosphere glow ;)
To create city lights you should be able to map a lights texture to the emit channel.

Don't know why the link isn't working for you, works fine here.

---

