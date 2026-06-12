---
title: "I've been working on a dark brown theme..."
date: 2009-04-12
forum: Art &amp; Design
---

### Post by detrate on 2009-04-12
Dark room was a good start... but it didn't quite fit me.  Too much white, the window borders weren't working for me... tabs don't signify that they are selected all that well... but I liked the idea of a dark brown theme.

Getting inspiration from Dark Room, I've been working on this theme I've dubbed EarthyTonez.  It's been evolving, becoming more refined and even has me customizing applications that lack gnome's color scheming profile (like Mozilla's thunderbird lightning calendar extension (by opening the jar and editing the css)).

[[img]http://pics.nexuizninjaz.com/images/mhxph6qlbo9w5n0fzx3_thumb.png[/img]](http://pics.nexuizninjaz.com/viewer.php?file=mhxph6qlbo9w5n0fzx3.png)

It uses slightly modified gnome-wise icons and I've recently begun integrating the 'Dust' window border (where it used to use Human).

I just thought I'd share this with you all and get some feedback before I package something up.

I've been working with dark themes for a while now... starting with blacks, then to dark greys then blues... but they were all too dry and cold.  The brown (which some people like to say reminds them of poop), really keeps you warm by comparison.  Also, white and black show up on it fairly well, so you don't get ~those annoying non-conforming applications~ as often.  Not pictured, I themed my KDE applications to match as well.

The web is a slightly different story because as I said, I've been theming my applications where I can... and that entails changing firefox's background color.  Some web developers neglect to explicitly set the background color, so that leaves pages that were intended to have a white background looking all sorts of bad.

I solved (95% of) this by creating the following global [stylish](https://addons.mozilla.org/en-US/firefox/addon/2108) theme.
```
@-moz-document url-prefix(http://), url-prefix(https://) { body { background-color:#fff; color:#000; } }
```




**DOWNLOAD HERE**: [http://z.nexuizninjaz.com/linux/themes/earthytonez_0.8.tar](http://z.nexuizninjaz.com/linux/themes/earthytonez_0.8.tar)




Anyway, enjoy, let me know your thoughts :).

---

### Post by kayosiii on 2009-04-13
I like it - I am not sure I am ready to leave my charcoal painted world just yet. But it is looking really good

---

### Post by detrate on 2009-04-13
Thanks for the compliment kayosiii :)


I've started to refine the border of dust and blend the colors a little more.

[[IMG]http://pics.nexuizninjaz.com/images/fmr9cqzi2tn44i0jb5kr_thumb.png[/IMG]](http://pics.nexuizninjaz.com/viewer.php?file=fmr9cqzi2tn44i0jb5kr.png)

Here's a taste of KDE (3.5) skinned to match:

[[IMG]http://pics.nexuizninjaz.com/images/bhsb7nxthspjvvnz1c1v_thumb.png[/IMG]](http://pics.nexuizninjaz.com/viewer.php?file=bhsb7nxthspjvvnz1c1v.png)

---

### Post by ninjapirate89 on 2009-04-13
I like it too. I really like dark themes so I use my own modified version of DarkRoom but its nowhere near as nice as yours.

---

### Post by detrate on 2009-04-13
Here's a beta for those interested: [http://z.nexuizninjaz.com/linux/themes/earthytonez_0.7.tar](http://z.nexuizninjaz.com/linux/themes/earthytonez_0.7.tar)

(KDE colors not included)

All licensing is true to the previous authors, it's mostly GPL with the exception of some CC tango based icons.  The 'ubuntu wise' icon set is a fork of the [Gnome Colors (wise)](http://www.gnome-look.org/content/show.php/GNOME-colors?content=82562) icon set.  I've made some slight changes to better match the theme.

---

### Post by Argama on 2009-04-13
Oh!, realy nice. Great job

---

### Post by detrate on 2009-04-14
Here's the kde 3.5 theme to match the KDE applications you may be running inside ubuntu: [http://z.nexuizninjaz.com/linux/themes/earthytonez.kcsrc](http://z.nexuizninjaz.com/linux/themes/earthytonez.kcsrc)

place it in ~/.kde/share/apps/kdisplay/color-schemes/

---

### Post by Orlsend on 2009-04-15
[I]I am Little comfused. Is the first screenshot Gnome or KDE?
[/I]
Edit:

I think it is Gnome,if it is would you please tell me the specs (Like Metacity,GTK,Icon set,wallpaper) Have you thought about a GDM,Usplash,Grub that would Match.

I am really interested in porting the theme to the project **[epidermis]("http://http://epidermis.tuxfamily.org/")**

Your Theme is pure Awesomeness!

---

### Post by s.fox on 2009-04-15
Great looking theme.  You must be really pleased :D

---

### Post by meymen on 2009-04-15
Have difficulty in tonality. I consider the meaning of colors, a new study in this area and should be.

Best re

---

### Post by detrate on 2009-04-15
> **Orlsend said:**
> [I]I am Little comfused. Is the first screenshot Gnome or KDE?
[/I]
Edit:

I think it is Gnome,if it is would you please tell me the specs (Like Metacity,GTK,Icon set,wallpaper) Have you thought about a GDM,Usplash,Grub that would Match.

I am really interested in porting the theme to the project **[epidermis]("http://http://epidermis.tuxfamily.org/")**

Your Theme is pure Awesomeness!

It includes both gnome and KDE 3.5.x -- I run Ubuntu with a few select KDE applications, so I themed them to math.

- Metacity -- with Dust as a base, modifying to my own likings >> forked as Dust Browns
- GTK -- Clearlooks as a base, modifying colors to my own linkings
- Ubuntu-wise -- a fork of Gnome Colors (wise)


I mention this information above and it's all included in the zip.


The wallpaper is called "Sunset Lake" by pepo.  Apparently he's deleted it from his deviant art page, but you can download a copy here >> [3840x1200](http://pics.nexuizninjaz.com/images/x61vnhp99oypoy2lk48a.jpg)

I also used this wallpaper with it for a while to compliment the brown a bit: Wall Henning by blackbeast (possibly nsfw) >> [2560x1024](http://pics.nexuizninjaz.com/images/rtb8k58l1xabjfxf1y62.jpg)



I have not made a GDM, Usplash or Grub theme (yet).  I run dual monitors and would really like to figure out how to theme both of them... but haven't been able to trick GDM into doing it yet.  Even if I lie about my resolution, it stays on my primary.

If anyone has any tips about this, please share.




As for the comment about tonality, I'm not sure I fully comprehend... but I've been using this theme for a few months now after spending time on grey based / blue based themes and I find these colors to jive together much better.  Spend > 8 hours a day with this sorta theme and not only will your eyes be hurting, your mood will be more dull / depressing:

[[IMG]http://pics.nexuizninjaz.com/images/p2ggq9sxeykr59ud5xza_thumb.png[/IMG]](http://pics.nexuizninjaz.com/viewer.php?file=p2ggq9sxeykr59ud5xza.png)


I went to brown for the neutrality and the warmth it's able to bring.  My computing experience has been much calmer since the change and my eyes thank me.

However, if you think you can improve upon this theme, please do, I've released the sources above and would love to see someone make improvements in areas I've overlooked.

---

