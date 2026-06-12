---
title: "d3a themes and Gnome-Apple Icons"
date: 2005-02-18
forum: Art &amp; Design
---

### Post by Campitor on 2005-02-18
Hi:

   I'm using the d3a theme on my computer, but added the Gnome-apple icons.  Most of the icons were nicely changed once I restarted gnome.  But some icons, specially the lock-screen icon, the logout icon and the search for files icons, are still d3a icons.  I've been roaming around the different icon folders to compare names, and the only solution I've come up with is to change (replace) the d3a stock-icons with the apple ones...but I really do not want to modify an original (and really good) set of icons.

  Is there any way I can change that without modifying the original set?  I've included a  screenshot, and you can see on the middle of the top-panell I have the lock-screen icon in d3a style.  Any suggestions would be greatly appreciated

---

### Post by EndersGame on 2005-02-18
Hey, sorry this isn't about your question.  How did you get your app launcher in the bottom to look like that?

---

### Post by kassetra on 2005-02-18
When you add panel apps, they tend to have their icons "set" ... which means that they do not follow the theme without some tweaking.
   
   To change the lock icon on your panel:
   right click on the lock (if possible)
   left click on properties (if possible)
   change the icon under the basic tab...
   
 If it's not possible to right click on the lock without locking your screen, you will have to edit the special panel file manually. If you need help doing that, pm me.
  
  EndersGame: that's a [gdesklet]("http://gdesklets.gnomedesktop.org/") app.

---

### Post by bvc on 2005-02-18
why not just copy d3a-icons to the desktop and rename it to ...oh...d3a-apple, copy it back to the icons dir and modify it all you want?

FYI: this of course for personal use only. If I remember correctly, milo didn't want his icons released mixed with others, as most designers do not. You could ask though. He is very nice!

---

### Post by kassetra on 2005-02-18
bvc: that's what I do normally, but panel icons can be trickier since they usually set a full path to the icon, and thus, do not change with the themes.

---

### Post by bvc on 2005-02-18
yeah, those have to be changed with an iconrc within the gtk theme, unfortunately.

---

### Post by bvc on 2005-02-18
btw: have you seen his Just Drive icons?
[http://miloszwl.com/porticons.html](http://miloszwl.com/porticons.html)

---

### Post by macewan on 2005-02-18
[QUOTE=EndersGame]Hey, sorry this isn't about your question.  How did you get your app launcher in the bottom to look like that?[/QUOTE]

Looks like the gDesklets [starterbar](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210)

---

### Post by kassetra on 2005-02-18
I like his macmonkies personally... heh.  :)

---

### Post by Yukonjack on 2005-02-18
[QUOTE=kassetra]I like his macmonkies personally... heh.  :)[/QUOTE]

Hehehe, he reminds me of the monkey that was in a computer game back in the xt86 computer days.

---

### Post by kassetra on 2005-02-18
that's probably exactly why I like him... ;)

---

### Post by Campitor on 2005-02-20
I am a bit confuesed :)  ...what Icon set should I modify...the Gnome-apple or the d3a icon set?  If I rename the hole thing, then wont some applications and functions be without an Icon?  I tried to follow your instructions and many menu entries lost their icon (Abiword, search files, etc.)  I went back to the original, d3a-theme with Gnome-Apple icons.  All works, but the before mentioned icons are still displayed in d3a style.  I'll try to manually modify them with Kassetras instructions, or just learn to live with them like that.  

Thanks for all the replies

Camp

---

### Post by kassetra on 2005-02-20
Campitor: did you get my pm?  
 
 I can also probably help you setup your icons so that you have a mix of the gnome-apple & d3a.
 
 Do you still need help?

---

### Post by bvc on 2005-02-20
I just loaded
d3a gtk
Gnome-Apple Icons
and have Gnome-Apple menu icons

from a terminal you can
cd .themes
cp -fr d3a d3a-apple
gconftool-2 -s -t string /desktop/gnome/interface/gtk_theme d3a-apple

and modify the .themes/d3a-apple/gtk-2.0/icons all you want. They have to be the same name. In other words, you have to replace the original with the gnome-apple. The
.themes/d3a-apple/gtk-2.0/gtkrc
calls
.themes/d3a-apple/gtk-2.0/icons/iconrc

---

### Post by Campitor on 2005-02-21
[QUOTE=bvc]I just loaded
d3a gtk
Gnome-Apple Icons
and have Gnome-Apple menu icons

from a terminal you can
cd .themes
cp -fr d3a d3a-apple
gconftool-2 -s -t string /desktop/gnome/interface/gtk_theme d3a-apple

and modify the .themes/d3a-apple/gtk-2.0/icons all you want. They have to be the same name. In other words, you have to replace the original with the gnome-apple. The
.themes/d3a-apple/gtk-2.0/gtkrc
calls
.themes/d3a-apple/gtk-2.0/icons/iconrc[/QUOTE]
 Bvc:
     Thanks for your detailed instructions...as you may already figured out, I'm very new at this and your instructions are helpful.  Thx.  Just three questions:

1.  Did you download the Gnome-apple icons from gnome-look or from milosz webpage...I think they are different versions

2.  In order to change the icon...do I change the lock screen icon (both in panel and in the menu) do I need to change both:  gnome-stock-lockscreen.png and panel-lockscreen.png or just one of them?

3.  Can I modify the .themes/d3a-apple/gtk-2.0/icons/iconrc file so it points to the icon in my Gnome-apple folder?  Or would that just screw things up?

Thanks for all your help

Camp

---

### Post by bvc on 2005-02-21
you are welcome!

> 1. Did you download the Gnome-apple icons from gnome-look or from milosz webpage...I think they are different versionsI got them from
[http://oceanic.wsisiz.edu.pl/%7Eslabosz/index.php?page=pliki2](http://oceanic.wsisiz.edu.pl/%7Eslabosz/index.php?page=pliki2)
I didn't know milo had them

> 2. In order to change the icon...do I change the lock screen icon (both in panel and in the menu) do I need to change both: gnome-stock-lockscreen.png and panel-lockscreen.png or just one of them? I know at least the panel-lockscreen.png, but I'd change both. I never have figure that out. The naming convention and 'how it works' is wacked out and seriously needs revision.

> 3. Can I modify the .themes/d3a-apple/gtk-2.0/icons/iconrc file so it points to the icon in my Gnome-apple folder? Or would that just screw things up? I've never tried, but it may work. You can always change it back. Kinda hard to really screw things up. Just make a bkup of the original iconrc.

---

### Post by Campitor on 2005-02-22
Ok...First of all, Thanks to Kassetra and bvc for all their help...I finnaly got it woriking how I want it.  

I ended up creating a new directory for the theme (so I dont modify the original) and changed the icons that I needed.  BTW, if you edit the iconrc file,  it also works, but a few (actually just one, and it might have been my mistake) icons were not changed....

Now, onto new things.  I really like Ubuntu, but mostly I like it because of this forum.  I specially like the fact that you get to add good points to the people that are very helpfull.  Thx.

Campitor

---

