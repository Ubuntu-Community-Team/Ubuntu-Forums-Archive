---
title: "How do you change FOLDER icon to something looking more appealing?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-12-05
Hello Ubuntians.....

I got a couple of folders on my desktop. I don't care too much for the folder icon and was interested in learning how I can change it to something else.

I tried right clicking on the folder icon and choosing "properties". The "basic" tab will appear with the folder icon off to the left. I clicked on it in an attempt to use a jpeg image but it didn't work.

Do I need to convet the jpeg to another format? If so what programs do I need to do this?

Additionally., when I'm in the "basic" tab and have clicked on the folder icon that I want to change a "select Custom Icon" menu pops up. What folder do I need to navigate to in order to change the present icon?

Thanks everyone......

---

### Post by Flyingjester on 2007-12-05
if you're using gutsy it is system > preferences > appearance > customize > icons then you can change the icon theme, or additionally you can go to [www.gnome-look.org](www.gnome-look.org) and download new icon themes, once downloaded assuming they are a .tar you can drag and drop it into the appearance window and it will auto-install, also icons are located in /usr/share/icons

---

### Post by thelatinist on 2007-12-05
Change your icon set in Sytem | Preferences | Appearance | Customize | Icons to change all your folder icons.  You can get lots of them from art.gnome.org or from gnome-look.org.

---

### Post by kelbizzle on 2007-12-06
If you want to make your own theres a great tutorial over at gimp which I've used. With practice they turn out beautifully. Just save them as png's. [http://www.gimp.org/tutorials/Creating_Icons/](http://www.gimp.org/tutorials/Creating_Icons/)

---

### Post by CatKiller on 2007-12-06
> **lentomies said:**
> Hello Ubuntians.....

I got a couple of folders on my desktop. I don't care too much for the folder icon and was interested in learning how I can change it to something else.

I tried right clicking on the folder icon and choosing "properties". The "basic" tab will appear with the folder icon off to the left. I clicked on it in an attempt to use a jpeg image but it didn't work.

Do I need to convet the jpeg to another format? If so what programs do I need to do this?

Additionally., when I'm in the "basic" tab and have clicked on the folder icon that I want to change a "select Custom Icon" menu pops up. What folder do I need to navigate to in order to change the present icon?

Thanks everyone......

This all seems like the right procedure - right-click on the folder, select Properties, click on the current icon, and then select the icon that you want instead. I just tried it with a random JPEG and it worked, so JPEGs aren't a problem per se.

Some images are kept in /usr/share/pixmaps but the folder that you're most likely to be interested in is the folder for your desktop theme. These will be in /usr/share/icons/<ThemeName>. The default icon theme is "Human". The default 100% view in Nautilus uses icons at 48x48, although you might want to use a scalable icon instead in case you want to make your desktop icons bigger.

Otherwise, you can just change icon theme, as has already been mentioned. If you install **gnome-art** ```
sudo aptitude install gnome-art
``` you'll get a tool that will automatically download and install themes from art.gnome.org.

---

### Post by Lothas on 2007-12-07
In windows there's a nice feature for example, for pictures folders that shows some of the pics inside the folder on the icon itself. It's very useful when all the pictures folders have dates on them and you have no clue what's in them. Is there anything like it for Ubuntu?

---

