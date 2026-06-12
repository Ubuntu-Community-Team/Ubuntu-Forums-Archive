---
title: "Remove fonts?"
date: 2008-09-06
forum: Art &amp; Design
---

### Post by c-m on 2008-09-06
I am increasingly using gimp, inkscape and scribus these days. I've noticed there are load of nonsense and useless fonts installed on the system as default. 

How do i remove all these useless fonts and just keep the core ones (required by programs) installed?

That way I can install my own fonts when needed.

Thanks

---

### Post by lyceum on 2008-09-06
to add fonts go to your home folder and create a new one called .fonts. Put your new ones in it. As for getting rid of fonts, I think you have to have root access, so I am not sure.

---

### Post by kenono on 2008-09-06
I know on the KDE font installer (KDE4) that you can remove them from there.

Also you can remove them manually from the /usr/share/fonts directory.

The reason I suggest the method using the font installer is that you can see them there and so make a good judgment on whether you want to keep them on your system or not.

---

### Post by c-m on 2008-09-06
Sorry, forgot to add i'm using Gnome rather than KDE. 

Its just a pain in the *** having to scroll through a load of fonts i don't need in Gimp etc..

---

### Post by AJB2K3 on 2008-09-07
You can use fontmatrix to prevent programs accessing these nonsense fonts that way any system then need them won't be affected.

---

### Post by dazzlindonna on 2008-11-18
This is just about the most frustrating feature I've come across with Ubuntu.  I'm sick of scrolling through endless foreign language fonts in Gimp as well, and I can't seem to find them anywhere, so I can't delete them.  I've tried installing fontmatrix but I get the following error:
Error: cannot install 'libqt4-core'
so, i'm stuck.

It's kind of crazy that there's no built in font manager.  Pulling my hair out.

--- ADDED ---

Whoa! Wait a second. I just realized that all the "foreign" fonts I was seeing in Gimp aren't foreign at all.  If I view them via System / Preferences / Appearance / Fonts, they are regular English language fonts (sawasdee as an example).  But Gimp, in its preview pane, shows those fonts as weird characters.  So...now the problem isn't getting rid of foreign fonts, it's how do I get Gimp to preview them properly?

---

### Post by danf_1979 on 2008-11-20
Why don't just search with aptitude?

This should work, although it shows more packages than just fonts, but its a good start:

```

aptitude search ~i| grep font

```

Then delete those foreign fonts. I have cleaned my system fonts this way.

---

### Post by fallendarling on 2009-06-08
> How do i remove all these useless fonts and just keep the core ones (required by programs) installed?

This solution worked most excellently for me, it is in two parts:

**Part 1: I did the following in terminal, this removed all but one of my fonts which were useless to me:**
"```
sudo apt-get remove ttf-kochi-mincho ttf-kochi-gothic ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ttf-unfonts-core ttf-indic-fonts-core ttf-wqy-zenhei
```"
**[COLOR="DimGray"]Credit to: [http://productivelinux.com/2009/04/22/how-to-remove-unneeded-fonts-in-ubuntu/comment-page-1/#comment-4271](http://productivelinux.com/2009/04/22/how-to-remove-unneeded-fonts-in-ubuntu/comment-page-1/#comment-4271)[/COLOR]**

**Part 2: I did this and removed one font which I think said Japanese in its description, that got rid of the last font which was of no use to me:**
"*use synaptic. Do a search in synaptic for "ttf-" and you'll get of list of font software and the fonts. Mark to uninstal the fonts [you] don't want and click the apply icon.*"
**[COLOR="DimGray"]Credit to fragos here: [http://ubuntuforums.org/showthread.php?t=643315](http://ubuntuforums.org/showthread.php?t=643315)[/COLOR]**

**Part 3: If that doesn't help, there is another suggestion as to how to delete fonts here, however, I did not use this suggestion, and I do not know if it works or not, it was next on my list to try:**
**[COLOR="DimGray"]http://ubuntuforums.org/showthread.php?t=1137188&highlight=remove+fonts%3F+arabic[/COLOR]**

I hope that helps and does not hurt anything (it sure has helped me - formerly when i was using the GIMP i would have to scroll through a long list of font names which ere useless or unusable due to their being of a language foreign to me, sometimes with only Japanese or Chinese or Arabic special characters, etc), and I hope I did not violate any forum rules in this post. I apologize in advance if I did. Thanks.

[[Edit: P.S. If anyone knows what I did wrong which caused my post to be so "wide", please say so, I'd like to edit the post and fix that problem. Sorry about it. Thanks.]]

FD

---

