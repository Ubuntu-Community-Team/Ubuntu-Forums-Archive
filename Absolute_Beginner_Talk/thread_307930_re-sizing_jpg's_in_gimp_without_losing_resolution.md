---
title: "re-sizing jpg's in gimp without losing resolution"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by deep.tinker77 on 2006-11-27
Hello all, I need a little help with gimp. I've looked around, but I couldn't find a real good answer, so I'm asking you all. I'm trying to re-size jpegs to fit my desktop, but all I end up doing is streaching the image out and making it look terrible (fuzzy and blurry) ](*,) . Has anyone had any luck in re-sizing an image without losing resolution of the original. I appreciate any help. Thanks

---

### Post by Bachstelze on 2006-11-27
If you upsize an image, you lose resolution, it's mathematic and there's no way around this. Maybe trying a better scaling algorithm (None/Linear/Cubic, choose Cubic) will help a little but don't excpect too much.

---

### Post by deep.tinker77 on 2006-11-27
> **HymnToLife said:**
> If you upsize an image, you lose resolution, it's mathematic and there's no way around this. Maybe trying a better scaling algorithm (None/Linear/Cubic, choose Cubic) will help a little but don't excpect too much.


Ok, I'll give it a shot. I just found some really nice backgrounds on deviantart and i've been trying to get them to fit to my desktop with no good results. Thanks.

---

### Post by steve.horsley on 2006-11-27
If you tell Gnome to stretch an image to fir the desktop, it does a good job. It blurs it to disguise the large pixels. It's so good that I'm not sure it is worth re-working the inage in GIMP first.

---

### Post by deep.tinker77 on 2006-11-27
> **steve.horsley said:**
> If you tell Gnome to stretch an image to fir the desktop, it does a good job. It blurs it to disguise the large pixels. It's so good that I'm not sure it is worth re-working the inage in GIMP first.

Yea, I've done it in KDE, it works to a point, but it can really make an image blurry and fuzzy, which i'm trying to avoid. Thanks

---

### Post by Bachstelze on 2006-11-27
Get yourself a bigger image ;)

---

### Post by deep.tinker77 on 2006-11-27
> **HymnToLife said:**
> Get yourself a bigger image ;)

Lol, that's pretty much the only thing I have left to do. :D

---

### Post by jsilve1 on 2006-11-27
> **deep.tinker77 said:**
> Hello all, I need a little help with gimp. I've looked around, but I couldn't find a real good answer, so I'm asking you all. I'm trying to re-size jpegs to fit my desktop, but all I end up doing is streaching the image out and making it look terrible (fuzzy and blurry) ](*,) . Has anyone had any luck in re-sizing an image without losing resolution of the original. I appreciate any help. Thanks

It is impossible to take a small image (say, 100 pixels square) and increase it in size to a typical desktop size (say, 1024x768) without making it look like shite.

Impossible.

You cannot ADD data that does not exist.

It is *always* better to start with a Really Large Image(TM) and scale it *down* than to scale a small image up.

Scaling down? Use GIMP->Image->Scale Image, Choose "Cubic", then apply a light amount of Unsharp Mask to the final scaled size.

---

