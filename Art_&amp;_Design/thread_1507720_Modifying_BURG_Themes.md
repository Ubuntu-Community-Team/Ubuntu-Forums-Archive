---
title: "Modifying BURG Themes"
date: 2010-06-11
forum: Art &amp; Design
---

### Post by techunit on 2010-06-11
Hi I would like to modify the BURG Theme Sora to have the Ubuntu 10.04 Default background and change the Ubuntu Icons to the newer looking one that came with 10.04 as well. I have the icons and and they have been saved to the proper size and format (*.png) 

I found that the themes under 
```
 /boot/burg/themes/ 
```I then copied the sora relevant folders to a different location where I renamed the folders (This was the only way I found to name the theme and apparently it worked.) 

I then created the icons for ubuntu, and copied over the default background for ubuntu and renamed it "background.png"

The result was less than hoped. I hoped that I would get what I wanted but unfortunately I did not. I instead got a black background and no new icons. I hope someone with more experience could help me with this.

In a last ditch attempt to change the sora themes ubuntu icon I replaced them with my new ones. Unfortunately this didn't work.

Thanks for any help you can provide it would be much appreciated.

---

### Post by techunit on 2010-06-12
bump...

---

### Post by techunit on 2010-06-12
I seriously hait doing this but I really need help with this. so bump...

---

### Post by techunit on 2010-06-12
ah... bump? Really no one knows how to do this. Sorry if I am doing this excessively but I have not gotten any responces to my last 4 threads not one.

---

### Post by 23dornot23d on 2010-06-13
Try here [Burg]("http://ubuntuforums.org/showthread.php?t=1402375")

---

### Post by Xgen on 2010-06-15
If I was going to modify a theme, I would copy that theme and rename it (example: sora_modified), make my changes and then do from the terminal:sudo update-burg to write the changes to the burg.cfg file.

---

### Post by HoKaze on 2010-06-16
As stated by Xgen, the best way of customising BURG themes (if you actually want to keep the changes when updating BURG) is to copy it to something like sora_mod and do your changes there.
Also, if I recall correctly, one of the updates for BURG a good few months ago did a massive re-haul of the icons (which before were limited and supported only a few distros and OSes). Because of this, all the themes now look in /boot/burg/themes/icons, even the sora-based themes. Try editing these or manually editing the theme file in the sora_mod folder to point to the icons folder within sora_mod.

If you need more help try looking around the BURG forums:[http://www.burgloader.com/bbs/](http://www.burgloader.com/bbs/)
Bean (the creator of BURG) is very active there and willing to help.

---

### Post by YtiDilav on 2011-03-01
I modified a theme and also got a black background. I did some experimenting, and found that BURG is particular about PNG's. Firefox will freely display all sorts of image files. But, BURG seems to need a very specific format.

I ran the pngcheck tool, which said my background was not actually a PNG. But, it had a .png file name extention, and firefox said it was a PNG.  So, i ran an imagemagick tool to convert it. Now, pngcheck said it was an ok PNG, but it still displayed as black in the BURG boot menu.  So, i ran pngcrush on my file, and finally BURG was able to display it.

This is really cool. Instead of paying for a commercial boot loader with a fixed interface, I can create my own boot interface for free.  :-)

---

### Post by Copper Bezel on 2011-03-02
Like Plymouth's .png files, I assume that it really is a .png, but it's indexed.

The simplest way to avoid this problem would be to copy an existing Burg theme backdrop, open GIMP, drop your new image in as a layer, and save it. That way, all the indexing information from the original image is unchanged.

---

### Post by cecilpierce on 2012-02-28
Anyone know how to modify the theme file to get two columns side by side instaed of going straight down ?

I have more OS's in the list then will fit vertically.

---

### Post by cecilpierce on 2012-02-29
added a screen shot

---

### Post by hal8000 on 2012-04-07
With addition of icons, Burg is similar to Grub2 in many ways.

The os-prober script in Grub2 fails to identify most of my linux partitions, and also fails in Burg also.

Looking at your screenshot, some icons do not match the linux distro, so it may have failed to identify all of your distros.

Each burg theme is stored in /boot/burg/themes under own theme name.
If you look at the Burg theme in /boot/burg/themes/burg, you will
see it has
wallpaper.png
theme
orb.png
progressbg.png


The structure of the theme file looks in parts very similar to the grub2
theme file outlined here:

[http://www.gnu.org/software/grub/manual/html_node/Theme-file-format.html#Theme-file-format](http://www.gnu.org/software/grub/manual/html_node/Theme-file-format.html#Theme-file-format)

More help here:
[https://help.ubuntu.com/community/Burg#Basic_Structure](https://help.ubuntu.com/community/Burg#Basic_Structure)


I've not managed to alter this myself, but you should be able to change the wallpaper on one of the set themes this way.

If you have corrupt entries, easy way is to disable os-probe in /etc/defaults/burg and add custom entries to /etc/burg.d/
Scripts start in order so 40_custom is run before 41_custom.
Make sure scripts are executable.

Hope that helps.

---

