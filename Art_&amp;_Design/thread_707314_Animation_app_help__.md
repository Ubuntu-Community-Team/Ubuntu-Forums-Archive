---
title: "Animation app help ?_?"
date: 2008-02-25
forum: Art &amp; Design
---

### Post by simmba on 2008-02-25
I am looking for an application that can take a video file (perhaps a digital camera vid file or a cell phone type) and can view each frame of the video as a seperate frame so I can make my own animation with certain frames. I had a hard time thinking of a title I hope that didn't throw you off at all >.< Thanks in advance for any help.

---

### Post by SpiderGorilla on 2008-02-25
I'm not sure if they can do it, but I assume they can. You can try the following pre-bundled applications:

Open Movie Editor
Pitivi Video Editor

Hope those help!

---

### Post by mendozaro on 2008-02-25
Kdenlive is your answer. You can find it in repositories.
You can use it to slice you video in frame size videos and do whatever you need with them.

---

### Post by ultimatsz on 2008-02-25
cinepaint... i think... go look around

---

### Post by CarpKing on 2008-02-25
```
sudo apt-get install gimp-gap
```

It will add a "Video" menu to GIMP and a "Split Video into Frames" option in the "Xtns" menu.  It might take some fiddling to figure it out, but it will do what you want.  If you have MPlayer installed, it can do it with any video format that it supports.  

Hints:  you'll probably want to use Video -> Frame Density to adjust the framerate (use Playback to make sure it still looks alright).  If you're trying to make an animated gif image, once you get to your desired framerate, use Frames to Image to get all the frames in the same file in GIMP, which you can resize to your desired size.  Then go to Image -> Mode -> Indexed and reduce the number of colors (to save space).  Next go to Filters -> Animation -> Optimize (for Gif).  This will make any parts of the image that don't change color between two frames transparent, again to save space.  Once you're satisfied, just save it as a gif and it will be animated.  If you have any questions, feel free to ask.

---

### Post by digitalis_vulgaris on 2008-02-26
It's sound funny, but the best application for 2d animation (based on my experience) is Blender. He has nice compositing tools, can read almost anything, you can draw directly on textures, make transitions and effects, combine it with 3d...
:lolflag:

---

### Post by lyceum on 2008-02-26
> **digitalis_vulgaris said:**
> It's sound funny, but the best application for 2d animation (based on my experience) is Blender. He has nice compositing tools, can read almost anything, you can draw directly on textures, make transitions and effects, combine it with 3d...
:lolflag:

I would agree when working from scratch. It is not good for video files though. If I am wrong I would love to see a how-to though. I can't see how you would get them into Blender.

---

### Post by eye208 on 2008-02-26
> **lyceum said:**
> I would agree when working from scratch. It is not good for video files though. If I am wrong I would love to see a how-to though. I can't see how you would get them into Blender.
[Blender's video editor](http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing)
[Blender's compositor](http://wiki.blender.org/index.php/Manual/Compositing)
[Using video as a texture](http://wiki.blender.org/index.php/Manual/Animated_Image_Textures)
[Using Blender in 2D mode (orthographic projection)](http://wiki.blender.org/index.php/Manual/Using_the_3D_View)

Using 3D programs in 2D mode is not uncommon. For example, South Park is made using Maya. Once you set the camera to orthographic projection, the result will have a flat 2D look. You can also render objects in a cartoon-like fashion, with black outlines etc. It's called "toon shading" or "cel shading".

---

