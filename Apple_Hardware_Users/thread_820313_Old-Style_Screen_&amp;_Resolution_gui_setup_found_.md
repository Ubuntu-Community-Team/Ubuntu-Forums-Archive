---
title: "Old-Style Screen &amp; Resolution gui setup found in Hardy!"
date: 2008-06-06
forum: Apple Hardware Users
---

### Post by stream303 on 2008-06-06
Wow.  Thanks to Philinux in this thread, I didn't realize that the pre-hardy gui configuration tool for graphics cards and screen resolution is still available - it is just hidden in Gnome now.  With the new xorg server I suppose this utility is definitely deprecated, but I was surprised to see it.

[http://ubuntuforums.org/showthread.php?t=817611](http://ubuntuforums.org/showthread.php?t=817611)

Basically, you go into System > Preferences > Main Menu, and in the left-hand pane highlight "Other".  To the right, enable "Screens and Graphics".  Now under your Applications menu, "Other" will show up and you can now fire up the old-style of video / screen configuration gui.

***** WARNING *****:  I have only enabled this, but not fully tested it on my G5 iMac.  I have no idea about how the integration works with the newer style of screen configurations is (System > Prefs > Screen Resolution).  If you do play with this, backup your existing xorg.conf ! :)

One thing that is VERY interesting is if you look under the Apple display menus, you can see a nice wide range of horizontal and vertical sync settings for various popular PPC models.  So even if this utility doesn't work, you have a nice reference for what values to use for a manual edit of xorg.conf if it comes to that.  Most of the values seem to agree with the various threads and wikis.

Again, I have not tried this on my Hardy PPC box, only enabled it to look around.  YMMV!

---

### Post by avtolle on 2008-06-06
Oops! Thought I'd posted about this a while back when I found it, but guess either I didn't or it didn't take. I used it to "tweak" one of my Cubes' displays, and it worked very well for me. As posted above, YMMV, but for me, it definitely seemed to work, and work well.

---

### Post by avtolle on 2008-06-06
And, if you want to get there directly without messing with editing the menu, or going to the menus, at the terminal```
sudo displayconfigure-gtk
``` will get you into the application.

---

### Post by stream303 on 2008-06-06
That's great!  Actually I had to use:
```
sudo displayconfig-gtk
```

That is a great tip since I have often found myself in weird resolutions where you can't get to the "apply" or "ok" buttons to make any changes. :)

---

### Post by avtolle on 2008-06-06
> **stream303 said:**
> That's great!  Actually I had to use:
```
sudo displayconfig-gtk
```That is a great tip since I have often found myself in weird resolutions where you can't get to the "apply" or "ok" buttons to make any changes. :)
It is "sudo displayconfig-gtk". I guess my brain got ahead or behind or otherwise out of sync with my fingers. :-( Thanks for catching that, stream303.

---

### Post by avtolle on 2008-06-06
Since I posted about my "tweaked" /etc/X11/xorg.conf file created using Screens and Graphics, it might be good to look at for an example of the changes made to said file by the application over the "stub" file generally created.

---

### Post by cyberdork33 on 2008-06-06
that tool always seemed to do more bad than good for the Intel folks.

---

### Post by stream303 on 2008-06-06
The catch-22 for some PPC'ers is that sometimes you can't even get an X gui going to get to the utility, without editing your xorg.conf first. :)

---

### Post by avtolle on 2008-06-06
> **stream303 said:**
> The catch-22 for some PPC'ers is that sometimes you can't even get an X gui going to get to the utility, without editing your xorg.conf first. :)
That is so true, stream303. That's why I've got a copy of an old one laying around for reference, should I need to edit.

---

