---
title: "how to theme panels?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by shanike on 2007-05-18
one extremely lame question (ubuGeeks aware):
how am i supposed to theme top and bottom panel?!?
my desktop goes like this

[IMG]http://img296.imageshack.us/img296/2913/win98resdq9.png[/IMG]

and i want my panels to look like this

[IMG]http://gnome-look.org/CONTENT/content-pre1/58216-1.png[/IMG]

what am i supposed to do?! :confused:

---

### Post by chamberlain2006 on 2007-05-18
That is a theme.  You can download themes from various web sites.  Once you have found one you like, go to System>Preferences>Theme, and drag and drop the file into it to install it.

---

### Post by gamer91 on 2007-05-18
for the panels - download an image from gnome art or gnome look, right click on the panel you want to change, the go

Properties>background>background image

and select the image you want.

---

### Post by lazyart on 2007-05-18
Holy High Bandwidth Batman!

Please, smaller pix or attach them to the thread next time.

art.gnome.org and gnome-look.org are two of many places to find themes.

---

### Post by starcraft.man on 2007-05-18
Try this [theme.]("http://www.gnome-look.org/content/show.php/Smoked+Glass+v0.9.5?content=27141") Its called smoked glass, its not exactly like Studio but its similar and dark, I love it. If you don't like that, find another GTK 2 theme on there and download and install it like mentioned above.

Oh and slight warning, if you do want to stay with it, you'll have to fix firefox and openoffice cuz they look somewhat bad with it.... >.>. [Download]("http://www.gnome-look.org/content/show.php/Neutronium?content=46153") this theme and extract, inside are instructions for fixing both.

OH and one final thing, once you get settled on a GTK theme you do like, and want your root programs (time and date for instance and other such apps like update manager) to look the same, you have to copy your themes to be available to root also, that install method is really just for user apps.

This command does that, just paste it in terminal (Applications > Accessories > terminal):

```
sudo cp -r ~/.themes /root
```

Found that a while ago while browsing the forums :)

Edit: BTW, yuck, whoever's desktop it is bleh... why would anyone skin VLC to look like Media Player 11 from windows?

---

### Post by gamer91 on 2007-05-18
> **starcraft.man said:**
>  why would anyone skin VLC to look like Media Player 11 from windows?

Windows users + they like it.

---

### Post by starcraft.man on 2007-05-18
> **gamer91 said:**
> Windows users + they like it.

Well I'm a (former) windows user... I never did really like the theme actually, maybe it was just me. I'd recommend looking at all the other themes you can get rather than imitating Vista/MS products... copying their themes only validates some people's claims that were trying to make Ubuntu something like windows... at least it seems to me >.>.

---

### Post by shanike on 2007-05-18
> **starcraft.man said:**
> 
Edit: BTW, yuck, whoever's desktop it is bleh... why would anyone skin VLC to look like Media Player 11 from windows?

dunno, some idiot ;)

anyway thanks for the code. however, smoked glass is way too smoked for me...
oh yeah, how i come i sometimes get (while installing themes) "invalid file format" warning?

---

### Post by shen-an-doah on 2007-05-18
The theme you're looking at there is the Ubuntu studio theme.

[http://ubuntuforums.org/showthread.php?t=442506](http://ubuntuforums.org/showthread.php?t=442506)

The third post down will tell you how to install the various parts of Ubuntu studio on your normal Feisty install. If you just want the theme, just install "ubuntustudio-theme" (and maybe the icon theme, GDM theme, etc, depending on how much of it you want).

---

### Post by starcraft.man on 2007-05-18
> **shanike said:**
> dunno, some idiot ;)

anyway thanks for the code. however, smoked glass is way too smoked for me...
oh yeah, how i come i sometimes get (while installing themes) "invalid file format" warning?

The theme might be archived with emerald and compiz themes inside... sometimes you have to extract first layer to get to where author separated them. Thus if you point the theme gui to the archive it will read what it knows and not what it doesn't.

Have a look at other themes though, you can even sort them by highest rating (tab in the top right of main window after you select GTK) :) The first few pages were all pretty good.

---

