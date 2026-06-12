---
title: "Metacity help"
date: 2005-11-27
forum: Art &amp; Design
---

### Post by vendetta red on 2005-11-27
Just a quick queston about Metacity. Is it possible to have the minimize, maximize, and close buttons all different widths without having space between the images? My minimize button is 28px wide, maximize button is 26px wide, and close button is 43px wide. I have played around with the XML file and can't figure it out. If this isn't clear enough, I can post screenshots.

---

### Post by benplaut on 2005-11-27
what you should look for is a section similar to this, at the top of the file:

```
<frame_geometry name="normal">
  <distance name="left_width" value="4"/>
  <distance name="right_width" value="4"/>
  <distance name="bottom_height" value="4"/>
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>
  <distance name="title_vertical_pad" value="0"/>
  <border name="title_border" left="0" right="0" top="0" bottom="1"/>
  <border name="button_border" left="0" right="0" top="0" bottom="3"/>
  <distance name="button_width" value="35"/>
  <distance name="button_height" value="15"/>
</frame_geometry>
```

the line 

  <border name="button_border" left="0" right="0" top="0" bottom="3"/>

is the one you're interested in ;)

---

### Post by vendetta red on 2005-11-28
ok, I took a look at that line and the left and right button borders are already set to 0. It seems that since in the line:

```
<distance name="button_width" value="43"/>
```

I have the width set to 43, that Metacity is assuming all 3 images will be that width and creates spaces between the actual images while "hotspotting" the spaces to act as the buttons.

This is what I have:

[IMG]http://www.student.nvcc.edu/home/ptoy/Pictures/metacity_problem.png[/IMG]

This is what I'd like to achieve:

[IMG]http://www.student.nvcc.edu/home/ptoy/Pictures/window_buttons_normal_ss.png[/IMG]

Thanks for your help so far.

---

### Post by bvc on 2005-11-28
specify the diff sizes in the draw_ops of each button
```
<draw_ops name="draw_close_button">
   <image filename="act.svg" x="0" y="0" width="43" height="height"/>
</draw_ops>
<draw_ops name="draw_min_button">
   <image filename="act.svg" x="0" y="0" width="28" height="height"/>
</draw_ops>
<draw_ops name="draw_max_button">
   <image filename="act.svg" x="0" y="0" width="26" height="height"/>
</draw_ops>
```

---

### Post by Bandit on 2005-11-28
BVC,s example should work fine. If you want you can download some theme's from my website. I commented the heck out of them cuase I learned XML by beating my head into the wall... They are good for just starting out and many of my code has been optimized for speed. Even my pixmap themes run lighting fast.
Good luck, 
Joey :smile: 

[http://www.banditshome.net](http://www.banditshome.net)

---

### Post by bvc on 2005-11-28
yup, sometimes there's more than one way to do something in metacity. I haven't a clue what most of it means :p 

so you could try this also
```
	<draw_ops name="menu_button">
		<image filename="menu_small.png" x="(width / 2)-3" y="(height / 2)-3" width="9" height="9"
	</draw_ops>
```

---

### Post by vendetta red on 2005-11-28
Thanks for all the suggestions so far.

It seems still that the line:

```
<distance name="button_width" value="43"/>
```

over rides the individual button width settings here:

```
<image filename="button_close_normal.png" x="0" y="0" width="43" height="object_height"/>
```

creating the spaces between the images or if I set the main distance to 26 (the smallest buttons value) it causes this:

[IMG]http://www.student.nvcc.edu/home/ptoy/Pictures/metacity_problem2.png[/IMG]

Shortening all the button images to 26px, further showing that the initial value over rides the individual settings. Removing the line with the initial value cause the Metacity to not work.

In the long run I think I am just going to have to even out the widths of the images, because I don't think that what I am trying to do is possible. :(



EDIT: I went ahead and resized the images and here is a ss of the turnout:

[IMG]http://www.student.nvcc.edu/home/ptoy/Pictures/metacity_ss.png[/IMG]

---

### Post by Vidar on 2005-11-28
But is that line (that's causing the troubles) really necessary? What happends if you comment it out?

---

### Post by vendetta red on 2005-11-28
I had tried commenting it out and getting rid of it completely. Unfortunately it seems Metacity requires that line and the whole thing fails to work if that line is not present.

---

### Post by bvc on 2005-11-29
[QUOTE=vendetta red]I had tried commenting it out and getting rid of it completely. Unfortunately it seems Metacity requires that line and the whole thing fails to work if that line is not present.[/QUOTE]It does not require that line if you have this```
  <distance name="button_width" value="35"/>
  <distance name="button_height" value="15"/>
```
which is what I usually use. It gives you more control it seems. I think you can still overide this in the individual ops but I could be wrong. The other option is to place the button background on the titlebar and then place the buttons. I did that in Edgesoft if you need a reference to what I'm saying.

---

### Post by benplaut on 2005-11-29
that looks quite nice... i'm not much for vista themes, but that is a nice rendition :)

btw, help the environment (whatever...) and make your theme fitt's law complient... change the borders on title and buttons to zero, so that when maximized with no tollbar on the top of the screen, the top right corner pixel of the screen counts as part of the X

---

### Post by vendetta red on 2005-11-29
[QUOTE=benplaut]that looks quite nice... i'm not much for vista themes, but that is a nice rendition :)

btw, help the environment (whatever...) and make your theme fitt's law complient... change the borders on title and buttons to zero, so that when maximized with no tollbar on the top of the screen, the top right corner pixel of the screen counts as part of the X[/QUOTE]

Thank you, this is my firsy go at creating anything custom for the desktop. :) I had seen some screenshots of Vista and I thought the titlebar looked nice so I set about making it as similar as possible.

And in reference to fitt's law, I changed all the borders to 0 and the only thing that looked like it took effect was the top and bottom of the titlebar closed in as thin as the button images. The right side is curved and won't register a click on the 'X' in the very top right corner. I tried making the corner square, but it seems even with the border value set to 0 that there was some space between the end of the image and the side of the window. :confused: 

My other question is whether or not it would be legal for me to upload this to gnome-look, being that it is Vista style, or if I would have to just keep it for myself.

---

### Post by bvc on 2005-11-29
If all the artwork is yours then it's yours, although you should give credit to the designer, but in this case there's already many themes in this style so I wouldn't worry about that.

---

### Post by vendetta red on 2005-11-29
Ok, thanks.

---

