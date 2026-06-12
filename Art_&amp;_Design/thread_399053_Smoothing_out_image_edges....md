---
title: "Smoothing out image edges..."
date: 2007-04-01
forum: Art &amp; Design
---

### Post by TheForkOfJustice on 2007-04-01
I have 2 images attached.  Zoom up to 400x on them both in GIMP and look at the edges.  The Ubuntu logo has smooth edging but the other (one I made for [http://linuxforclinics.org](http://linuxforclinics.org)) has very irregular, jagged edging.

How do I make the edging in mine nice and smooth like the Ubuntu logo?

I've tried 'blur' and 'Gaussian Blur' but they don't produce exactly what I'm looking for, unless I'm doing it wrong.  Little help?

---

### Post by xiangpeng on 2007-04-01
> **TheForkOfJustice said:**
> I have 2 images attached.  Zoom up to 400x on them both in GIMP and look at the edges.  The Ubuntu logo has smooth edging but the other (one I made for [http://linuxforclinics.org](http://linuxforclinics.org)) has very irregular, jagged edging.

How do I make the edging in mine nice and smooth like the Ubuntu logo?

I've tried 'blur' and 'Gaussian Blur' but they don't produce exactly what I'm looking for, unless I'm doing it wrong.  Little help?

Is your logo a vector?

---

### Post by ComplexNumber on 2007-04-02
**TheForkOfJustice**
as xiangpeng implies, one of the images is an svg(or is a large non-svg) and the other isn't. use svgs to make an icon truly scalable.

---

### Post by TheForkOfJustice on 2007-04-02
> **ComplexNumber said:**
> **TheForkOfJustice**
as xiangpeng implies, one of the images is an svg(or is a large non-svg) and the other isn't. use svgs to make an icon truly scalable.

They are both PNG files.  My logo for LFC is bigger than the Ubuntu logo I included (even though it doesn't look that way).  View them both to see what I mean.

I have no idea what you mean by 'vector' and my logo was created at the same size at which you are looking at now.  It hasn't been resized.

---

### Post by ComplexNumber on 2007-04-02
> **TheForkOfJustice said:**
> They are both PNG files. My logo for LFC is bigger than the Ubuntu logo I included (even though it doesn't look that way). View them both to see what I mean.

I have no idea what you mean by 'vector' and my logo was created at the same size at which you are looking at now. It hasn't been resized.
i think you'll find that the 1st one looks jagged too when you scale it up to the same size. see screenshot. if you look it, you can see that it has used antialiasing.
the 2nd screenshot shows what they look like at the same same size.

svgs are vectors. svg = scalable vector graphics.

---

### Post by TheForkOfJustice on 2007-04-02
> **ComplexNumber said:**
> i think you'll find that the 1st one looks jagged too when you scale it up to the same size. see screenshot. if you look it, you can see that it has used antialiasing.
the 2nd screenshot shows what they look like at the same same size.

svgs are vectors. svg = scalable vector graphics.

How do I use anti-aliasing?  Will is make images look less jagged?

What difference would it make to save it as a svg?

Also, if you have to scale the image to compare them, isn't it kind of unfair?  The edges of my logo should look as nice as the ubuntu one at any size and resizing can introduce artifacts in image detail.

---

### Post by ComplexNumber on 2007-04-02
i honestly don't know how to use anti-aliasing. i've never had to use it. maybe someone else can help about that.

i think you are best off making it in inkscape at a reasonable size. vectors tend to have less 'jaggedness', but there may still be some present depending on much you scale it up. if you scale it down too much, svgs can sometimes look awful.

how big and how small are you wanting the logo to become anyway?

---

### Post by bashologist on 2007-04-02
Here's a svg file you could maybe use. [http://upload.wikimedia.org/wikipedia/en/9/94/Ubuntu_Logo.svg](http://upload.wikimedia.org/wikipedia/en/9/94/Ubuntu_Logo.svg)

Inkscape would probably be best for that. You would have to start your design over tho. It's worth the effort imo.

---

### Post by mcduck on 2007-04-04
> **TheForkOfJustice said:**
> How do I use anti-aliasing?  Will is make images look less jagged?

What difference would it make to save it as a svg?

Also, if you have to scale the image to compare them, isn't it kind of unfair?  The edges of my logo should look as nice as the ubuntu one at any size and resizing can introduce artifacts in image detail.

SVG can be scaled to any size with perfect quality, while resizing a bitmap image will reduce the quality, even more so if you need to make the image bigger for some reason. You should always make logos as vector graphics.

---

