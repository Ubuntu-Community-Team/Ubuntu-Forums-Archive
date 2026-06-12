---
title: "Some themes I've made that could be made easier for the user if I knew ImageMagick"
date: 2011-03-02
forum: Art &amp; Design
---

### Post by LarsKongo on 2011-03-02
I've created several themes for GNU/Linux that requires some manual image editing to be used as intended.

For examples of what I mean check out some of my themes: ;)
[http://lassekongo83.deviantart.com/art/GAIA-Sprout-179554275](http://lassekongo83.deviantart.com/art/GAIA-Sprout-179554275)
[http://lassekongo83.deviantart.com/art/Soothe-199342656](http://lassekongo83.deviantart.com/art/Soothe-199342656)
[http://lassekongo83.deviantart.com/art/Zuki-Blues-175190463](http://lassekongo83.deviantart.com/art/Zuki-Blues-175190463)

The panel is supposed to be pasted on the wallpaper manually by the user because of limitations in Gnome. (I know that you can now set a transparent png image manually in the panel properties. However, this doesn't apply to images with rounded edges or other things that are sticking out a bit.) ;)

For more people to have the option to use my themes as intended I want to check the possibilities of creating an ImageMagick script that can do the following:

1. Check the user's desktop resolution.
2. Open the wallpaper image the user have placed in the same folder as the script.
3. Resize the wallpaper to the user's desktop resolution.
4. Open the panel.png file inside the same folder and then liquid-rescale it to the desktop width and place it at the top of the wallpaper image so the end result will look like this for example:

[[IMG]http://data.fuskbugg.se/skalman02/show-tn.png[/IMG]]("http://data.fuskbugg.se/skalman02/moarofthosegreen-panel.png")
(Click to enlarge.)
(Download wall here: [http://lassekongo83.deviantart.com/art/Moar-of-those-180844396](http://lassekongo83.deviantart.com/art/Moar-of-those-180844396) )

Now I have no idea where to start with ImageMagick as I've never used it before. So I'm asking here hoping that someone can help me out with some basics here. ;)

I know about liquid-rescaling as there's a plugin for GIMP, but everything else is new for me.

---

### Post by Copper Bezel on 2011-03-02
This is actually the wrong tool for the job. What you want is Conky. It's a very lightweight application that can be configured to overlay an image (or multiple images, or text, or geometry, or about six billion meaningless system meters, but that's irrelevant now) a on the user's desktop, above x-nautilus-desktop but below all applications. Full support for .png alpha, of course. See [this]("http://ubuntuforums.org/showthread.php?t=1676307") thread.

*Gorgeous* work, by the way.

---

### Post by Framli on 2011-03-03
Hi LarsKongo, this script should do the trick.

```
#!/bin/bash

# Find the biggest file in the folder as its certainly the wallpaper
wallpaper=$(ls -S1 | head -1)

# Use xdpyinfo to get the screen resolution : widthxheight
resolution=$(xdpyinfo | grep dimensions | grep -o \[0-9\]*x\[0-9\]* | head -1)

# Isolate the width (for the panel)
screen_width=$(echo $resolution | sed s/x.*//)

# Get the width of panel.png (we need it for liquid resize)
panel_width=$(identify panel.png | grep -o \[0-9\]*x\[0-9\]* | head -1 | sed s/x.*//)

# calculate the resizing amount needed for the width of panel.png
width_in_percent=$(($screen_width*100/panel_width))

# Show what we are doing
echo "Wallpaper : $wallpaper"
echo "Panel : panel.png"
echo "Resolution : $resolution"

# Imagemagick awesomeness appends here
convert $wallpaper -geometry $resolution\! $resolution-$wallpaper
convert panel.png  -liquid-rescale $width_in_percent%\!x100%\! $screen_width-panel.png

# Et voila! New files are "widthxheight-wallpaperfilename" and "width-panel.png"
echo "Files produced : $resolution-$wallpaper $screen_width-panel.png"
```

You really should learn some imagemagick commands, they are very powerful and easy to use! There is an extensive documentation at [http://www.imagemagick.org/Usage/](http://www.imagemagick.org/Usage/)

---

### Post by LarsKongo on 2011-03-03
Thanks for that. :D
Some problems though. Script doesn't keep the alpha transparency in the panel.png image. I've been googling some time now to find a solution, but none of them works. :P

Using this image: [http://data.fuskbugg.se/skalman02/panel.png](http://data.fuskbugg.se/skalman02/panel.png)

I'm also wondering if the liquid-rescale can ignore some margins to the left and right of the image so those rounded edges doesn't get stretched? (Just like liquid-rescale does in GIMP.)

---

### Post by babybean on 2011-03-03
No help here but I have to say it looks amazing, good luck getting imagemagic working.

---

### Post by Copper Bezel on 2011-03-03
Do you have any particular preference against just using Conky? I mean, you can have Conky draw the panel and just pin it to the upper right corner. There's no need to edit the backdrop, so when the user changes the backdrop, they don't have to run the script all over again. There's no trouble with rescaling, because the image would be cropped instead. It'd also save you a hell of a lot of time in making up this script.

---

### Post by LarsKongo on 2011-03-03
I'm looking into that too. :)
(I'm not sure if the user can click on gnome-panel if there's a conky over it though.)

ImageMagick however is good to learn too. ;)

---

### Post by Copper Bezel on 2011-03-03
Fair point! = )

I don't actually think Conky renders over Gnome Panel, but I'm only like 90% sure. (I'm embarrassed to say that I can't actually test it, because I somehow managed to bork my Gnome Panel soon after I stopped using it.)

---

### Post by arzali on 2011-03-03
Do you know gimp batch mode? [http://www.gimp.org/tutorials/Basic_Batch/](http://www.gimp.org/tutorials/Basic_Batch/)
I used it to make batch token icons and batch resize them.

---

