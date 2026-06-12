---
title: "Flux like window borders in Gnome?"
date: 2006-06-19
forum: Art &amp; Design
---

### Post by DR_K13 on 2006-06-19
I am looking for minimalistic border  theme for gnome. Almost no boarder or none at all, I have seen a few people running gnome with it, anyone know how to find it or make it?  here is an example of the " minimal borders" that I like/  Granted I do use both flux and gnome. 

Thanks

---

### Post by bvc on 2006-06-19
hmmm.....there are no borders on that screen shot. Maybe what you have seen is people running flux and openbox instead of metacity? I recently made [nm156]("http://kwh.kernow-gb.com/~bvc/wp/?p=31") to go with rezlooks, based on rezza's screenshot with an openbox theme.

---

### Post by DR_K13 on 2006-06-19
I did see lack of borders in metacity... yet I cant find the screenshot right now. :mad: 

I do like  the Rezlooks GTK Engine and your borders for it. Do I just install it like a regular window border theme?8-)

---

### Post by bvc on 2006-06-19
yes, install any nm156 the normal way

i remember a borderless metacity posted at gnome-look.org but I don't recal its name, and for some reason think the author removed it from gnome-look because of the reaction

is that what you want? no border? at all where you have to use the keyboard only? I can whip that up pretty quick (I think), and after nm156 was thinking of a very small border on top, none on sides and bottom, with buttons much like a ion? theme I saw recently. Does that interst you?

---

### Post by bvc on 2006-06-19
Nothing Metacity
[http://www.gnome-look.org/content/show.php?content=32164](http://www.gnome-look.org/content/show.php?content=32164)

---

### Post by DR_K13 on 2006-06-19
[QUOTE=bvc]yes, install any nm156 the normal way

i remember a borderless metacity posted at gnome-look.org but I don't recal its name, and for some reason think the author removed it from gnome-look because of the reaction

is that what you want? no border? at all where you have to use the keyboard only? I can whip that up pretty quick (I think), and after nm156 was thinking of a very small border on top, none on sides and bottom, with buttons much like a ion? theme I saw recently. Does that interst you?[/QUOTE]


Yup, whats what I am looking for.  i think I saw it on gnome-look at one time too. I wonder why he took it down?

---

### Post by DR_K13 on 2006-06-19
[QUOTE=bvc]Nothing Metacity
[http://www.gnome-look.org/content/show.php?content=32164](http://www.gnome-look.org/content/show.php?content=32164)[/QUOTE]



WTF lol   ,  is that for real?

---

### Post by bvc on 2006-06-19
what do you mean? I thought that's what you wanted #-o

---

### Post by DR_K13 on 2006-06-20
[QUOTE=bvc]what do you mean? I thought that's what you wanted #-o[/QUOTE]


Well its perfect except I still use the mouse and need a top bar. :-\"

---

### Post by bvc on 2006-06-20
then, unlike your screenshot above, produce one that is accurate or try to give a better explaination because....
[QUOTE=DR_K13]Almost no boarder or none at all[/QUOTE]

[QUOTE=bvc]is that what you want? no border? at all where you have to use the keyboard only?[/QUOTE]
[QUOTE=DR_K13]Yup, whats what I am looking for[/QUOTE]

---

### Post by DR_K13 on 2006-06-20
[QUOTE=bvc]then, unlike your screenshot above, produce one that is accurate or try to give a better explaination because....[/QUOTE]

No side or bottom border, BUT I do need a top border. ](*,)

---

### Post by bvc on 2006-06-20
I don't know a theme that does that but it is easy to do. Open the metacity theme xml file and edit (nm156 for example);
<distance name="left_width" value="3"/>
<distance name="right_width" value="3"/>
<distance name="bottom_height" value="3"/>
to
<distance name="left_width" value="0"/>
<distance name="right_width" value="0"/>
<distance name="bottom_height" value="0"/>

and do this for each <frame_geometry name=>

That probably won't speed up the theme though. It gets a lot more involed to accomplish that.

---

### Post by DR_K13 on 2006-06-21
[QUOTE=bvc]I don't know a theme that does that but it is easy to do. Open the metacity theme xml file and edit (nm156 for example);
<distance name="left_width" value="3"/>
<distance name="right_width" value="3"/>
<distance name="bottom_height" value="3"/>
to
<distance name="left_width" value="0"/>
<distance name="right_width" value="0"/>
<distance name="bottom_height" value="0"/>

and do this for each <frame_geometry name=>

That probably won't speed up the theme though. It gets a lot more involed to accomplish that.[/QUOTE]


Thanks !!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by cpbl on 2006-07-26
What about a way to toggle decoration on a given window, like you can do in KDE? It's nice to have a theme with borders, titles, etc... but when I don't need them I'd like to be able to toggle them off.
This is my favourite missing feature so far in Gnome (metacity)...
Can you do that too??

---

### Post by bvc on 2006-07-26
no

---

