---
title: "change menu button in metacity theme"
date: 2006-06-01
forum: Art &amp; Design
---

### Post by hezral on 2006-06-01
anyone knows how to change the menu button in this theme [http://www.gnome-look.org/content/show.php?content=38917](http://www.gnome-look.org/content/show.php?content=38917)

so that it shows the icon of the application instead?

---

### Post by bvc on 2006-06-01
copy and past this over the current menu code```
<draw_ops name="menu_button">
	  <icon alpha="1.0" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>

<draw_ops name="menu_button_pressed">
	  <icon alpha="0.5" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>

<draw_ops name="menu_button_prelight">
	  <icon alpha="0.7" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>

<draw_ops name="menu_button_unfocused">
	  <icon alpha="0.50" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>

<draw_ops name="menu_button_unfocused_prelight">
	  <icon alpha="0.7" x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>
```

you also might want to make maximized windows correctly
```
<frame_geometry name="no_borders" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="0"/>
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>
  <border name="title_border" left="0" right="0" top="0" bottom="1"/>
  <border name="button_border" left="2" right="0" top="2" bottom="2"/>
</frame_geometry>
```

---

### Post by hezral on 2006-06-01
thanks a lot bvc!!!! i'll try it when i get home.

---

### Post by bvc on 2006-06-04
you can also leave the menu button there and put the app icon next to the title text.
```
<draw_ops name="title_focused">
  		<icon x="0 `max` ((width-title_width)) / 2 - height" y="(height-mini_icon_height)/2 + 1" width="mini_icon_width" height="mini_icon_height" alpha="1"/>
  		<title color="shade/gtk:bg[SELECTED]/0.7" x="5 `max` (width-title_width)/2+1" y="1 `max` ((height-title_height)/2)+1"/>
  		<title color="gtk:fg[SELECTED]" x="4 `max` (width-title_width)/2" y="0 `max` ((height-title_height)/2)"/>
</draw_ops>

<draw_ops name="title_unfocused">
  		 <icon x="0 `max` ((width-title_width)) / 2 - height" y="(height-mini_icon_height)/2 + 1" width="mini_icon_width" height="mini_icon_height" alpha="0.7"/>
  		<title color="shade/gtk:bg[NORMAL]/0.8" x="4 `max` (width-title_width)/2" y="0 `max` ((height-title_height)/2)"/>
</draw_ops>
```

---

### Post by hezral on 2006-06-04
thanks I'll try that too

---

### Post by hezral on 2006-06-05
hmm.. i tried putting the codes in post #2 but the theme wont display at all..can you try it to the theme i posted or maybe post the theme xml?

---

### Post by bvc on 2006-06-05
[http://kwh.kernow-gb.com/~bvc/theme/devel/Clearbox-look-2.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/devel/Clearbox-look-2.tar.gz)

---

### Post by hezral on 2006-06-06
thanks bvc. i'll try it when i get home. btw nice themes you got on your homepage.

---

### Post by bvc on 2006-06-06
Thank you! If you don't know, have have much more [here]("http://www.gnome-look.org/usermanager/search.php?username=bvc")

---

### Post by hezral on 2006-06-06
ok it worked. but the one you gave had both the icon and the arrow button. i already edit it to show the icon only. thanks a lot!! i'll check your other themes too.

---

### Post by bvc on 2006-06-07
the first post will only put the app icon in place of the menu button

the second was to leave the menu button in the menu position and put the app icon with the title

glad you figured it out!

---

