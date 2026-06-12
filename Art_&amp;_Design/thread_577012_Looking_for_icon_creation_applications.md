---
title: "Looking for icon creation applications"
date: 2007-10-15
forum: Art &amp; Design
---

### Post by obis666 on 2007-10-15
Hi I'm looking for icon creation/design apps, I have tried babygimp and gnome icon editor. I get this error when I run babygimp:

Name "Load::VAR1" used only once: possible typo at /usr/bin/babygimp line 6874.
Scanning plugins ... loading 0 plugins ... done
Can't coerce CODE to string in entersub at /usr/lib/perl5/Tk/Widget.pm line 190.
 at /usr/bin/babygimp line 575
 at /usr/lib/perl5/Tk/Widget.pm line 191
        Tk::Widget::new('Tk::Radiobutton', 'Tk::Frame=HASH(0x88bc7a0)', '-text', 'Erase', '-value', 'CODE(0x84fa664)', '-pady', 0, '-variable', ...) called at /usr/lib/perl5/Tk/Widget.pm line 256
        Tk::Widget::__ANON__('Tk::Frame=HASH(0x88bc7a0)', '-text', 'Erase', '-value', 'CODE(0x84fa664)', '-pady', 0, '-variable', 'REF(0x84f6b14)', ...) called at /usr/bin/babygimp line 575
 at /usr/bin/babygimp line 575

I have perl and perl tk installed also I followed the instructions on the babygimp site, it said to install ImageMagick or Netpbm, I did both. No dice. I googled this problem and it seems many other ubuntu users seem to have this problem with no solutions noted.

And Gnome icon editor just does not have the quality I need. Does anyone know where to point me? Maybe to a tutorial or just some quality apps (open source) that I can use to make professional looking icons.

thank you in advance
-obis

---

### Post by smartboyathome on 2007-10-16
Are you trying to create icons for gnome? I have done just fine with PNGs.

---

### Post by adamorjames on 2007-10-16
> **smartboyathome said:**
> Are you trying to create icons for gnome? I have done just fine with PNGs.

Yeah pngs work for me too. Gimp can make icos.

---

### Post by obis666 on 2007-10-16
yeah I just want to try my hand at making some gnome icon themes. Are you saying that I should use GIMP? I thought there might be a simpler way (like preferably a tool) to resize each image to 9 different sizes. The directories usually have images with these sizes: 16x16 22x22 24x24 32x32 36x36 48x48 72x72 96x96 192x192 and scalable. I cant imagine resizing each icon for every directory. Has anyone here actually made an icon theme? maybe I'm not on the right forum for this.

---

### Post by smartboyathome on 2007-10-16
I have tried it, you might look in my sig at the link about theming. Also, you can use imagemagick to do what you want (though I haven't used it much).

---

### Post by AnRa on 2007-10-16
You may use Inkscape and/or GIMP. ;)

---

### Post by smartboyathome on 2007-10-16
Scalable icons are better done in Inkscape, as they truely are scalable. Also, if you have that type of icon, you really don't need any others.

---

### Post by obis666 on 2007-10-17
> **smartboyathome said:**
> I have tried it, you might look in my sig at the link about theming. Also, you can use imagemagick to do what you want (though I haven't used it much).
Thats really great, and thanks but I am kind of more looking for a way to just make all of my icons once and then run a script or an app so I dont have to deal with manually resizing each image. 

And as far as the other comments I will try inkscape out.

---

### Post by adamorjames on 2007-10-17
Yeah SVG is great. Inkscape for the win! :guitar:

---

