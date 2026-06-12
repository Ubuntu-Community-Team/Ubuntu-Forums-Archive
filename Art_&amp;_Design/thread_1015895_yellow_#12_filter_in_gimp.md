---
title: "yellow #12 filter in gimp?"
date: 2008-12-19
forum: Art &amp; Design
---

### Post by vajorie on 2008-12-19
I'm a newbie in photography[1], and I seem to like a lot the effect of the #12 yellow filter on black and white photographs. But the filter is expensive and I'm not sure if it's needed in digital photography. 

Say I take a color photograph with no filters. Is there a way to apply the effect of a yellow filter to that photo while converting it to black and white?

I googled this but nothing came up (wrong keywords?) except a lot of tutorials on "filters" like the curves tool etc. 

Thanks a lot :)

[1] I'm good with gimp but I don't understand how to use the "decompose" tool and what to do after decomposing - in case this is relevant for the answer.

---

### Post by pietjanjaap on 2008-12-19
Rewrite the file to grey scale, then rewrite to color, then you have still a black and white (grey) picture.
The you can do colors on top of this with a filter.

Or check this, [http://screencasters.heathenx.org/episode-076/](http://screencasters.heathenx.org/episode-076/)
Instead of the colors use your yellow.
Check also the main site, ther are more

Search on "gimp+tutorial" in google.
"gimp+filter"
"gimp+texture"
"gimp+howto"
"gimp+how to"
"gimp+training"

Check youtube

---

### Post by unutbu on 2008-12-19
Open the file in GIMP (File>Open).
Work in RGB mode (Image>Mode>RGB).
If the image has color, desaturate it (Colors>Desaturate).
Color it yellow (Colors>Colorify).

---

### Post by pietjanjaap on 2008-12-19
[http://www.gimp-tutorials.com/tutorial/Old-Photograph-373.html](http://www.gimp-tutorials.com/tutorial/Old-Photograph-373.html)
[http://www.tipclique.com/tutorial/fireworks/video-tutorial-old-picture/](http://www.tipclique.com/tutorial/fireworks/video-tutorial-old-picture/)
[http://www.tipclique.com/tutorial/photoshop/creating-warm-golden-sunsets-in-photoshop-with-gradient-maps/](http://www.tipclique.com/tutorial/photoshop/creating-warm-golden-sunsets-in-photoshop-with-gradient-maps/)
[http://gimpology.com/submission/view/convert_photos_into_gold/](http://gimpology.com/submission/view/convert_photos_into_gold/)

---

### Post by vajorie on 2008-12-19
hmm, the way I am seeing, these are instructions to apply some form of sepia-ness to images? perhaps I did not explain myself well enough :)

when taking black and white photos, if there is haze or if the sky is too light, using a yellow filter removes haze or increases the detail & contrast of the sky (used a lot in Ansel Adams' photos). Another name for this filter, I think, is "minus-blue". 

edit: the resulting photograph is still black and white with no "coloration" effects.

my guess is that this effect can be achieved thru gimp, perhaps by playing around with the RGB values after using the decompose feature, but I'm not sure how. 

perhaps using the "curves" feature in ufraw with a raw pic file? that feature totally escapes my low intelligence... 

sorry for the misunderstanding :)

---

### Post by unutbu on 2008-12-19
Suppose you took a black and white picture of clouds without the yellow filter.
Suppose the extra light causes the white areas to become over exposed.
Digitally, your image file has a bunch of extreme white areas represented by RGB values of (255,255,255). You've lost detail that can not be recovered.

This is an extreme, if not uncommon, example.

A milder form of the problem remains even if the picture is not overexposed. The detail is compressed into values very near 255 in the R,G,B channels. You can stretch the colors out using the Color>Curves tool as you mentioned. This may help a bit, but if the picture lacks enough pixels with distinct colors, the result may turn out blocky.

Here is a tutorial on using the Color>Curves tool (in GIMP).
[http://docs.gimp.org/en/gimp-tool-curves.html](http://docs.gimp.org/en/gimp-tool-curves.html)
To show more detail in the highlights, you would want a "concave up" curve -- like the right-half of the letter U.

---

### Post by kayosiii on 2008-12-19
ok well firstly filters have a place in photography even with digital maniplation if you manage to clip a colour channel then there is very little to get that back.

Beyond that though you might want to give the following a shot...
1) Colours->Invert
2) Colours->Components->Decompose->CMY
you should now have greyscale layers roughly corresponding to Cyan Magenta and Yellow from the original image.
3) Set the layer mode of Cyan and Magenta Channels to overlay (I am not 100% sure this is correct - play with other layer modes as well to see what you get)
4) now you can use the layer opacity slider on the cyan and magenta layers to drop their relative contribution to the image. which is essentially what the yellow filter does.

---

### Post by vajorie on 2008-12-19
> **kayosiii said:**
> ok well firstly filters have a place in photography even with digital maniplation if you manage to clip a colour channel then there is very little to get that back.

Beyond that though you might want to give the following a shot...
1) Colours->Invert
2) Colours->Components->Decompose->CMY
you should now have greyscale layers roughly corresponding to Cyan Magenta and Yellow from the original image.
3) Set the layer mode of Cyan and Magenta Channels to overlay (I am not 100% sure this is correct - play with other layer modes as well to see what you get)
4) now you can use the layer opacity slider on the cyan and magenta layers to drop their relative contribution to the image. which is essentially what the yellow filter does.

wow, that really helped. it didn't work exactly how you described, but it was a great pointer for how I wanted my black and whites to look like. for those who might want to do something similar: 

I grabbed a picture from flickr (I'm on my eee pc, my pics aren't here). 
1. invert colors
2. decompose to cmy 
2a. note: bc colors were inverted, what you see as yellow is in fact blue
3. put cyan layer on top, magenta below that, yellow at the bottom (the one with the most contrast goes to the top, the least goes to the bottom)
4. turn yellow layer invisible (unnecessary but just in case it has an effect)
5. play around with cyan and magenta to taste. 
6. save as jpg, done

here are the result (file name is: blue-CMY.jpg), along with the original (blue.jpg) and a desaturated copy of it (blue1.jpg). Just to keep up with the copyright of the picture (creative commons), it's from "m-a-e" in flickr. I searched for blue lol

edit: I no longer need to think whether I need a yellow filter ;) the effect here though is probably one from a very strong yellow filter and not #12.

---

### Post by VeeDubb on 2008-12-20
I have a better solution for you actually.

There used to be a really nice BW film simulation plugin for Gimp.  For some unknown reason, it is no longer included in Ubuntu's Gimp, and seems to have dropped off the face of the web.

Fortunately for you, I was able to find the old plugin, and if you'd like, I'd be happy to email it to you.  Just message me your email address.

It allows you to simulate a variety of B&W films, and apply a variety of filters to the image before conversion.  My personal favorite is Agfa200 B&W with a yellow filter.

---

### Post by kayosiii on 2008-12-22
> **vajorie said:**
> 

1. invert colors
2. decompose to cmy 
2a. note: bc colors were inverted, what you see as yellow is in fact blue

The inversion is needed because the CMY conversion inverts the colour channels. Since CMY is subtractive colour - the inversion just cancels this effect.
> **vajorie said:**
> 
3. put cyan layer on top, magenta below that, yellow at the bottom (the one with the most contrast goes to the top, the least goes to the bottom)

what is the rational behind this if I may ask?

---

### Post by vajorie on 2008-12-22
> **kayosiii said:**
> 
what is the rational behind this if I may ask?

substracting blue. same thing with canceling (or decreasing) B in RGB and playing around with R&G, but it looks nicer to me in CMY.

---

