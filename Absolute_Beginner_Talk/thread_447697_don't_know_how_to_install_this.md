---
title: "don't know how to install this"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by SaltyTaro on 2007-05-18
So I found this raw converter for digital images, dcraw.c, and I go to [the site]("http://www.cybercom.net/~dcoffin/dcraw/"), and it says
> Compile with "gcc -o dcraw -O4 dcraw.c -lm -ljpeg -llcms" or "gcc -o dcraw -O4 dcraw.c -lm -DNO_JPEG -DNO_LCMS"
I don't get it.  I tried going to the folder that this was downloaded to and putting that into the terminal, but I got a ton of error messages
```
...
dcraw.c:2692: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
dcraw.c:2701: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
dcraw.c:2701: error: &#8216;stderr&#8217; undeclared (first use in this function)
dcraw.c: In function &#8216;foveon_fixed&#8217;:
dcraw.c:2712: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
dcraw.c: In function &#8216;foveon_make_curve&#8217;:
dcraw.c:2738: error: &#8216;M_PI&#8217; undeclared (first use in this function)
dcraw.c:2740: warning: incompatible implicit declaration of built-in function &#8216;calloc&#8217;
...

```
What should I do?

---

### Post by bashologist on 2007-05-18
Do you have build-essentials? If not then type the following.
sudo apt-get install build-essential

If that doesn't help then Idk.

---

### Post by Najand on 2007-05-18
dcraw is already on the repositories. You can get the ubuntu native package by using:
```
 sudo apt-get install dcraw

```

---

### Post by astoltz on 2007-05-18
dcraw is in the repositories.  Unless there's a reason you need to compile from source, installation is easy just ```
sudo apt-get install dcraw
```

EDIT  ---Damn, beat me to the punch...

---

### Post by Najand on 2007-05-18
LOL.... That is OK... I was just probably faster because of the time zones difference between Tokyo and Denver!

---

### Post by SaltyTaro on 2007-05-18
Ah, thanks, works perfectly

---

