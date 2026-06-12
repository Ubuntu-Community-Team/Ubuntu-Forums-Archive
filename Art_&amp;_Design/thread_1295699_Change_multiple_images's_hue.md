---
title: "Change multiple images's hue"
date: 2009-10-19
forum: Art &amp; Design
---

### Post by simunic on 2009-10-19
Hello
I have a lot of images (icons in .png) and they are black and white with a blue shadow. Using the Gimp, when I set the hue valor (in hue-saturation tool) to 158, the icon stay black and white but with a red shadow. It's that simple, so I only have to open the image, set the hue and save the change. But I have more than 2000 icons to modify and it'd be impossible to change the whole.
So I though there have to be a script or a program to do that massively but I searched it in google and I didn't find anything. Anyone knows a solution to my problem?

---

### Post by mcduck on 2009-10-20
> **simunic said:**
> Hello
I have a lot of images (icons in .png) and they are black and white with a blue shadow. Using the Gimp, when I set the hue valor (in hue-saturation tool) to 158, the icon stay black and white but with a red shadow. It's that simple, so I only have to open the image, set the hue and save the change. But I have more than 2000 icons to modify and it'd be impossible to change the whole.
So I though there have to be a script or a program to do that massively but I searched it in google and I didn't find anything. Anyone knows a solution to my problem?

[Imagemagick]("http://www.imagemagick.org") is your solution. :)

It's a command-line image processing tool, highly usable with scripts.

I'd say the best tool for your purpose would be the "[modulate]("http://www.imagemagick.org/Usage/color/#modulate")", and you could use it to process all the images by doing something like this:

```
for i in *.png; do convert $i -modulate 100,100,158 recolored_$i; done
```

---

### Post by simunic on 2009-10-20
> **mcduck said:**
> [Imagemagick]("http://www.imagemagick.org") is your solution. :)

It's a command-line image processing tool, highly usable with scripts.

I'd say the best tool for your purpose would be the "[modulate]("http://www.imagemagick.org/Usage/color/#modulate")", and you could use it to process all the images by doing something like this:

```
for i in *.png; do convert $i -modulate 100,100,158 recolored_$i; done
```

Thank you very very much! I've been searching it a lot of time!
It works perfect converting more than 1000 files in only one directory so I obviously recommend it.

---

