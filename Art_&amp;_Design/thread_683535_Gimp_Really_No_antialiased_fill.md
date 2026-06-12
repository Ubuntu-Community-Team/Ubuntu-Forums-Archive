---
title: "Gimp: Really? No antialiased fill?"
date: 2008-01-31
forum: Art &amp; Design
---

### Post by DirtDawg on 2008-01-31
Does the bucket tool really have no feathering or anti-aliasing? How can this be? The magic wand is anti-aliased, why wouldn't the bucket be as well?

As a result, when trying to fill an area surrounded by anti-aliased lines, I get hideous semi-transparent "moats" between the lines and the fill. 

Please, someone tell me I am missing something very simple here. I can find no feathering options for the bucket tool anywhere and internet sleuthing has left me empty handed.

---

### Post by jan quark on 2008-01-31
do you mean the white moats as in the pic on the right side ??

the left side is without the moats, because I created a new layer, put this layer above the main layer and selected multiply as the mode

but I am not really sure it that hits the nail on the head

---

### Post by DirtDawg on 2008-01-31
> **jan quark said:**
> do you mean the white moats as in the pic on the right side ??

the left side is without the moats, because I created a new layer, put this layer above the main layer and selected multiply as the mode

but I am not really sure it that hits the nail on the head

I have included an example of what I'm talking about. The "boulders" on the left were bucketed at a tolerance of 15 to really display what I mean by "moats". The boulders on the right were filled the bucket at about tolerance 150.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=58198&d=1201802706[/IMG]

Although it looks correct on the right, it is not. The fill is not anti-aliased so it's really more of a blunt instrument at that point. Also, turning the tolerance up and down doesn't work in many circumstances (not to mention a royal PITA). For example, what if I was trying to fill an area dark green surrounded by lines that were black? Then a tolerence of 150 would color everything dark green, both the fill and the lines.

This is really disappointing to me. I have been working with Gimp on a professional level for some time now and I not only love it, but it is superior to my copy of Photoshop 7 in many, many ways. But no feathering on the bucket!? Unless I am mistaken, I will have to boot into Windows for this project. Lame! :mad:

---

### Post by jan quark on 2008-01-31
and you can't use the layer method?

just make the black outlines and set a new layer as the "filling"

---

### Post by DirtDawg on 2008-01-31
> **jan quark said:**
> and you can't use the layer method?

just make the black outlines and set a new layer as the "filling"

Could you please explain? Do you mean crate a layer underneath the outlines and color those? I'm not clear on your meaning.

---

### Post by Paul820 on 2008-01-31
If you set the **threshold** to 100.0 it should fill right up to the black lines.

---

### Post by DirtDawg on 2008-01-31
> **Paul820 said:**
> If you set the **threshold** to 100.0 it should fill right up to the black lines.

Nope, I have tried this before with unsatisfactory results. An example to illustrate:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=58204&d=1201808354[/IMG]

---

### Post by smartalecks on 2008-01-31
between the black lines, is it transparent or is it white? If its transparent you can use the magic wand tool (make sure it is set to select transparent) and then expand the selection by 1 or 2, and on a layer below the outline layer you can add the color...

The gimp team has alot on their plate at the moment (gtk, gap, keeping up with the psd format changes...) but they are putting more focus on the gimp recently, hopefully we'll see 3.0 soon :D

---

### Post by DirtDawg on 2008-01-31
> **smartalecks said:**
> between the black lines, is it transparent or is it white? If its transparent you can use the magic wand tool (make sure it is set to select transparent) and then expand the selection by 1 or 2, and on a layer below the outline layer you can add the color...

Okay, well as long as I know there's no feathering on the bucket tool, and I'm just not missing something simple, I will resign myself to working with Photoshop for this kind of work. Too bad.

To my untrained mind, it seems like it would be easy to transplant the feathering code from the magic wand to the bucket, but what do I know.

> **smartalecks said:**
> The gimp team has alot on their plate at the moment (gtk, gap, keeping up with the psd format changes...) but they are putting more focus on the gimp recently, hopefully we'll see 3.0 soon :D

Indeed. Their work is appreciated, but it's frustrating to find these little annoyances when I'm trying to get something done.

---

### Post by red_Marvin on 2008-01-31
This got me curious, so I experimented a little, this is a somewhat cumbersome workaround, but anyway.

*Magic wand selection tool*: use this to select the area you want to fill, adjust the threshold so that the whole area, including the anti-aliased parts of the contour are selected.
Also adjust the feather edges to something small, just enough to make the filled area fade into the edges nicely.

*Flood fill bucket:* set the threshold to max (255) so that the whole selected area is filled. The feathering of the selection takes care of the edges.

---

