---
title: "Turning Text to 3D image"
date: 2007-07-09
forum: Art &amp; Design
---

### Post by ajax75 on 2007-07-09
Hi 
I'm trying to do a DIY logo of a name in a particular font. I want to convert the text into a 3D image with perhaps a light source directed on it from an angle.

Any ideas on any open source programs that would be suitable for such a task?

Thanks

---

### Post by dfreer on 2007-07-09
Hmmm. I would do it with GIMP (that's cuz I'm familiar with it), although I'm not sure about the light source aspect (you can do shadows and reflections, however). 
Some image manipulation/3D modeling programs that might help (just some names, I don't really use any so I can't say whether they will help or not):
GIMP
inkscape
blender (advanced!)

---

### Post by King_Critter on 2007-07-10
Gimp, definitely. You can either make one from scratch, if you know enough, but since I'm guessing you're not already a 1337 Gimp artist (after all, you *are* asking this question ^_^) there's a really easy way to do it. Just open the gimp, write some text, then right-click and select *Script-fu > Alpha to Logo*, then choose what kind of logo you want. Logos made easy. :D

---

### Post by durand on 2007-07-10
Gimp is really designed for 2D stuff, the first program that came to my mind was Blender3D...

---

### Post by dfreer on 2007-07-10
> **durand said:**
> Gimp is really designed for 2D stuff, the first program that came to my mind was Blender3D...

Is there a difference between blender and blender3D? I thought there was just the one program...

---

### Post by ajax75 on 2007-07-11
Thanks for the suggestions guys

I have tried Gimp and the* script-fu* stuff is interesting and gets pretty close but Blender seems  to be capable of producing what I really want. 

I can import a jpeg image of the writing I want into Blender but thats about it. Can I convert it into 3D somehow without tracing over it and redoing the whole thing by hand (mouse)?

Once again thanks

---

### Post by durand on 2007-07-11
Sorry, I think I misworded it. Blender is the same as Blender3D. I just wanted to say that Blender was what you would really need to use because others were suggesting using 2d apps. 

> I can import a jpeg image of the writing I want into Blender but thats about it. Can I convert it into 3D somehow without tracing over it and redoing the whole thing by hand (mouse)?

I would do something like this using inkscape to trace the image using Path>Trace Bitmap to get a path. If you then save this as an svg, you can import it into Blender using one of the included scripts! So now you have a traced path in Blender. You might have to tweak it a bit though.

Alternatively, here are some tutorials to do similar things. 

[http://blendernewbies.blogspot.com/2007/03/modeling-blender-3d-logo.html](http://blendernewbies.blogspot.com/2007/03/modeling-blender-3d-logo.html)
[http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/2D_Image_(logo)_to_a_3D_Model](http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro/2D_Image_(logo)_to_a_3D_Model)

Both are very good! Oh and if you could post your logo, I could give tracing it a go...

---

