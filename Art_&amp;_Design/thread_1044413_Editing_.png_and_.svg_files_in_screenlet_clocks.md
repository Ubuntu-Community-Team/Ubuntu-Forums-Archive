---
title: "Editing .png and .svg files in screenlet clocks"
date: 2009-01-19
forum: Art &amp; Design
---

### Post by sofasurfer on 2009-01-19
I am able to move clock appearance icons from one theme to another, thus somewhat customizing clocks in screenlets. But I want to move the kclock face (Clock.png) to the cairo-clock (clock-marks.svg). I think I did actually accomplish this using Gimp, but was unable to save the file because Gimp apparently does not support .png or .svg files.

What editor should I use for manipulating these files?

---

### Post by croto on 2009-01-19
hi,
gimp supports png formats. When you go to the "save as" dialog box, there's a drop down menu with the supported formats, and png is there.

---

### Post by sofasurfer on 2009-01-19
I found that I can save a .png file but I still can not save a .svg. I read that .svg is supported though plugins. I installed gimp-cbmplugins which is the only plugin source I could find. 

Can anyone tell me where to get .svg support?

---

### Post by crwmike on 2009-01-19
Try changing the file name to a .svg in the save-as dialog.(The GIMP will create a file in the correct format if recognised)

Also, take a look at Inkscape.

---

### Post by sofasurfer on 2009-01-19
Apparently Gimp is not able to deal with a .svg file. I found that .svg files are recognized by Inkscape (available through synaptic). But Inkscape can not save a .png file as a .svg.

I think this subject is beyond my current abilities. I don't know much about graphics editing at this time.

Maybe I should be asking if anyone out there has any customized clock faces for screenlets clock and kclock?

---

### Post by gigatwo on 2009-01-19
> **sofasurfer said:**
> Apparently Gimp is not able to deal with a .svg file. I found that .svg files are recognized by Inkscape (available through synaptic). But Inkscape can not save a .png file as a .svg.

I think this subject is beyond my current abilities. I don't know much about graphics editing at this time.

Maybe I should be asking if anyone out there has any customized clock faces for screenlets clock and kclock?

Png graphics and svg graphics are two completely different types of 2d graphics. Png, files, which are raster based images, are based up of pixels. SVG files are vector files that are pased off or points, curves and shapes, which means that they can be scaled to any size without pixelation.

Gimp is a raster editor (although it can import svgs), and inkscape is a vector editor (although it can export png files.)

---

### Post by crimesaucer on 2009-01-21
[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-20-12.png[/IMG]
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-20-13.jpg](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-20-13.jpg)

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-15-12.png[/IMG]
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-15-11.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-15-11.png)


I always edit my clock image. I just make a backup copy of the original, and then I use Inkscape to change the .svg image.


I do this for most of my screenlet's background.svg images. (see the calendar and the pager.)


I also edit the python scripts if I want to change the font that is used, or the RGBA color of the boxes used in the pager screenlet.

---

### Post by crimesaucer on 2009-01-21
I just imported a ".png" into Inkscape and saved it as a ".svg" and it worked for me..... although I wasn't able to re-edit the newly transformed ".svg" like I normally can using Inkscape with true .svg images.


So use GIMP to change your colors, save it as "background.png" then import into Inkscape and save it as "background.svg".

---

