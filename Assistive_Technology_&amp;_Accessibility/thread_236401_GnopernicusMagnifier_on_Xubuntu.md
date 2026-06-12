---
title: "Gnopernicus/Magnifier on Xubuntu"
date: 2006-08-14
forum: Assistive Technology &amp; Accessibility
---

### Post by RKCole on 2006-08-14
Hello, everyone.

This may be a stupid question, and if so I sincerely apologize as I am quite ignorant when concerning Ubuntu Desktops (GNOME, KDE, Xfce) and accessibility.

My college is going to be participating in a community project in which we will be installing Xubuntu on donated computer systems (which are typically older PCs) and then freely redistributing these systems to students and other individuals who are in need of computer systems.

My Linux class (including myself) will be the support base for those in the community who receive these systems.

I am quite unfamiliar with Xubuntu/Xfce, so I plan on installing the Xubuntu Desktop on my current Ubuntu Dapper (GNOME) installation so that I can get a feel for Xfce without losing my original installation.  My question is this:  Will Gnopernicus (especially the gnome-mag component) work with the Xubuntu distribution?

As I said, this may be a stupid question, but as far as the variety of Linux desktops comes into play, I am very ignorant  I just want to figure this out so that I can hopefully be a strong support person and so that I may be able to help those who receive the donated systems.

Thanks for any input; it is greatly appreciated.

---

### Post by Henrik on 2006-08-15
> **RKCole said:**
> This may be a stupid question, and if so I sincerely apologize as I am quite ignorant when concerning Ubuntu Desktops (GNOME, KDE, Xfce) and accessibility.

It's certainly not a stupid question, but cutting edge access research :)  XFCE is still fairly untested in this regard.

> My question is this:  Will Gnopernicus (especially the gnome-mag component) work with the Xubuntu distribution?

In principle it should work. 

I did some testing but the AT-SPI stuff seems badly broken on edgy today so my results were mixed. I can get gnopernicus to run, but not the magnifier. kmag runs fine, but this does of course not have a cursor tracking feature.

In any case I would recomend using Orca instead of gnopernicus, the new screen reader and magnifier front-end for Gnome and XFCE. It starts fine on Xubuntu and text-to-speech works fine in some applications (like gedit), but not others (like abiword or openoffice). The magnifier part fails for the same reason that the gnopernicus one fails (as it does on gnome for that matter).

XFCE could certainly do with some AT testing and probably some bug reports here and there.

---

### Post by RKCole on 2006-08-16
As soon as I get some time, I'll give it a try on my Ubuntu Dapper installation and see what happens.

I was also wondering...Is the Accessibility Team looking for any new members?  I would like to join and contribute whatever I can to help further Linux Accessibility.  And if so, what would I need in order to be qualified?

Take care.

---

### Post by Henrik on 2006-08-17
Joining the team is easy! (but it should obviously be better documented). I've posted a topic about it [here](http://www.ubuntuforums.org/showthread.php?t=238402) and I'llnhave it set to sticky.

Welcome RKcole!

---

### Post by jasongrieves on 2006-08-21
very cool stuff.  XFCE is based off of GTK so i assume we can load up the at-spi layer?  This needs to be tested and played with.  I had not even thought of this avenue!  Great catch

---

### Post by RKCole on 2006-08-22
I tried out Gnopernicus/Magnifier on Xubuntu this morning, and it looks like it would work.  The only problem is the top panel--this causes some flaw (from what I have seen so far) which distorts/freezes the magnifier.  This was the same problem I had with Ubuntu, but I fixed it by dragging the top panel to the bottom so that there are two bottom panels.  Unfortunately, it does not seem that this will be as easy in Xubuntu.  Once I can find a way to permanently situate the top panel in a position at the bottom of the screen, I'll try to do some more testing.

**Testing Conditions**
This was tested on a xubuntu-desktop install in Ubuntu Dapper.

This was tested with a horizontal split (similar to Windows Magnifier), thus the top panel MUST be placed at the bottom of the screen for optimum performance.

To create the horizontal split (on a 1024x768 resolution) do the following (this assumes the Magnifier is enabled in Gnopernicus):

1)  When at the Gnopernicus main menu, click **Preferences**.
2)  When the Preferences menu appears, click on the option for **Magnifier**.
3)  When the Magnifier Preferences dialog box opens, click on the **Add/Modify** button below the Zoomer List box.
4)  When the Zoomer Options dialog box appears, set the **Zoomer Placement** settings to the following values:

Left:      0
Top:       0
Right:     1023
Bottom:    200

5)  Click on the **Apply** button to apply the changes.

The settings may or may not immediately take effect.  I had to log out and log-in again and everything worked as it should.  This will create a horizontal magnifier strip across the top of the screen.  So far, most programs have worked with it very well.  I have not had any problems with programs being partially hidden under the magnifier with this setup.  But as you can see, a top panel greatly interferes with this setup.

This is definitely a much friendlier way of working with the magnifier compared to the default startup settings which take up half of the screen in a vertical split, thus only allowing applications to be half-visible, if visible at all.

I hope this helps someone, and if anyone has any suggestions as to how to permanently situate the top panel at the bottom of the screen in Xubuntu, this information would be greatly appreciated.

Take care.

---

### Post by Henrik on 2006-08-23
We should clearly revisit the default windows placement. 

About the panel: Have you tried simply changing the 'top' coordinate to something like 30 or 50?

---

### Post by RKCole on 2006-08-24
Sorry for my ignorance...but how do I change the top parameter?  Is it the **screen-position** item in the ~/.config/xfce4/panel/panels.xml file?  Once I get this figured out I'll start testing and see what I find out, and I'll report back if you'd like?

I'm still a beginner in my eyes, but I'm getting better...Thanks for your patience with me.

Take care.

---

### Post by Henrik on 2006-08-25
It turns out to be the **yoffset** value for the first panel in the file you mentioned. It should also be possible to move it with the mouse. If that is not working properly it is probably a bug and should be reported in [Malone](https://launchpad.net/distros/ubuntu/+source/xfce4-panel/+bugs). You might also try asking questions in #xubuntu on freenode. They are very helpful :)

I was actually talking about moving the zoom window so that it sits below the top panel. Is that not an option? Or does the menu that comes down then interfere with the magnification Window? Hm, that is an issue to consider for Ubuntu as well.

---

### Post by RKCole on 2006-08-25
I had tested the magnifier (top/horizontal split) originally on Dapper with the top menu in its default top position, but it appears that anything above the magnifier will be grayed out if you try to view it, even if the magnifier does not cover it.  This gave me a LOT of trouble when I first begun using Ubuntu (Breezy back then) until I found out that I could just drag the panel to the bottom portion of the screen.  This way seems to be an optimal setup.  I've noticed that every program I've worked with so far repositions itself below the magnifier, and every part of the program is usually shown, unless the applet is very long vertically.  I'm on my Windows system right now (I'm trying to get my wife to to see the great things Linux has to offer, but a lot of her friends (who have never used it) are making it out to be a horrible thing.  As is the case, right?  Typically we tend to reject/avoid things that are strange to us...It's going to be a fun thing showing her, though, what Linux is like... :)

If you'd like, I can send you a screenshot of what my setup looks like with and without the magnifier running...just let me know where to post it and if it would be of any help.

I'll see what I can find out about Xubuntu, but at the moment the panels (neither top nor bottom) can be moved by dragging them.  I found a small workaround by putting handles on the panels through the Xfce Menu->Settings->Settings Manager->Panel applet, but the top panel will not stay (permanently) where I place it.  I'll edit the panels.xml file and see if that helps.

Thanks for the help, and I'll report back when I find anything out.

Take care.

---

### Post by Henrik on 2006-08-25
> **RKCole said:**
> If you'd like, I can send you a screenshot of what my setup looks like with and without the magnifier running...just let me know where to post it and if it would be of any help.

Yes please do. You can email it to henrik AT ubuntu.com. I have to warn you though: I might post it on my blog :)

> I'll see what I can find out about Xubuntu, but at the moment the panels (neither top nor bottom) can be moved by dragging them.  I found a small workaround by putting handles on the panels through the Xfce Menu->Settings->Settings Manager->Panel applet, but the top panel will not stay (permanently) where I place it.  I'll edit the panels.xml file and see if that helps.

Hm sounds odd. Perhaps you can report it in Malone, or point it out in #xubuntu. They eere claiming that it should stay in place. Perhaps the magnifier is causing it to jump back.

---

### Post by RKCole on 2006-08-25
I'll get the screenshots sent out soon. (I have to go and do the dishes first. :) ).  I just hope you don't mind my ocean background...Hopefully I'll get to see it in person one of these days...

As for the blog, that's not a problem at all.  I'll send the instructions on how I got it that way, too...maybe it can be used as an accessibility theme or something along those lines...not sure...I just want to be of some help in some way, shape, or form as my ZoomText updater will expire soon...and it's around $200 for a new contract...once it expires, I am not going to use Windows anymore.

Take care.

---

### Post by RKCole on 2006-08-30
I finally was able to straighten some things out, and I am glad to report that the magnifier does work very well in Xubuntu.  It is very smooth, and does nto seem to have many problems from first impressions.

What I do see, however, while I am typing this, is taht it does not show the keyboard input as well as it does on GNOME.  What I mean by this is that when I begin typing, no letters that are entered are shown until I move the mouse pointer; then everythign which was typed appears on-screen.  So basically, when I first begin typing a word, all that I see until moving the mouse pointer is pretty much the first letter of the word.

IN any case, though, this works out a lot better than in using GNOME (for me especially because of only having 256MB of RAM).

The best part of this is that IT WORKS!!

Does anyone know if Gnopernicus comes standard with Xubuntu?

Have a great day, everyone.

---

### Post by Henrik on 2006-08-30
The reason the magnifier does not follow the cursor in Xubuntu is that XFCE does not yet support the Gnome accessibility framework (called AT-SPI). I believe they are working on this support though.

Which editor are you using? I may be that it works if you use Gedit and gnopernicus/Orca, though you'll probably need to install most of gnome and then make sure AT-SPI. It might still be faster though because you don't actually run Gnome.

---

### Post by RKCole on 2006-08-30
Hello, Henrik.

The keyboard entry tracking seems to work on most applications except for entry forms like textboxes in Firefox.  I am beginning to think that that is the main issue: Firefox itself.

In any case, I am really enjoying using this on XFCE/Xubuntu. It's quite amazing compared to what I was used to in GNOME.  I've been working with it for the past few hours and it works wonderfully.

As for installing GNOME components, that won't be a problem at all.  My original install was GNOME/Ubuntu, and I just installed the xubuntu-desktop package.  The GNOME components should already be available since I did this, right?  In any case, I am very impressed, and until I can afford more RAM (and maybe even after that) I think I am going to stick with the Xfce desktop, but I still have GNOME available if I ever need it or want to use it.

Thanks for all of the input and support.

---

### Post by jasongrieves on 2006-08-31
Hi,

try this...

export GTK_MODULES=gail:atk-bridge

see if that helps in some of the GTK applications.  Run it from teh command line to see if the accessibility layers are being loaded

---

### Post by naelphin on 2006-12-21
When I try to use gnopernicus, I get an error:

```
(process:9838): GLib-GObject-CRITICAL **: gtype.c:2215: initialization assertion failed, use IA__g_type_init() prior to this function

(process:9838): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(process:9838): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
```

Using dapper, and used synaptic to install gnopernicus. What should I do?

---

### Post by octathlon on 2007-01-03
In case you are still having problems moving the top panel in Xubuntu - 

I was playing with the Xubuntu Live CD the other day and I found that if you right-click on the panel and select Configure Panel, you then have the option of moving it to top, bottom, or sides.  Also you increase or decrease their sizes, and even add or remove panels.

---

### Post by cerdiogenes on 2007-01-12
> **RKCole said:**
> I had tested the magnifier (top/horizontal split) originally on Dapper with the top menu in its default top position, but it appears that anything above the magnifier will be grayed out if you try to view it, even if the magnifier does not cover it.  This gave me a LOT of trouble when I first begun using Ubuntu (Breezy back then) until I found out that I could just drag the panel to the bottom portion of the screen.  This way seems to be an optimal setup.  I've noticed that every program I've worked with so far repositions itself below the magnifier, and every part of the program is usually shown, unless the applet is very long vertically.  I'm on my Windows system right now (I'm trying to get my wife to to see the great things Linux has to offer, but a lot of her friends (who have never used it) are making it out to be a horrible thing.  As is the case, right?  Typically we tend to reject/avoid things that are strange to us...It's going to be a fun thing showing her, though, what Linux is like... :)

Hi RKCole, I´m writing only to say that when gnome-mag with COMPOSITE support be available to X/Ubuntu this workaround will not be necessary anymore. You will be able to use vertical/horizontal split without seeing the gray area in the magnified aread.

Best regards.

---

