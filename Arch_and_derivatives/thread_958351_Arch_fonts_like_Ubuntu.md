---
title: "Arch fonts like Ubuntu"
date: 2008-10-25
forum: Arch and derivatives
---

### Post by simao on 2008-10-25
Hello!

I switched from Ubuntu due to various reasons, but one thing I really like in ubuntu is how it renders my fonts. I had Sub Pixel Smoothing activated with 96dpi,instaled ms fonts and everything worked just fine

I moved to arch and I instaled freetyp2-ubuntu, libxft-ubunto, cairo-ubuntu and fontconfig-ubuntu, but the font rendering is still awfull. The fonts are too blurry!

Is there any configuration I can use to get my nice ubuntu font rendering back?

Any help would be appreciated

Thank you,
Simao

---

### Post by fwojciec on 2008-10-25
Fonts in Arch are configured by a ~/.fonts.conf file or by linking appropriate config settings from /etc/fonts/conf.avail to /etc/fonts/conf.d.  It is by all means possible to have ubuntu-like fonts in Arch, it's just a matter of configuring them correctly.

Also, you might find this wiki page instesting: [http://wiki.archlinux.org/index.php/Fonts#Fonts_with_LCD_filter_enabled]("http://wiki.archlinux.org/index.php/Fonts#Fonts_with_LCD_filter_enabled")

For reference -- this is what my /etc/fonts/conf.d directory looks like:
```
$ ls -la /etc/fonts/conf.d/
total 4.5K
drwxr-xr-x 2 root root 720 2008-09-29 12:12 ./
drwxr-xr-x 4 root root 168 2008-07-22 13:00 ../
lrwxrwxrwx 1 root root  35 2008-08-31 14:18 10-sub-pixel-rgb.conf -> ../conf.avail/10-sub-pixel-rgb.conf
lrwxrwxrwx 1 root root  39 2008-08-31 14:18 20-fix-globaladvance.conf -> ../conf.avail/20-fix-globaladvance.conf
lrwxrwxrwx 1 root root  39 2008-08-31 14:18 20-unhint-small-vera.conf -> ../conf.avail/20-unhint-small-vera.conf
lrwxrwxrwx 1 root root  42 2008-08-31 14:18 29-replace-bitmap-fonts.conf -> ../conf.avail/29-replace-bitmap-fonts.conf
lrwxrwxrwx 1 root root  36 2008-08-31 14:18 30-metric-aliases.conf -> ../conf.avail/30-metric-aliases.conf
lrwxrwxrwx 1 root root  33 2008-08-31 14:18 30-urw-aliases.conf -> ../conf.avail/30-urw-aliases.conf
lrwxrwxrwx 1 root root  30 2008-08-31 14:18 40-nonlatin.conf -> ../conf.avail/40-nonlatin.conf
lrwxrwxrwx 1 root root  27 2008-08-31 14:18 45-latin.conf -> ../conf.avail/45-latin.conf
lrwxrwxrwx 1 root root  31 2008-08-31 14:18 49-sansserif.conf -> ../conf.avail/49-sansserif.conf
lrwxrwxrwx 1 root root  26 2008-08-31 14:18 50-user.conf -> ../conf.avail/50-user.conf
lrwxrwxrwx 1 root root  27 2008-08-31 14:18 51-local.conf -> ../conf.avail/51-local.conf
lrwxrwxrwx 1 root root  27 2008-08-31 14:18 60-latin.conf -> ../conf.avail/60-latin.conf
lrwxrwxrwx 1 root root  35 2008-08-31 14:18 65-fonts-persian.conf -> ../conf.avail/65-fonts-persian.conf
lrwxrwxrwx 1 root root  30 2008-08-31 14:18 65-nonlatin.conf -> ../conf.avail/65-nonlatin.conf
lrwxrwxrwx 1 root root  29 2008-08-31 14:18 69-unifont.conf -> ../conf.avail/69-unifont.conf
lrwxrwxrwx 1 root root  31 2008-08-31 14:18 80-delicious.conf -> ../conf.avail/80-delicious.conf
lrwxrwxrwx 1 root root  31 2008-08-31 14:18 90-synthetic.conf -> ../conf.avail/90-synthetic.conf
-rw-r--r-- 1 root root 959 2008-07-06 18:06 README
```

And this is my ~/.fonts.conf:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    
  <!-- Additional font directories -->
  <dir>~/.fonts</dir>

  <!-- Enable freetype's new subpixel filter. Currently, only a cairo
  version containing the patches from freedesktop #10301 respects this
  setting. -->
  <match target="font">
    <edit mode="assign" name="lcdfilter">
      <const>lcddefault</const>
    </edit>
  </match>
  
</fontconfig>
```

You might prefer different settings, of course.  For the record -- I'm using the regular *lcd packages (like described in the wiki I linked earlier) rather than *ubuntu packages, but it shouldn't really make a significant difference.

---

### Post by simao on 2008-10-26
Hi,

thank you for your reply.

I don't understand. I installed and reinstalled and uninstalled so many packages and I can't get my fonts like ubuntu. :|

I tried that and everything on [http://wiki.archlinux.org/index.php/Fonts](http://wiki.archlinux.org/index.php/Fonts) and still, nothing.

I guess I'll have to go back to ubuntu just because of the fonts.

Thank you,
Simao

---

### Post by kelvin spratt on 2008-10-26
I don't know what you are doing wrong in Arch but on my system the standard Arch fonts are as good if not better than Ubuntu.

---

### Post by bwhite82 on 2008-10-26
Make sure the package:

ttf-ms-fonts is installed:

> pacman -S ttf-ms-fonts

Then change the settings like you would in Ubuntu, complete with 96dpi.

BTW, no one cares if you "go back to" [insert distro name here]. Use what ever distro works for you.

---

### Post by simao on 2008-10-26
> **Soldierboy said:**
> Make sure the package:

ttf-ms-fonts is installed:



Then change the settings like you would in Ubuntu, complete with 96dpi.

BTW, no one cares if you "go back to" [insert distro name here]. Use what ever distro works for you.

yes I did that but the fonts just seem different from ubuntu, some fonts are too blurry, some are too sharp. :|

I know no one cares about the distro I use, I was just showing my frustration with this issue.

Thank you,
SM

---

### Post by andrek on 2008-10-27
On my Arch machine, *-ubuntu packages do the great job. It looks JUST like on Ubuntu.

---

### Post by kpkeerthi on 2008-10-30
Use the *-ubuntu and [this]("http://launchpadlibrarian.net/17567455/.fonts.conf") fonts.conf

See the maintainers comment [here]("http://aur.archlinux.org/packages.php?ID=17327")

---

### Post by andrek on 2008-10-30
It's my comment, btw :) But yeah, it works great now. In case of any new changes, this .font.conf should still work.

---

### Post by simao on 2008-11-06
yes the fonts look a lot alike like ubuntu's fonts :)

Thank you!

---

### Post by S-DeN on 2008-11-25
Hello, I have installed four *-ubuntu patches and put .fonts.conf in my home. But how I may to configure fonts for CRT monitor, without subpixel antialiasing?

I use this config:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font" >
    <edit mode="assign" name="rgba" >
      <const>rgb</const>
    </edit>
  </match>
  <match target="font" >
    <edit mode="assign" name="hinting" >
      <bool>true</bool>
    </edit>
  </match>
  <match target="font" >
    <edit mode="assign" name="hintstyle" >
      <const>hintslight</const>
    </edit>
  </match>
  <match target="font" >
    <edit mode="assign" name="antialias" >
      <bool>true</bool>
    </edit>
  </match>
  <match target="font">
    <edit mode="assign" name="lcdfilter">
      <const>none</const>
    </edit>
  </match>
</fontconfig>
```

I have replaced **lcddefault** with **none**, but fonts is too bad. How I should to change *.fonts.conf*, that my fonts looked better?

sorry for errors)))

---

### Post by handy on 2008-11-25
The following should be of assistance:

***_[http://wiki.archlinux.org/index.php/Fonts#Fonts_with_LCD_filter_enabled](http://wiki.archlinux.org/index.php/Fonts#Fonts_with_LCD_filter_enabled)_***

---

