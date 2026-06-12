---
title: "GNOME feels big."
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Enalia on 2007-03-12
So, my laptop has a resolution of 1280x800.  When I first started using Ubuntu I got the feeling that it was "kiddy" I changed my resolution to what I have now and I guess it helped a bit but really I just got used to it.

I realized today that the reason it seemed kiddy is because everything is so BIG. Does anyone else know what I mean?

I've changed the height of the panel, which helped a lot, it feels to be the appropriate size.  But, well, take gAIM for example.  I can fit 20 buddies on the list at one time. 

Can't really find a specific complaint about GIMP but it too feels made-for-toddler.

And firefox takes up about 1/4 of the screen with it's hugeness. I changed the chrome.css file and now it looks MUCH better.  Is there a similar GLOBAL GNOME css file that I can just fiddle with once and get to work across all of my gnome applications for all time?

If no one can help with that can I atleast be assured that I'm not being whiny, and SOMEONE knows what I mean.

thanks

---

### Post by kelbizzle on 2007-03-12
I know what you mean. It does seem that everything is a bit jumbo. I just turned the resolution up a bit higher.

---

### Post by igknighted on 2007-03-12
I find gnomes icons to be rather small (at least on the panels), almost unusably so.  The desktop ones are rather large, but you can shrink those if you like.  As for Gaim, the reason the lines are so big is because it defaults to include the buddy icons, which tend to be large.  Turn that option off an it will act normally.  Kopete is another AIM like client, it defaults to the smaller line size if you don't want to mess with Gaim.

---

### Post by maniacmusician on 2007-03-12
It may just be the font size that's bothering you. Sometimes that makes a lot of difference. Try lowering that and see how you like it.

---

### Post by tubasoldier on 2007-03-12
I understand what you mean. It is one of the reasons I chose KDE. But it is my own opinion and preference. Go for what you like best. Thats what I say.

---

### Post by Najand on 2007-03-12
Ok... Actually the nice thing about Gnome is that you can configure all parts of it.. There is a tool called "gconf" to do that. Actually another package called "gconf-editor" make it easier to cofigure your Gnome. It  can be easily installed from the  repositories by using the code:
```

sudo apt--get install gconf-editor

```
For example if you want to  change the size of icons:
1. Open a Terminal
2. Use command "gconf-editor"
3. A GUI will open. It looks very similar to Windows Registery Editor.
4. Click on: 
      "/ " ==> "apps" ==>"nautilus" ==> "icon_view" 
5.select the "default zoom level" and change the  key to one of the following:
    * normal
    * smaller
    * small
    * standard
    * large
    * larger
(The dafualt value is standard.)
If you see your desktop, you will find your icons wiill change at the  same tiime you change the  key. If you go through "gconf" keys you will find very interesting  things you  can customize by yourself.

---

### Post by tm0054 on 2007-03-12
Do you have a widescreen laptop that is stuck on 1024x768 resolution (does the screen look big & stretched out?)?

Mine was that way until I downloaded the '915resolution' package from the add/remove programs area (in the advanced area) FOR INTEL GRAPHICS CARDS. I downloaded that package, rebooted and voila my screen was set to 1280x800.

Personally I love the smaller Ubuntu icons - I first tried Linspire and felt like I was using 'My First Windows' because the icons were so huge.

---

### Post by SuSUntu on 2007-03-12
> **maniacmusician said:**
> It may just be the font size that's bothering you. Sometimes that makes a lot of difference. Try lowering that and see how you like it.

This is the thing that always makes the biggest difference for me, though it isn't the only tweak that might impact the 'toyish' look. Default fonts are set to 10 (if I recall correctly) and it makes all of the menus and toolbar items in apps  way too big for a given resolution.

I always set my application font to 8 and the rest to 8 or 9 in Preferences > Font.

---

### Post by enneth on 2007-05-23
... But how to disable the icons in the contact list in Gaim? Cannot seem to find exactly where to do it.

---

