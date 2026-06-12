---
title: "how to: appearance settings - icons - themes"
date: 2010-10-14
forum: Art &amp; Design
---

### Post by Claus7 on 2010-10-14
Hello,

with this tutorial we want to customise our ubu box with the icons we want (more or less). Here I'll describe some steps I took in order to fit things to my liking.

I wanted to use an icon theme, which will have distinct folder icons for pictures, videos e.t.c., will have a marine-blue flavour and use a specific icon for the applications main menu in the top panel of my Desktop.

The theme that appealed most to my liking was Humanities-G, which can be downloaded from [COLOR="YellowGreen"]gnome look org[/COLOR].

Installing this theme I wanted to change the applications icon as well as to make more blue-ish the colour of the folders available.

[SIZE="5"]**Step 1** create applications icon[/SIZE]

This was not easy at all since I had to choose an icon with the right dimensions and the right extension so as to become the new applications icon. In order to achieve that I acquired a *start-here.[COLOR="DarkOrange"]png[/COLOR]* file from another theme (usually under **places->24** or places->24x24 inside the theme's folder).

I installed Inkscape from synaptic, opened this png file as embed and saved it as a *start-here.[COLOR="Red"]svg[/COLOR]* file. 

[SIZE="5"]**Step 2** moving applications icon[/SIZE]

Then I transferred this file under /home/user_name/.icons/Humanities-G2/places/24

(the initial Humanities-G theme was installed and existed in **.icons** folder, so the tampered directory theme was a copied one, just adding in the end of the folder's name number 2)

[SIZE="5"]**Step 3** creating a new theme with the new icon[/SIZE]

Doing so I also changed the name of the theme in file index.theme
> [Icon Theme]
Name=Humanities-G2
matching the one I gave to the folder of that new theme.

Finally that folder was compressed with the options **.tar.bz2** and saved to Desktop.

[SIZE="5"]**Step 4** changing folder's colour[/SIZE]

In order to do so I had to install the [COLOR="RoyalBlue"]MagIcons[/COLOR] program and while opening to choose the Humanities-G2.tar.bz2 file from my Desktop.

There I had the options to tamper with many colour schemes so as to fit my needs. When I finished I clicked on apply and the new theme was ready to go. 

Regards!

PS: Icon themes can be found also under /usr/share/icons yet these are better not to be tampered.
PS2: This took place on ubuntu 10.10 64bit, yet I do not thing that it makes any difference for other versions as well.
PS3: Rebooting your system after all these steps would be a nice idea. Also the theme would be nice to be selected under appearance, before someone chooses to change the colour. After that, under Appearance->Icon the option magicons should be selected

---

### Post by Claus7 on 2010-10-15
Hello,

what we want to do:
[COLOR="DarkOliveGreen"]we want to change the gdm login screen in ubuntu maverick 10.10.[/COLOR]

In the old days some clicks away were enough so as to change this option. Now, there is the ability for some tweaking, yet it is a little bit harder.

I wanted to create a nice login screen [COLOR="Teal"]combining also two pics[/COLOR] on one, the one above the other, in such a way so as to have a landscape as the background and ubuntu logo as the layer above it.

Download a wallpaper that you like, having in mind to have the resolution you want (here 1280x1024). In case you cannot find one the:
```
convert input.jpg -resize 1280x1024 output.png
``` will most of the times do the work. If your image has resolution that cannot be converted to the one you want, then the crop option is a nice idea. Also point that the image you have to create should be a png one (I did not test other format).

Now, since you have the wallpaper you want, you might want to add some "features" as well. Open the image with gimp and in order [COLOR="Olive"]to add a new image[/COLOR] choose from File the option **Open as Layers**. That way browse to the image of your choice and add it in the centre of your wallpaper. 

From the Layer options you will be able to scale your new inserted image and from the gimp panel the move tool (cross with triangles in the edges) will place your image where you want.

Now save as this file as a png following the easy steps of the windows that will appear and you have created your merged image.

Now, place it under /usr/share/backgrounds/ and with [COLOR="Purple"]ubuntu tweak[/COLOR] place it as your new login screen. And you are set!

Regards!

---

