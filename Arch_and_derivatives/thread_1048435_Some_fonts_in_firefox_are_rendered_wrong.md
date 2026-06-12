---
title: "Some fonts in firefox are rendered wrong"
date: 2009-01-23
forum: Arch and derivatives
---

### Post by andrek on 2009-01-23
I'm running Archlinux with pekwm.
Here's my .Xdefaults file :
```
Xft.antialias:true
Xft.dpi:96
Xft.hinting:false
Xft.hintstyle:hintnone
Xft.rgba:none
Xcursor.theme: Human
```
( no hinting since I like more osx-like blurred fonts )

The fonts are generally looking great, except for some microsoft(?) ones on few web pages. I've tried reinstalling ttf-ms-fonts with no results. Any ideas?

[[img]http://f.imagehost.org/t/0194/fonts.jpg[/img]](http://f.imagehost.org/view/0194/fonts)

---

### Post by gjoellee on 2009-01-23
That happens to me as well :(

---

### Post by fwojciec on 2009-01-23
This site works fine for me.  This is my ~/.fonts.conf:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  
  <!-- Additional font directories -->
  <dir>~/.fonts</dir>

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
      <const>lcddefault</const>
    </edit>
  </match>

</fontconfig>
```
And this is what I have in /etc/fonts/conf.d directory:
```
> ls -l /etc/fonts/conf.d  
total 4.0K
lrwxrwxrwx 1 root root  35 2009-01-20 17:39 10-sub-pixel-rgb.conf -> ../conf.avail/10-sub-pixel-rgb.conf
lrwxrwxrwx 1 root root  39 2009-01-20 17:39 20-fix-globaladvance.conf -> ../conf.avail/20-fix-globaladvance.conf
lrwxrwxrwx 1 root root  39 2009-01-20 17:39 20-unhint-small-vera.conf -> ../conf.avail/20-unhint-small-vera.conf
lrwxrwxrwx 1 root root  42 2009-01-20 17:39 29-replace-bitmap-fonts.conf -> ../conf.avail/29-replace-bitmap-fonts.conf
lrwxrwxrwx 1 root root  36 2009-01-20 17:39 30-metric-aliases.conf -> ../conf.avail/30-metric-aliases.conf
lrwxrwxrwx 1 root root  33 2009-01-20 17:39 30-urw-aliases.conf -> ../conf.avail/30-urw-aliases.conf
lrwxrwxrwx 1 root root  30 2009-01-20 17:39 40-nonlatin.conf -> ../conf.avail/40-nonlatin.conf
lrwxrwxrwx 1 root root  27 2009-01-20 17:39 45-latin.conf -> ../conf.avail/45-latin.conf
lrwxrwxrwx 1 root root  31 2009-01-20 17:39 49-sansserif.conf -> ../conf.avail/49-sansserif.conf
lrwxrwxrwx 1 root root  26 2009-01-20 17:39 50-user.conf -> ../conf.avail/50-user.conf
lrwxrwxrwx 1 root root  27 2009-01-20 17:39 51-local.conf -> ../conf.avail/51-local.conf
lrwxrwxrwx 1 root root  27 2009-01-20 17:39 60-latin.conf -> ../conf.avail/60-latin.conf
lrwxrwxrwx 1 root root  35 2009-01-20 17:39 65-fonts-persian.conf -> ../conf.avail/65-fonts-persian.conf
lrwxrwxrwx 1 root root  30 2009-01-20 17:39 65-nonlatin.conf -> ../conf.avail/65-nonlatin.conf
lrwxrwxrwx 1 root root  29 2009-01-20 17:39 69-unifont.conf -> ../conf.avail/69-unifont.conf
lrwxrwxrwx 1 root root  31 2009-01-20 17:39 80-delicious.conf -> ../conf.avail/80-delicious.conf
lrwxrwxrwx 1 root root  31 2009-01-20 17:39 90-synthetic.conf -> ../conf.avail/90-synthetic.conf
-rw-r--r-- 1 root root 959 2008-07-06 18:06 README
```

Also, in case you have these installed, you should try removing xorg-fonts-75dpi and xorg-fonts-100dpi packages.

---

### Post by andrek on 2009-01-23
Removing xorg-fonts-75dpi and xorg-fonts-100dpi solved the problem.
Thanks a lot!

---

### Post by K.Mandla on 2009-01-24
As a side note, I sometimes get this as well, but it's only in non-Western fonts like kanji, hiragana, katakana, etc. I use the precompiled Firefox package from Mozilla, and it does it in Arch and Crux both.

---

### Post by handy on 2009-01-26
I get it occasionally also.

I thought it was due to my having all of Firefox's fonts set to 24 points for use on the 24" screen, as sometimes decreasing the font size using the hot keys, will solve the problem.

---

### Post by fuuf on 2009-01-26
I've noticed this aswell, only on xkcd though. anyway, I took the less conventional method and just just changed the fonts with stylish :P

---

