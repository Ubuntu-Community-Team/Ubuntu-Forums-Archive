---
title: "Ambiance - Theme Editing. Help?"
date: 2010-04-20
forum: Art &amp; Design
---

### Post by Roasted on 2010-04-20
I fired up the Ambiance theme that's coming out with 10.04 and while I was very impressed by it, it wasn't my cup of tea. I made some slight alterations and suddenly it's my favorite theme. For example, I changed the background color to match that of dust-sand, giving it a nice slate look. Then (because I darkened the background) I also darkened the text to jet black, which contrasted nicely and was very easily readable.

Well, I want to change the dark gray at the top of windows, along with the background color of the menu under applications/places/system, and the panel color. They're all the same darkish gray color, but I'd like to darken it a little bit.

What I did was I took a screenshot and went into gimp and found the hex value for the dark gray that's default in Ambiance. Then I searched through the gtkrc file and the XML file within the theme folder itself and changed all instances of the old dark gray hex to a new hex that corresponds with a darker gray (almost blackish) that I wanted to try. The problem is, it changes the top edge of each window, however it's still the default dark gray in the top panel, along with the background of applications/places/system. I'm curious – how can I change the color to those areas as well? Basically, fire up Ambiance. Look at all of the dark gray. In the menu, the top panel, the top of each window – I want ALL of that changed. How can I do that?

---

### Post by DanRabbit on 2010-04-20
Hey There,

The problem you are running into with the panel is because Ambiance uses a pixmap for theming the panel ;) You will have to open up that image in GIMP and then alter its color in that way.

---

### Post by Roasted on 2010-04-20
Well, I got closer - but no cigar quite yet. I solved the problem from my original question, but there's a section that I can't seem to edit. I checked some of the png's that were in the theme folder and I can't seem to find where I need to go to edit this last bit. 

[[IMG]http://img260.imageshack.us/img260/5344/screenshotmr.th.png[/IMG]](http://img260.imageshack.us/i/screenshotmr.png/)

---

### Post by mcduck on 2010-04-20
The window decorations come from the Metacity theme, not from the GTK theme, so you need to edit /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml and most likely also some of the image files in the same directory..

---

### Post by Roasted on 2010-04-20
Oh, okay. That helps shed some more light on the situation. Thank you!

Question, though. Let's say I get this tweaked the way I want it and I want to upload it to gnome-look.org. What would I basically need to do? Is there anything in particular I need to do? Reason I ask is I just packaged it in a tar.gz and tested it on my 10.04 VM, and while it installs fine, it still picks it up as the standard Ambiance theme with zero modifications. *shrug*

Sorry I hate to sound like such a noob on this, but just trying to get started. Thanks for the help.

EDIT - Inside the metacity-1 folder, there are 3 images. trough_left/middle/right. I edited each of those in gimp, yet nothing changed. I assume that it's in the XML file, however where in the XML file do I know is the window decoration?

---

### Post by Roasted on 2010-04-21
All right - with some additional help from DanRabbit it was figured out. I got the theme customized in the manner I want. There's quite a few things that I want to change though, which brings up a question that I'm hoping somebody here can answer.

Let's say I install a theme such as Dust Sand. When I change the background color from BBBBBB to DDDDDD. When I change it, does it make that DDDDDD change in the actual GTKRC file? Or does it add some kind of temporary "mask" file that takes priority over the BBBBBB file?

Reason I ask is I was assuming I could just edit the metacity settings in the XML file of the theme, then select the theme in appearances, change the colors the way I want, then just save it and pack it in a tar.gz and that be it. But it's proving to be a bit of a headache, which lead me to believe perhaps me changing the color settings in appearance/customize settings is NOT the same as putting in the default color settings in the actual GTKRC files themselves. Can anybody shed some light on this??

---

### Post by mcduck on 2010-04-21
Changing the colors in the Appearance dialog is indeed just a temporary change, stored in gconf, and doesn't change the theme itself.

It would be quite annoying actually if the original colors of the theme were lost the very second you touched the color options in the Appearance dialog, even more so when it comes to system-wide installed themes and a computer with many users... ;)

---

### Post by Roasted on 2010-04-21
Well at least it makes sense to me on why I can just "reset to default" and blam - there's my original colors again. It just points back to the original file.

I've never made a theme, and as far as I'm concerned I'm just doing some light noob work on an existing theme to make some changes. All I'm really doing is taking a screenshot of the regular theme, loading it in gimp, using color picker to pick up the hex value of that color, then I search the entire GTKRC and Metacity XML file to find where it's entry is at and change it.

So ultimately I have to set up the colors with the theme accordingly so when I personally load it and install it, BLAM - it's 100% dead on to what *I* want. Then if users want to change it, they can in the appearance settings. Am I on the right path?

---

### Post by mcduck on 2010-04-21
> **Roasted said:**
> Well at least it makes sense to me on why I can just "reset to default" and blam - there's my original colors again. It just points back to the original file.

I've never made a theme, and as far as I'm concerned I'm just doing some light noob work on an existing theme to make some changes. All I'm really doing is taking a screenshot of the regular theme, loading it in gimp, using color picker to pick up the hex value of that color, then I search the entire GTKRC and Metacity XML file to find where it's entry is at and change it.

So ultimately I have to set up the colors with the theme accordingly so when I personally load it and install it, BLAM - it's 100% dead on to what *I* want. Then if users want to change it, they can in the appearance settings. Am I on the right path?

Yes, you got the idea right. :)

By the way, the way I usually use to figure out what color affects what in the actual theme is to use some app like [The Widget Factory]("apt:thewidgetfactory") that is able to display most of the widgets for you in one window and load themes separately from what you are actually using on your desktop. Then I simply change some color to something radically different, bright red for example, and check the TWF window to see what changes in the theme.

---

### Post by Roasted on 2010-04-21
I forget where I even got this originally. I think I downloaded a PPA for the theme and then just grabbed the folder out of .themes and began tweaking it, then re-packaged it in a tar.gz and here it is.

I've never messed with themes before, besides installing them by the hundreds to try them out. Can anybody see anything wrong considering I got the theme from a PPA, got it out of .themes, edited it, tar.gz'd it, and here it is? Any fore-see-able problems?

---

### Post by Roasted on 2010-04-23
Well I learned a thing or two about editing existing themes, although it's pretty straight forward. I can't imagine building one from ground-up, though. But it was easy enough for me to edit the config files to adjust the default color choices the way I wanted.

Here's what I came up with:

[http://gnome-look.org/content/show.php/Ambiance+-+v2?content=123677](http://gnome-look.org/content/show.php/Ambiance+-+v2?content=123677)

---

