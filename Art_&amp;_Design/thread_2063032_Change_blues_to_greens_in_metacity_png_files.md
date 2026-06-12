---
title: "Change blues to greens in metacity png files?"
date: 2012-09-26
forum: Art &amp; Design
---

### Post by mips on 2012-09-26
Hi,

I'm trying to edit the Greybird gtk/xfce theme so all blues are replaced by greens which has been easy using the gtk theme preferences utility. Problem is all the little .png files for the buttons etc in the metacity & unity folders are in blue

I need to find an easy way to change all of these little png files. Say we have a blue colour #398EE7 it must be changed to #39E78E so in essence I'm swapping the green & blue byte values around. Every png has several shades of blue in it to create a gradient for the little buttons so quite a few values need change.

Any ideas?

Please be specific in your responses as I know zip about gfx art and don't have a single artistic bone in my body :biggrin:



Screenshot sample of a blown up image in gimp,
[IMG]http://ompldr.org/vZm42cw/sample.png[/IMG]

---

### Post by mani.g on 2012-09-26
Try Gimp
- Colour (Menu)
- select Colouring (or whatever the thrid entry is called in English; I am German so I use the German version, there it says "Einfärben..." [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG])
- play around a bit and find the colours you want

Peter

---

### Post by GreatDanton on 2012-09-26
In Gimp I would try: colors/map/color exchange  (or just type color exchange in HUD if you are using Unity).

> - select Colouring (or whatever the thrid entry is called in English; I  am German so I use the German version, there it says "Einfärben..." [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG])In English version this item is called colorize, however I am not sure if that method is accurate enough for what he would like to do.

Hope this helps.

---

### Post by mips on 2012-09-26
Thanks I've tried these suggestions already but not getting anywhere.

---

### Post by GreatDanton on 2012-09-27
If previous suggestions are not working, then it will be best to ask at Gimp forums, since there hang experts for such things.

[http://gimpforums.com/](http://gimpforums.com/)

Regards.

---

### Post by mips on 2012-09-27
Thanks all.

Not being great at this sort of stuff I used Tools->Colorise to to change the .png files, it came close enough for me seeing they are so small the eye does not pick up the minor differences.

For the .xpm files it was harder as they had grey borders that form part of the window theming. Here I used a combination of Tools-Selection->By Colour Slelect followed by Tools->Colorise but this did not cover all the pixels so in a few of the images I also had to do a Colours->Map->Colour Exchange...

I'm pretty sure there is a much easier way to do this but for now I achieved what I wanted to at the expense of double vision & sore fingers :biggrin:

---

### Post by Parker32 on 2012-10-03
If (and it is a big if) you can figure out how the colour matrix in convert works, then something like the example in [http://www.imagemagick.org/script/command-line-options.php#color-matrix](http://www.imagemagick.org/script/command-line-options.php#color-matrix) will probably work. My best guess would be something like:
Code: [Select]

     " 1.0 0.0 0.0 0.0, 0.0, \
       0.0 0.0 1.0 0.0, 0.0, \
       0.0 1.0 0.0 0.0, 0.0, \
       0.0 0.0 0.0 1.0, 0.0, \
       0.0 0.0 0.0 0.0, 1.0" \
for a colour matrix, and then use a shell loop to apply it to all files. I would most definitely make a backup copy first before trying it.

---

### Post by ofnuts on 2012-10-04
> **mips said:**
> Hi,

I'm trying to edit the Greybird gtk/xfce theme so all blues are replaced by greens which has been easy using the gtk theme preferences utility. Problem is all the little .png files for the buttons etc in the metacity & unity folders are in blue

I need to find an easy way to change all of these little png files. Say we have a blue colour #398EE7 it must be changed to #39E78E so in essence I'm swapping the green & blue byte values around. Every png has several shades of blue in it to create a gradient for the little buttons so quite a few values need change.

Any ideas?

Please be specific in your responses as I know zip about gfx art and don't have a single artistic bone in my body :biggrin:



Screenshot sample of a blown up image in gimp,
Can't see the real image so I'm only guessing from your screen shot; but I would try:
- "Layer/Transparency/alpha to selection". This will do a partial selection on the semi-transparent gray borders. The question is whether this is above 50% selection or not, if under 50% , the marching ants won't include them (then ants march on the 50% frontier). This will be your lucky day.
- "Select/Sharpen": this is actually a threshold on 50% transparency, so if it is your lucky day you will be left with only the blue stuff selected (by definition, the marching ants will still be on the same line). If its not your lucky day, you have to threshold the selection for a  value greater that 50%: "Select/Save to channel", then edit channel,  apply Threshold tool, and "Channel to selection".
- paint new gradient with required color (it will only be applied to pixels in selection).

Otherwise, you can also have a shot at "Colors/Map/Rotate colors"

Otherwise, for this kind of image it is often quicker to redo them from scratch: 
- create base shape on transparent layer, filled with white
- duplicate layer
- Alpha-lock the top layer ("Lock" checkbox at top of layers list)
- Apply gradient to top layer (due to alpha-lock it won't change pixels opacity)
- Shift top layer vertically
- Adjust opacity of white layer
- Save as XCF
- Export as PNG or else

---

