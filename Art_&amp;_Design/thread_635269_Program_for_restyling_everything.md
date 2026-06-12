---
title: "Program for restyling everything?"
date: 2007-12-08
forum: Art &amp; Design
---

### Post by Jadd on 2007-12-08
Is there a program that restyles your entire OS? I mean you download a pack which includes grub screen, splash screen, gdm, metacity or emerald, icons, fonts, buttons, wallpaper and mouse cursors, and then apply it.
If there isn't one, then someone should make it!

(Discussion moved [here]("http://ubuntuforums.org/showthread.php?t=713952"))

---

### Post by GeorgiaBoot on 2007-12-08
Well I found this one that makes the whole OS look like a Mac.

[http://lifehacker.com/software/how-to/make-your-linux-desktop-look-like-a-mac-317110.php]("http://lifehacker.com/software/how-to/make-your-linux-desktop-look-like-a-mac-317110.php")


It is not 100% accurate but it looks good and changes just about everything.

---

### Post by Jadd on 2007-12-10
Thanks for that link, but I'm looking for something that could do all that... automatically.

---

### Post by smartboyathome on 2007-12-10
You can customize what the whole OS looks like, but not all in one program.

---

### Post by GeorgiaBoot on 2007-12-10
As he said you need a couple different things to customize everything. 

With that one I showed you there are only 3 downloads, you don't need any other software to use it. 

I can give you a heads up if I see any things that are more simple but I think that is the simplest you will get.

good luck

---

### Post by rsambuca on 2007-12-10
sudo apt-get install gnome-art

You will then find the program under "System - Preferences - Art Manager".

It is a tool for downloading and installing Gnome themes and provides a theme list with options to preview, download, and install them.  Backgrounds, themes, icons,  login managers, splash screens, etc.

---

### Post by smartboyathome on 2007-12-10
It doesn't get themes from gnome-look.org though (which I find has a better selection). It gets them from art.gnome.org.

---

### Post by Jadd on 2007-12-12
Thanks, I had tried that before. It's nice, but not what I'm looking for. Say I hate the Ubuntu human brown theme (which I don't). Wouldn't be cool if I could download just one archive, install it in one or two clicks, and then everything would be themed? Everything: metacity or emerald, icons, wallpaper, grub, boot splash screen, gdm login screen, cursors... Everything, in one installation.

---

### Post by rsambuca on 2007-12-12
This is really starting to sound like another of those "I want Ubuntu to be made exactly how I want it" threads.  And who is going to decide which wallpaper goes with which icons and window borders...  Then you just get too many complaints that it isn't flexible enough...

---

### Post by Jadd on 2007-12-13
> **rsambuca said:**
> This is really starting to sound like another of those "I want Ubuntu to be made exactly how I want it" threads.  And who is going to decide which wallpaper goes with which icons and window borders...  Then you just get too many complaints that it isn't flexible enough...
It's not that at all! It's just, I want to make sure it hasn't already been done before I attempt to make this program/script myself.
Hopefully, when I system like this is set up, artists will start making overall looks... Right now, it's great fun going to [gnome-look.org](http://www.gnome-look.org) for metacity, wallpapers, icon sets... but getting a bunch of those that fit together visually is a hassle. So it would be cool if people could easily make groups that match all these togethor.

---

### Post by Hairy_Palms on 2007-12-13
you could always stick it into a package, see my attachment,

EDIT woops,its too big to attach, 
[http://rapidshare.com/files/76365834/totaltheme.deb.html](http://rapidshare.com/files/76365834/totaltheme.deb.html)

---

### Post by Jadd on 2008-01-10
> **Hairy_Palms said:**
> you could always stick it into a package, see my attachment,

EDIT woops,its too big to attach, 
[http://rapidshare.com/files/76365834/totaltheme.deb.html](http://rapidshare.com/files/76365834/totaltheme.deb.html)
That is brilliant. Thank you for that. It's not exactly what I wanted but it proves it's possible. Thanks Hairy palms.

---

### Post by Jadd on 2008-01-12
I've just programmed in a few hours a small GUI for restyling your entire OS at once. Right now it only does the wallpaper, the metacity window borders, the GTK controls, the icons and the GDM login screen. I call it complete-look.

Get the deb and a complete-look archive here:
[http://www.4shared.com/dir/5288885/4089e83e/complete-look.html](http://www.4shared.com/dir/5288885/4089e83e/complete-look.html)

Note: you may need the updated gambas2 runtime dependencies. Get them by adding this source:
```
deb http://azores.linex.org/gambas-other/ gutsy main
```

G2g, talk about it more on monday.

---

### Post by smartboyathome on 2008-01-12
Ok, just wondering, but does it have a way of importing files which contain Wallpapers/Metacity Themes/GTK Themes, or does it just allow you to select each?

---

### Post by Jadd on 2008-01-14
Here's how complete-look works (at its current stage).
You start it by running complete-look.gambas or clicking applications, sytem tools, complete look.
You get a wizard welcoming you:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=56456&stc=1&d=1200334926[/IMG] On clicking next, you have to select a complete-look archive, which is in the .tar.bz2 format. This complete-look pack contains the wallpaper, metacity theme, gtk+ theme, gdm theme and icon set. It also includes a look.ini settings file.
The next step allows to choose whether to install and activate everything, or just some of it. For example, you activate everything but the gdm login screen:
[img]http://ubuntuforums.org/attachment.php?attachmentid=56457&d=1200334926[/img]
The third screenshot shows my screen after the wizard had ended. You can see my theme has changed from the default Ubuntu human to something else. My borders, icons, wallpaper and controls have changed.
[img]http://ubuntuforums.org/attachment.php?attachmentid=56458&d=1200334926[/img]

So as you can see, smartboyathome, you can choose which bits to install, however, a complete-look arhive contains all of metacity theme, gtk+ theme, iconset, wallpaper and gdm login screen. In the future I'd like to add emerald themes, splash screens, boot screens, mouse cursors and sounds.

How's that sound?

---

### Post by smartboyathome on 2008-01-14
Would you happen to also be able to make it compaible with tar.gz? I find it better than tar.bz2. Also, would you happen to be able to open a complete-look file by double clicking on it? If so, you could change the extention of the file by default and then have it open with it.
One more thing: Is there a wizard to export your theme settings as a complete-look file?

---

### Post by Fnubey on 2008-01-14
Think all in all this is a nice and brillant idea, especially designing it like in that wizard style. But: I think it should be possible to alter grubscreen or bootscreens too.
People should do their own choices in how their ubuntu can look like. Maybe this happens to be included in one future releases...

---

### Post by Jadd on 2008-01-14
> **smartboyathome said:**
> Would you happen to also be able to make it compaible with tar.gz? I find it better than tar.bz2. Also, would you happen to be able to open a complete-look file by double clicking on it? If so, you could change the extention of the file by default and then have it open with it.
Like the emerald themes? They have an extension of .emerald and a mime-type of application/x-emerald-theme, even though I'm sure they're actually tarballs of the mime-type application/x-compressed-tar. Should I follow in their footsteps, making a new extension and a new mime-type?
> One more thing: Is there a wizard to export your theme settings as a complete-look file?Not yet, that's a good feature to add, though.
> **Fnubey said:**
> Think all in all this is a nice and brillant idea, especially designing it like in that wizard style. But: I think it should be possible to alter grubscreen or bootscreens too.
People should do their own choices in how their ubuntu can look like. Maybe this happens to be included in one future releases...
Yeah, forgot to add those to the list! People can already do that (I have), but it's not easy to change everything at once, or to find stuff that fits togethor. That's why most people stick with the default look and feel, it's too much hassle to find a grubscreen, bootscreen, GDM login screen, wallpaper, GTK+ theme, metacity theme and icon set that fit togethor aesthatically. With complete-look packs, those woes should be over...

---

### Post by smartboyathome on 2008-01-14
> **Jadd said:**
> Like the emerald themes? They have an extension of .emerald and a mime-type of application/x-emerald-theme, even though I'm sure they're actually tarballs of the mime-type application/x-compressed-tar. Should I follow in their footsteps, making a new extension and a new mime-type?

Yep, that is exactly what I meant. NEW IDEA!!! How about a way to make these settings apply to more than one desktop environment (ie, you can use it to install KDE and GNOME themes to help them integrate)? Integrating ETK and E17 themes would also be useful for me, but it definately isn't necessary right now.

---

### Post by Jadd on 2008-03-03
Hey everybody. I've decided to continue this discussion in the customization section, here:
[http://ubuntuforums.org/showthread.php?p=4445912](http://ubuntuforums.org/showthread.php?p=4445912)

I'm looking forward to hearing your ideas!

---

### Post by CaptainCabinet on 2008-03-03
> **rsambuca said:**
> sudo apt-get install gnome-art

You will then find the program under "System - Preferences - Art Manager".

It is a tool for downloading and installing Gnome themes and provides a theme list with options to preview, download, and install them.  Backgrounds, themes, icons,  login managers, splash screens, etc.

Oo thanks for that. :)

---

