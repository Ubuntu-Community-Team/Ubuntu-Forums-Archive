---
title: "clearlooks 2.0 metacity"
date: 2005-12-18
forum: Art &amp; Design
---

### Post by muchmusic on 2005-12-18
[http://planet.gnome.org/](http://planet.gnome.org/)

has a nice new item posted from clearlooks devs. a metacity clearlooks 2.0! yay, it's pretty.

---

### Post by hartl_vienna on 2005-12-18
It´s great. I like it. Thanks

---

### Post by tseliot on 2005-12-18
It's beautiful! I use it in my dapper in vmwareplayer

---

### Post by bvc on 2005-12-18
[It's also here,]("http://gnome-look.org/content/show.php?content=32659")
[and here.]("http://www.stellingwerff.com/?p=16#comments")

---

### Post by Gnobody on 2005-12-18
Do you guys want a squared version I made?  Well, since Daniel hasn't posted one yet get it below -->

---

### Post by poofyhairguy on 2005-12-19
[QUOTE=Gnobody]Do you guys want a squared version I made?  Well, since Daniel hasn't posted one yet get it below -->[/QUOTE]


Awesome. Thanks a lot. I like that much more!

---

### Post by Gnobody on 2005-12-20
:KS 
I updated the squared version to 2.01 -->

Thanks dude for noticing that, I would have never caught it because I don't shade windows.  *FIXED*

---

### Post by GoA on 2005-12-20
Thanks, this looks so good with clearlooks cairo. :D

---

### Post by dude2425 on 2005-12-20
Squared version is still rounded when you roll up a window.

---

### Post by Gnobody on 2005-12-21
[QUOTE=dude2425]Squared version is still rounded when you roll up a window.[/QUOTE]

*fixed*

---

### Post by dude2425 on 2005-12-21
Still doesn't fit. It's rounded and squared at the same time now. I've hacked up a squared version of the previos clearlooks metacity theme and came across the same problem. I can't seem to remember how to fix it though ATM. I'll have to go back later and see what I did.

---

### Post by bvc on 2005-12-22
```
<draw_ops name="round_bevel_unfocused_shaded">
  <include name="bevel_unfocused"/>
  <!--<include name="corners_outline_top"/>
  <include name="corners_outline_bottom"/>
  <include name="corners_hilight_shaded"/>-
  <line color="shade/gtk:bg[NORMAL]/0.25" x1="5" y1="height-1" x2="width-6" y2="height-1"/>-->
	<line color="shade/gtk:bg[NORMAL]/0.25" x1="0" y1="height-1" x2="width" y2="height-1"/>
</draw_ops>
```

```
<draw_ops name="round_bevel_shaded">
  <include name="bevel"/>
   <!--<include name="corners_outline_selected_top"/>
  <include name="corners_outline_selected_bottom"/>
  -<include name="corners_hilight_shaded"/>
  <line color="shade/gtk:bg[SELECTED]/0.25" x1="5" y1="height-1" x2="width-6" y2="height-1"/>-->
	<line color="shade/gtk:bg[SELECTED]/0.25" x1="0" y1="height-1" x2="width" y2="height-1"/>
```of course for perfection you'd have to do a little more to the focused to get the bottom line right

---

