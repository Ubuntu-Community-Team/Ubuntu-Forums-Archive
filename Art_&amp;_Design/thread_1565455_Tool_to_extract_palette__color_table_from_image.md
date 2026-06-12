---
title: "Tool to extract palette / color table from image"
date: 2010-08-31
forum: Art &amp; Design
---

### Post by InkyDinky on 2010-08-31
I'm looking for a tool that takes as an input an image (gif preferrably) and returns in some format the colors used in that image.
I want to take and image and extract the palette so that I can make a mosaic out of it in real life and therefore need to know the colors. However, I'm having trouble finding just such a tool.
Is there all ready a tool out there?
GUI or CLI (preferred)????

---

### Post by jtarin on 2010-09-01
Open your image in the Gimp there is a filter found in the image window menu under Colors &#8594; Info &#8594; Smooth Palette. Maybe not what you want but its the first thing to come to mind

---

### Post by lykeion on 2010-09-01
The CLI tool to use is ImageMagick.
You can use the convert command to generate a histogram of the image:```
convert image_file.gif -format %c -depth 8  histogram:info:-
```or you could convert a image into a simpler color table image:```
convert image_file.gif -unique-colors -scale 1000%  color_table.gif
```
Read more about ImageMagick usage _[here]("http://www.imagemagick.org/Usage/quantize/#extract")_

---

### Post by InkyDinky on 2010-09-01
Awesome! Your color_table example is pretty much exactly what I am looking for.
I figured ImageMagick could do it I just couldn't find the way to do it.

Also using 'identify -verbose file.extension' will print out the color map. But, it only works for gifs.

---

### Post by low2003 on 2012-04-14
Although this problem has already been solved, here is another way of extracting colors from any image that uses 256 colors or less with GIMP:

1. Image-->Mode-->Indexed; 
2. select "Generate optimum palette";
3. set "Maximum number of colors" to 256;
4. click "Convert";
5. Windows-->Dockable Dialogs-->Palettes;
6. right-click empty space inside tab (you should see a list of colored rectangles with writing next to them in the Palettes Dialog; right-click something white next to the writing);
7. select "Import Palette";
8. select "Image";
9. finally, click "Import".

You should see somewhere in the Palettes Dialog a rectangle containing all of the colors in your image, named after your image. For example, if your image was named "image.xcf", then "image.xcf" will be written next to your palette. There will also be a number in brackets next to the name, indicating the number of colors in your palette.

Read more about GIMP usage [here]("http://docs.gimp.org/en/gimp-concepts-palettes.html")

---

