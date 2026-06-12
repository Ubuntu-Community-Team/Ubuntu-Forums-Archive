---
title: "Default Font"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-12-21
The font in both of my Ubuntu machines are less than perfect.  The have rough edges which looks  poor compared to those in XP. I've tried all of the combinations in System > Preferences > Fonts but can't seem to get the results I expected.  The font selected as default is Sans and Sans Bold.  Can anyone recommend a font or some other way I can improve the way fonts appear please. Antialiasing doesn't seem to help

---

### Post by logos34 on 2006-12-21
$ sudo apt-get install msttcorefonts

read through this:
[http://avi.alkalay.net/linux/docs/font-howto/Font.html#freetype](http://avi.alkalay.net/linux/docs/font-howto/Font.html#freetype)

In theory Tahoma font (windows menus) seems to be the key here, but actual results are mixed.  I've never been able to approach windows font rendering using tahoma in linux (I did in KDE, but that was in Suse 10.1).  

I prefer gnome desktop, and after fiddling with the fonts and sizes I went back to default sans.  

You can try adjusting the sharpness in your video card display settings.  That helps a little.

---

### Post by logos34 on 2006-12-21
and another link with nice pictures of kde with ms fonts in SUSE:

[http://en.opensuse.org/Optimal_Use_of_Fonts_on_SuSE](http://en.opensuse.org/Optimal_Use_of_Fonts_on_SuSE)

---

### Post by a.v.l on 2006-12-22
> **logos34 said:**
> $ sudo apt-get install msttcorefonts

read through this:
[http://avi.alkalay.net/linux/docs/font-howto/Font.html#freetype](http://avi.alkalay.net/linux/docs/font-howto/Font.html#freetype)

In theory Tahoma font (windows menus) seems to be the key here, but actual results are mixed.  I've never been able to approach windows font rendering using tahoma in linux (I did in KDE, but that was in Suse 10.1).  

I prefer gnome desktop, and after fiddling with the fonts and sizes I went back to default sans.  

You can try adjusting the sharpness in your video card display settings.  That helps a little.

Thanks for your help, I've just discovered by changing to a darker theme it seems to have improved matters, I'll study your advice and see what I can come up with. I just need to find out how to adjust my Nvidia card settings now.  Can't seem to find anywhere to do this.:-k

---

### Post by bapoumba on 2006-12-22
This may not be what you are actually looking for, but check this thread :
[http://ubuntuforums.org/showthread.php?t=4456&highlight=fonts.txt+smooth]("http://ubuntuforums.org/showthread.php?t=4456&highlight=fonts.txt+smooth")
I have been using that for a long while now ;)

---

### Post by logos34 on 2006-12-22
You got me worrying about fonts again!  

Just came across this:
[http://www.ubuntuforums.org/showthread.php?t=208396&highlight=font](http://www.ubuntuforums.org/showthread.php?t=208396&highlight=font)

and it's a DEFINITE improvement.  You have msttcorefonts, so now just get that fontconfig.tbz file.  

I restarted and changed Application font back to Tahoma and rendering is visibly improved.  Tweaked size to 8.5 (8 too small and 9 too big) and now it looks pretty sharp!

Bold highlighted url links in firefox still a tad blurred but otherwise better.

---

