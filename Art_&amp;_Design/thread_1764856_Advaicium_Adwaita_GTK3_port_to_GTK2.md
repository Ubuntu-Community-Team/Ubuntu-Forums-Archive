---
title: "Advaicium: Adwaita GTK3 port to GTK2"
date: 2011-05-22
forum: Art &amp; Design
---

### Post by maximo1010 on 2011-05-22
Advaicium is now dead. Someday, this thread will be holding a completely new version of Advaicium, namely Ada X. The first Ada X version will be 10.0, codenamed Firelight.

You can still download Advaicium 0.96.2 as of now.

---

### Post by nilarimogard on 2011-05-23
Great work!

---

### Post by mxt on 2011-05-23
Great job, thanks!

I would add this to gtk-2.0/gtkrc to improve the integration of Chrom[e,ium]:

style "chrome-gtk-frame"
{
    ChromeGtkFrame::frame-color = @bg_color
    ChromeGtkFrame::inactive-frame-color = "#EAEAEA"

    ChromeGtkFrame::frame-gradient-size = 128
    ChromeGtkFrame::frame-gradient-color = @bg_color

    ChromeGtkFrame::scrollbar-trough-color = @bg_color
    ChromeGtkFrame::scrollbar-slider-prelight-color = @base_color
    ChromeGtkFrame::scrollbar-slider-normal-color = @base_color
}

class "ChromeGtkFrame" style "chrome-gtk-frame"

---

### Post by jtfolden on 2011-05-23
I just checked and this uses the version of Adwaita from Gnome-themes-standard 3.0.0 rather than the more streamlined version (with less padding and other fixes) that was released in Gnome-themes-standard 3.0.1 about 3 weeks ago.

That might be the version still in Ubuntu's Gnome 3 PPA(?) but if you are using Fedora or OpenSUSE this is a regression.

Other than that, it's a good start!  I hope you can get the scrollbars taken care of, as well. :D

---

### Post by inckie on 2011-05-24
I’m getting pink borders everywhere since updating today. Please see the screenshot.

---

### Post by maximo1010 on 2011-05-24
> **inckie said:**
> I&#8217;m getting pink borders everywhere since updating today. Please see the screenshot.

I too have that (Adwaita AND Advaicium). But not in stuff like Rhythmbox, Brasero (both are GTK3). This does not have to do anything with Advaicium (come on, that's a GTK2 theme). It's Adwaita's fault. I can not fix that. Please talk to the GNOME 3 devs about this issue.

---

### Post by PPyclik on 2011-05-24
Problem with pink borders occurs, when you have too new version of Adwaita installed on your system, eg. from Fedora's rawhide. At least, that's true on Fedora.

Anyway, great work. :)

In order to have always up to date version of Adwaita, I made symlinks from /usr/share/themes/Adwaita contents (without gtk-2.0 directory) to ~/.themes/Advaivium.

---

### Post by maximo1010 on 2011-05-24
> **mxt said:**
> Great job, thanks!

I would add this to gtk-2.0/gtkrc to improve the integration of Chrom[e,ium]:

style "chrome-gtk-frame"
{
    ChromeGtkFrame::frame-color = @bg_color
    ChromeGtkFrame::inactive-frame-color = "#EAEAEA"

    ChromeGtkFrame::frame-gradient-size = 128
    ChromeGtkFrame::frame-gradient-color = @bg_color

    ChromeGtkFrame::scrollbar-trough-color = @bg_color
    ChromeGtkFrame::scrollbar-slider-prelight-color = @base_color
    ChromeGtkFrame::scrollbar-slider-normal-color = @base_color
}

class "ChromeGtkFrame" style "chrome-gtk-frame"

Done. :)

---

### Post by inckie on 2011-05-24
> **maximo1010 said:**
> I too have that (Adwaita AND Advaicium). But not in stuff like Rhythmbox, Brasero (both are GTK3). This does not have to do anything with Advaicium (come on, that's a GTK2 theme). It's Adwaita's fault. I can not fix that. Please talk to the GNOME 3 devs about this issue.

Hey, chill! I just thought you&#8217;d have advice on how to fix it. Sorry if I sounded demanding. :)

> **PPyclik said:**
> Problem with pink borders occurs, when you have too new version of Adwaita installed on your system, eg. from Fedora's rawhide. At least, that's true on Fedora.

Anyway, great work. :)

In order to have always up to date version of Adwaita, I made symlinks from /usr/share/themes/Adwaita contents (without gtk-2.0 directory) to ~/.themes/Advaivium.

I just did that and the pink borders remain only in tooltips. Thanks, @PPyclik!

---

### Post by maximo1010 on 2011-05-24
> **inckie said:**
> Hey, chill! I just thought you&#8217;d have advice on how to fix it. Sorry if I sounded demanding. :)


I am calm, actually...

---

### Post by rodrigo.miguel on 2011-05-24
Good job maximo1010

I published a post about Advaicium on my blog (in Brazilian Portuguese):
[http://linuxlike.blogspot.com/2011/05/advaicium-versao-gtk2-do-tema-adwaita.html](http://linuxlike.blogspot.com/2011/05/advaicium-versao-gtk2-do-tema-adwaita.html)

And also a video on how to proceed with the installation:
[http://youtu.be/QyqwPfFZxCg](http://youtu.be/QyqwPfFZxCg)

I await the evolution of the theme! ;)

---

### Post by mxt on 2011-05-25
> **maximo1010 said:**
> Done. :)

Thanks. 

Another change I propose is restoring the default contrast, more similar to Adwaita (contrast = 1.0).

---

### Post by mxt on 2011-05-25
A small regression: after the last update toolbar buttons in Chrome are cut. This seems to solve the problem:

style "button"
{
	xthickness = 4
	ythickness = 4

...

---

### Post by ceramicm on 2011-05-25
I started work on a similar gtk2 theme. I ported the adwaita scrollbars and tabs using the pixmap engine and added round sliders. You can use the code and images if you'd like. I attached the theme; relevant files are in the gtk-2.0 directory.

Edit on 2011-5-28: Uploaded a newer version. Read about changes [here]("http://ubuntuforums.org/showpost.php?p=10873648&postcount=23").

---

### Post by maximo1010 on 2011-05-25
> **ceramicm said:**
> I started work on a similar gtk2 theme. I ported the adwaita scrollbars and tabs using the pixmap engine and added round sliders. You can use the code and images if you'd like. I attached the theme; relevant files are in the gtk-2.0 directory.

I will use the code and images, that's really key to integration.
Alpha 1 is down the road!

By the way, where are the sliders?

---

### Post by maximo1010 on 2011-05-25
> **rodrigo.miguel said:**
> Good job maximo1010

I published a post about Advaicium on my blog (in Brazilian Portuguese):
[http://linuxlike.blogspot.com/2011/05/advaicium-versao-gtk2-do-tema-adwaita.html](http://linuxlike.blogspot.com/2011/05/advaicium-versao-gtk2-do-tema-adwaita.html)

And also a video on how to proceed with the installation:
[http://youtu.be/QyqwPfFZxCg](http://youtu.be/QyqwPfFZxCg)

I await the evolution of the theme! ;)

You're welcome!

However, the screenshots are from the older 0.96.1 theme.

---

### Post by ceramicm on 2011-05-25
> By the way, where are the sliders?

Created using Murrine, rather than pixmap, so there are no image files:

```
style "scale" {
	xthickness	= 0
	ythickness	= 0

	bg[ACTIVE]	= @bg_color
	bg[NORMAL]	= shade (1.30, @bg_color)
	bg[PRELIGHT]	= shade (1.18, @bg_color)
	bg[SELECTED]	= shade (0.9, @bg_color)
	bg[INSENSITIVE]	= shade (0.98, @bg_color)

	GtkScale::slider-length		= 14
	GtkScale::slider-width		= 14
	GtkScale::trough-side-details	= 0

	engine "murrine" {
		sliderstyle		= 0	 	# 0 = nothing added
		glazestyle		= 0
		focusstyle		= 0	
		glowstyle		= 0
		highlight_shade		= 1.0		# set highlight amount for buttons or widgets
		border_shades		= {0.8, 0.6}
		contrast		= 1.1
		lightborderstyle	= 1
		roundness		= 15
		trough_shades		= {0.9, 1.1}
	}
}
class "GtkScale" style "scale"
class "GtkVScale" style "scale"
class "GtkHScale" style "scale"

```

---

### Post by PPyclik on 2011-05-25
Hey,

in addition to this work-in-progress-but-already-wonderful theme, I created extension for Chrome/Chromium, which changes scrollbars to Adwaita-styled ones. Hope you like it. :)

To install it, remove .zip extension from the file and drag it over Chrome's/Chromium's window.

Also, alternative download [http://ge.tt/93L4BY4]("http://ge.tt/93L4BY4") (without .zip extension).

---

### Post by murderslastcrow on 2011-05-25
Thanks PPyClik- big help to improve consistency for the people who use Chrome on my computers.

After taking a look at those pixmap additions, I hope they make it into the current theme, soon. It'd be nice not to have to rely on too many engines to get this working, but it's pretty close to being consistent enough for every day use (pretty fast). I'm already quite impressed- keep it up. I'm actually kinda' surprised the Gnome 3 developers didn't do this themselves, honestly. (of course, the new GTK 3 theme engines are likely to surpass the abilities of GTK 2 themes entirely soon, but for now this should work great).

Also, might want to include the GTK 3 from the 'Netbook' theme, since the GTK 3 in the 0.96.2 is a bit outdated (at least according to my theme in Arch Linux, and the one in Fedora 15). Looking forward to the next version. :D

---

### Post by jtfolden on 2011-05-25
Yes, I noticed a new version of the Adwaita theme (3.0.2) was delivered to my Fedora 15 system a few hours ago, as well.

---

### Post by inckie on 2011-05-27
A quick suggestion, if I may:

```
--- gtkrc.old	2011-05-27 15:14:02.940584339 -0300
+++ gtkrc.new	2011-05-27 15:15:18.434223847 -0300
@@ -1,7 +1,7 @@
 
 # Advaicium GTK2 developer release gtkrc version 0.96.2 (pre-alpha branch, iteration 2)
 
-gtk-color-scheme = "base_color:#ffffff\nfg_color:#000000\ntooltip_fg_color:#000000\nselected_bg_color:#4A90D9\nselected_fg_color:#ffffff\ntext_color:#1A1A1A\nbg_color:#EDECEB\ntooltip_bg_color:#E7F3FD\ntoolbar_bg_color:#C6C6C0\nbtn_bg_color:#DEE1DE"
+gtk-color-scheme = "base_color:#ffffff\nfg_color:#000000\ntooltip_fg_color:#000000\nselected_bg_color:#80B7EE\nselected_fg_color:#ffffff\ntext_color:#1A1A1A\nbg_color:#EDEDED\ntooltip_bg_color:#E7F3FD\ntoolbar_bg_color:#C6C6C0\nbtn_bg_color:#EDEDED"
 
 gtk-auto-mnemonics = 1
 
@@ -77,7 +77,7 @@
 	base[ACTIVE]      = shade (0.9, @selected_bg_color)
 
 	engine "clearlooks" {
-		colorize_scrollbar = TRUE
+		colorize_scrollbar = FALSE
 		reliefstyle = 0
 		menubarstyle = 3
 		toolbarstyle = 0
@@ -239,7 +239,7 @@
 
 style "notebook_bg" {
 
-	bg[NORMAL]        = shade (1.02, @bg_color)
+	bg[NORMAL]        = shade (1.02, @base_color)
 }
 
 style "button"
@@ -253,7 +253,7 @@
       
 
 	bg[NORMAL]     = @btn_bg_color
-	bg[PRELIGHT]   = shade (1.07, @btn_bg_color)
+	bg[PRELIGHT]   = shade (0.98, @base_color)
 	bg[SELECTED]   = shade (1.04, @btn_bg_color)
 	bg[ACTIVE]     = shade (0.9, @btn_bg_color)
 	bg[INSENSITIVE] = mix (0.3, @btn_bg_color, @bg_color)
```

---

### Post by thebluesgnr on 2011-05-28
Pretty good job, theme looks great!

If I may suggest, you should try to get it upstream for GNOME 3.2. You could probably do that by posting the theme here: [https://bugzilla.gnome.org/show_bug.cgi?id=646556](https://bugzilla.gnome.org/show_bug.cgi?id=646556)

Again, awesome job!

---

### Post by ceramicm on 2011-05-28
I updated my theme with more accurate scrollbars, tooltips, text entry boxes, handles, and more. I also included adwaita 3.0.2.

---

### Post by murderslastcrow on 2011-05-29
Hi, Ceracim. Does your theme inherit Advaicium in some way, or is it an amendment to the gtkrc in that file? For some reason, I only get the scrollbars, buttons, text fields, etc. from your theme, but everything else is a plain theme with mismatched colors, no toolbar/menubar bitmaps like Advaicium, etc. Might just be a noobish mistake of mine, but I'd definitely like to give your theme a good, honest look. If it does inherit Advacium, it may an issue since I renamed the folder to 'advacium', but I don't expect that to affect the way the theme is recognized, much.

Any pointers would be very helpful.

Also, I think it would be great to include a GTK 2 theme upstream for Gnome 3.2, or a stable release update, but the main issue I think they'd have would be dependencies. So far as I know, the only engines required now are for Clearlooks, and this theme depends on a few more engines. Then again, it may be impossible to reproduce the theme without bringing in some other theme engines. Other than that, I think it would be a non-issue, so long as the theme is as accurate as possible.

Thanks for the hard work, guys. Takes a load off my shoulders.

---

### Post by jtfolden on 2011-05-29
Yes, I'm seeing the same issue with the netbook package. GTK2 apps are not completely themed.

edit: Ooops, fixed... I didn't realize the Netbook theme used the Murrine engine.

I've noticed a small issue though, selected menubar items, appear as white text on a white background.

---

### Post by ceramicm on 2011-05-29
I created my theme based on the default Clearlooks/Adwaita and also include some assets from the Moblin theme (hence the name Netbook). It does not require Advaicium. I use the Clearlooks, Murrine, and Pixmap engines.

Which GTK 2 apps aren't being themed correctly? I have tested GIMP and AbiWord, and they both theme correctly for me (see [screenshot]("http://ubuntuforums.org/showpost.php?p=10873648&postcount=23")). Toolbar bitmaps are included and should work. I intentionally did not include menubar bitmaps because they break part of the menu highlight and, to my eyes, the menubar gradiant from Murrine is similar enough. I'll look into your issue; I'd really like to make it work.

I read the [upstream bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=646556") (it's what gave me the idea to look at the Moblin theme), and I considered linking to this thread, but I figured that the GNOME developers would probably write a GTK 2 Adwaita engine. Once that happens, a theme based on Clearlooks, Murrine, and Pixmap will be replaced by one based on Adwaita.

I'm perfectly fine (honored) with anyone using my theme (in whole or in part) in the meantime. I plan to keep working on it. I can remove the Clearlooks portions and only use Murrine and Pixmap. I want to clean up the code some and then add check/radio boxes.

*Edit*: Yes, I have the same problem with selected menubar items. I haven't found a way to change that text color to @text_color. It seems to always stay white. I'd appreciate it if anyone could share a fix.

---

### Post by murderslastcrow on 2011-05-29
Oh, haha. All it needed was Murrine, silly me. Works well with QGtkStyle, as well. I agree that the menubar is best done with a generated gradient, since this would make it easier to modify for something like the dark Adwaita theme. All in all, great job.

I only have one issue, and it may be something impossible to fix and keep everything as it is, but one GTK application (Banshee) seems to have a long, 1px line across the bottom of the menubar (screenshot attached). I'm guessing this is intentional, but I'm wondering if it's necessary to the accuracy of the theme, since it makes it a bit difficult to look at with toolbarless applications. Of course, if you could point me to the part of the gtkrc that controls the color of the line/existence of the line I could modify it myself. No need to change everything because of my little preference.

Aside from that, it's very, very close to being dead on. I would very much like to package it in the AUR (Arch User Repository) for Arch users to get it quickly. Of course, it would be best if the theme were uploaded to gnome-look.org and had a name aside from 'netbook' for me to give it in AUR. I'll only package it with your permission, of course. This may hold people over until 3.2, and your work is well appreciated by me, so I think it'd be great for a wider audience.

Hah, this newer theme totally hijacked the thread, so maybe we could make a new one for your edition? Just making suggestions, you don't have to listen to a word I say. XD

P.S. One last thing that I'm not sure if the Murrine engine is capable of- is there any option to make the menubar grabbable, as in Adwaita/Ambience/Greybird/Oxygen? I can look it up myself if this isn't easy information to come by. Thanks!

---

### Post by PPyclik on 2011-05-29
That theme is almost pixel perfect now. :) There is one little problem with menus though, you are probably aware of it. :)

---

### Post by ceramicm on 2011-05-29
Thanks! I'm glad it's working now, and I'm glad you like it.

I've tweaked and cleaned up the code (fixed the issue with menubar text color). The newest version is attached. Please let me know if you find any regressions.

I removed the line under the menubar. The option is "GtkMenuBar::shadow-type = GTK_SHADOW_NONE". I'll find a way to apply it to just Banshee if it causes problems in other apps.

Regarding grabbable menubars, I include the line "GtkWidget::window-dragging = 1" in style "menu" {}. Is that what you were referring to?

Thank you for offering to package it for AUR. I would appreciate that very much. Should I stop bundling Adwaita and create a symlink so that the system Adwaita is used?

I'm open to name suggestions from anyone, if you have any ideas (I don't yet...maybe a translation of "adwaita"?). I'll post it to gnome-look and create a separate thread once we come up with a name.

Thank you for the constructive feedback!

---

### Post by PPyclik on 2011-05-29
Awesome work, menu-bar text problem is gone. Not sure, if these are regressions, I found some differences between gtk2 and gtk3 buttons though. Hope it helps. :)

---

### Post by Ulukai on 2011-05-29
In Firefox, the menu color problem is still not fixed. When pressing File, Edit, Help etc, the color swaps to white. Other GTK2 apps seem fine. 

Very nice job so far, although I don't like the tabs, they look too pyramid-like...

---

### Post by jtfolden on 2011-05-30
> **ceramicm said:**
>  Should I stop bundling Adwaita and create a symlink so that the system Adwaita is used?

I think perhaps that would be a good idea, if possible. 

> I'm open to name suggestions from anyone, if you have any ideas (I don't yet...maybe a translation of "adwaita"?). I'll post it to gnome-look and create a separate thread once we come up with a name.


Well, Adwaita was the name of one of the oldest living (around 255 yo) giant tortoises in the world. The species is 'Aldabra' so that might be one to use... or if you wanted to stick to the names of other long-lived tortoises there is 'Tu'i Malila' and 'Esmeralda'. :D

---

### Post by Ulukai on 2011-05-30
> **jtfolden said:**
> I think perhaps that would be a good idea, if possible. 



Well, Adwaita was the name of one of the oldest living (around 255 yo) giant tortoises in the world. The species is 'Aldabra' so that might be one to use... or if you wanted to stick to the names of other long-lived tortoises there is 'Tu'i Malila' and 'Esmeralda'. :D

+1 for Aldabra!

---

### Post by PPyclik on 2011-05-30
+1 :)

---

### Post by Venemo on 2011-05-30
I myself would be glad to see an Adwaita-like Gtk2 theme.
If you are finished, I think you should even send it to upstream so that they can make good use of your work.

> **jtfolden said:**
> Well, Adwaita was the name of one of the oldest living (around 255 yo) giant tortoises in the world. The species is 'Aldabra' so that might be one to use... or if you wanted to stick to the names of other long-lived tortoises there is 'Tu'i Malila' and 'Esmeralda'. :D

According to Wikipedia, adwaita means "one and only" in Sanskrit.
I don't see any problems naming the Gtk2 variant Adwaita too, as long as it looks identical to the Gtk3 version, I think everyone will be delighted to see it.

---

### Post by ceramicm on 2011-05-30
The newest version fixes colors, listviews, treeviews, notebook tabs, and toolbars.

It also comes with a new name. I chose the name Aldabra (Adwaita is a turtle; Aldabra is its species) because it is memorable and easy to spell, so someone looking for the theme should be able to find it. Aldabra it is. Thanks for all the feedback and suggestions!

Anyone is welcome to rename, package, or otherwise distribute the theme, or to recommend it to upstream. I still feel like GNOME wouldn't be interested (because I think they are probably working on an actual Adwaita GTK2 engine), but I would be honored if it was useful.

Over the next few days, I hope to add accurate expanders,  check boxes, radio buttons, regular buttons, and to fix Banshee listviews and Firefox menubar text. I want to put Aldabra on GNOME-look for broader adoption, too.

---

### Post by murderslastcrow on 2011-05-31
Hey, sorry- was away from the computer for my birthday. Things really have improved quite a bit since I left- I can confirm it's exceptional work. I'm very satisfied with it as it is, but I'm glad you're willing to improve it even further to make it match as exactly as you can. Glad there's someone with the free time for it! I'm going to refer to this post until there's a gnome-look.org entry and make a post in the Arch forums as soon as I get it in the AUR.

I'll probably send in a tip at OMG Ubuntu! as well, since this is a pretty major update from Advaicium. Speaking of which, we may want to move the discussion to an actual gnome-look.org entry, or start a new thread... then again, this may be pretty on-topic, although the topic name is misleading to some extent. I'm not a moderator, so of course it doesn't matter very much, just speculating.

P.S. That looked like the relevant option for dragging the menubar, but I still can't seem to do it, at least not in Banshee, Pidgin, or Mousepad (these may be unique in some way, but I figure they're pretty far apart on the GTK 2 spectrum for a general test). Not entirely sure if we're referring to the same feature, but it's not a major annoyance, just something that would make it feel completely compatible with Adwaita. So far as I'm concerned, you've done more than enough work already, and this is the only thing I could recommend for a finishing touch. Of course, it could just be a local issue with my packages or something like that.

---

### Post by PPyclik on 2011-05-31
Wow, new tabs, I love them. :D Would you add code from [third post]("http://ubuntuforums.org/showpost.php?p=10851805&postcount=3") to your gtkrc? It really adds to Chrome integration.

---

### Post by jtfolden on 2011-05-31
Great work. Glad one of the suggested names was found suitable. :-)

I have a, sort of, side question; I'm curious if it's possible to more effectively theme Banshee? It doesn't currently pick up the toolbar background. I know it's a bit of a 'weird' app...

Oh and I think the Gnome devs might *possibly* appreciate the contribution as it didn't seem like a GTK2 theme was high on the list of priorities last time I checked (as of a couple of months ago). It couldn't hurt to post on one of their mailing lists or IRC channel, I don't think.

---

### Post by ceramicm on 2011-05-31
Google Chrome/Chromium code is now a part of Aldabra. Thanks for the tip!

I started a [new thread]("http://ubuntuforums.org/showthread.php?t=1772074") specifically for Aldabra. Updates will be posted to that thread. I would appreciate any new feedback there. Thank you very much for the positive response so far!

*Edit*: Aldabra is now available on [GNOME-look.org]("http://GNOME-Look.org/content/show.php?content=142247") as well.

*Edit*: I added a link to the new thread in the [upstream bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=646556").

---

### Post by Venemo on 2011-06-01
> **ceramicm said:**
> I still feel like GNOME wouldn't be interested (because I think they are probably working on an actual Adwaita GTK2 engine)

You "feel" wrong.
Upstream doesn't work on anything like this, because they lack the manpower to do so. They admittedly haven't had the manpower to create the theme for Gtk 2 either.

[http://lists.fedoraproject.org/pipermail/desktop/2011-May/007271.html](http://lists.fedoraproject.org/pipermail/desktop/2011-May/007271.html)

---

### Post by dmaxel on 2011-06-06
Great job, but I won't be using this until a few more things are fixed. My main problem is that the buttons, drop-down menus, etc. are all quite a bit larger than with regular Adwaita. This is a horrible thing for my little netbook, so I guess I'll have to pass for now.

---

### Post by maximo1010 on 2011-06-19
> **PPyclik said:**
> Awesome work, menu-bar text problem is gone. Not sure, if these are regressions, I found some differences between gtk2 and gtk3 buttons though. Hope it helps. :)

I did notice them, I just don't really know Murrine nor CSS nor is it screenshotable and I haven't got a CSS rendering tool.

---

### Post by maximo1010 on 2011-06-19
OK, the reason for my recent inactivity is my sneaky laptop with a boiling GPU and Mac envy (no, not again!). I think I will continue working on this theme using my Fedora 15 virtual machine or when/if I get a new laptop. Alpha 1 will definitely pop up soon, though.

PS: Any fork will be mixed into Advaicium to make it the most consistent port of Adwaita available by merging the best parts of every theme into one. So: If you want to help me - fork me!

Release date for Alpha 1 (0.97.1): July 31, 2011

Possible release date for 1.0 (1.00.1): March 22nd, 2012

---

### Post by galacticaboy on 2011-09-09
I just tried this theme, my windows boreders are not changing, why?

---

### Post by galacticaboy on 2011-09-09
This is what mine look like after applying the theme. Why is it like that?

---

### Post by maximo1010 on 2011-11-05
> **rodrigo.miguel said:**
> Good job maximo1010

I published a post about Advaicium on my blog (in Brazilian Portuguese):
[http://linuxlike.blogspot.com/2011/05/advaicium-versao-gtk2-do-tema-adwaita.html](http://linuxlike.blogspot.com/2011/05/advaicium-versao-gtk2-do-tema-adwaita.html)

And also a video on how to proceed with the installation:
[http://youtu.be/QyqwPfFZxCg](http://youtu.be/QyqwPfFZxCg)

I await the evolution of the theme! ;)

Nothing is coming for now. Until someday something completely new comes out.

---

### Post by maximo1010 on 2011-11-05
> **galacticaboy said:**
> I just tried this theme, my windows boreders are not changing, why?

Because there are none to change into. How would you be able to change your car into a dream car if the dream car doesn't exist?

PS: Ada X is coming!

---

### Post by pchgo on 2012-07-23
I love this theme...

---

