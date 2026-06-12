---
title: "Inkscape installation help"
date: 2011-02-17
forum: Art &amp; Design
---

### Post by the_blue_box on 2011-02-17
Hi 
I don't know if this is the right place to post this but...
I have tried to install Inkscape 0.48.0 as a tar.gz
but when I get to the part where I have to run the command ./configure I get this error

```
configure: error: libgc (the Boehm Conservative Collector) 6.4+, is needed to compile inkscape -- http://www.hpl.hp.com/personal/Hans_Boehm/gc
```any help would be much appreciated.

[COLOR=Blue]the_blue_box[/COLOR]

---

### Post by davec64 on 2011-02-17
Hi,

You don't actually need to install from a tar.gz as 0.48.0 is already in the repositories. To install it:

```
sudo apt-get install inkscape
```

Or alternatively search for Inkscape in Synaptic.  :)

---

### Post by the_blue_box on 2011-02-17
](*,)](*,)](*,)

why didn't I think of that :roll: too much work and not enough sleep I think :D
it's installed now.

thanks a lot :D :D :D

[COLOR=Blue]the_blue_box[/COLOR]

---

### Post by prokoudine on 2011-02-18
Just in case, the next time you try to install a newer version of what's already in repositories, use

```
sudo apt-get build-dep name_of_application
```

That will usually fetch you all packages required to build this application. In case of Inkscape that would be

```
sudo apt-get build-dep inkscape
```

But really it's so much easier to use repositories and PPAs.

---

