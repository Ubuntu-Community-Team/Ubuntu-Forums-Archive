---
title: "decent full screen magnifier?"
date: 2008-09-27
forum: Assistive Technology &amp; Accessibility
---

### Post by noeyewar on 2008-09-27
hey out there.

is there a decent working full screen magnifier for ubuntu?

i am used to using zoomtext on windows (between 6-10 x magnification) but i would like to try out ubuntu.

i have tried the standard beryl zoom functionality before, but the picture quality became very crappy when using high magnifications, and it is very confusing the way the "zoomed area" follows the mouse pointer. 

so is there any good magnifiers that can be used with ubuntu?

thnaks

---

### Post by Sef on 2008-09-27
What is your operating system?

---

### Post by ronnielsen1 on 2008-10-19
Try the shortcut keys [COLOR=Red]control[/COLOR] and [COLOR=Red]+[/COLOR] (Press it more for bigger - [COLOR=Red]control -[/COLOR] for smaller)

works on all OS's I think

---

### Post by RKCole on 2008-11-15
Hello, noeyewar.

I as a former ZoomText user back when I used Windows, over a year and a half ago now.  I now use Ubuntu 8.04 ("Hardy Heron") with Compiz Fusion and its Enhanced Zoom plug-in.  This works very well with fullscreen magnification, and it does not seem to make a very large footprint on my system hardware whatsoever.  You can access the Enhanced Zoom features through an application called compizconfig-settings-manager (ccsm).

If you would like an alternative to this, try hitting AL%+F2 to open the Run Application dialog box, type in the following:

```

magnifier -fmz [zoom level]

```

Then press ENTER to start the GNOME Magnifier.  I tried it at 16x just now and it seemed to work just fine.

Now, to kill this, you would want to do the following:  1) hit ALT+F2 to open the Run Application dialog box, 2) type 

```

killall magnifier

```

and 3) hit the ENTER key to kill the magnifier.

Hope this helps you out some. 
Take care.

---

