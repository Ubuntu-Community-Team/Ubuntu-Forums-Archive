---
title: "Wacom Tablet and Sketchbook on Linux?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by toastysquirrel on 2007-12-28
I'm in the pre-installation phase with Ubuntu, having never worked with *nix before in my life, I'm cautiously but eagerly trying to ween myself away from Windows dependency.  That being said I have an older Graphire 2 Wacom tablet and I'm hoping to use it with Ubuntu.  From what I've seen the [Linux Wacom Project]("http://linuxwacom.sourceforge.net/") is probably where I need to get started with that.

But now for the part I'm not so sure about... Is there a good art/sketching program out there that will wok on Ubuntu?  I currently use [Autodesk Sketchbook]("http://usa.autodesk.com/adsk/servlet/index?id=6848332&siteID=123112") Pro 1.1 which is freakin' awesome for, well, sketching.  The problem is that it's a Windows App.  Is anyone aware of a program that's comparable for Linux?

I'm pretty sure I'm still going to be dual booting into Windows for games and for PhotoshopCS, but I'd like to move as much as I can away from XP.

Does anyone have any thoughts?  Thanks everyone!

---

### Post by toastysquirrel on 2007-12-29
~bump~

Wow, the threads in this forum move fast :)

---

### Post by argraff on 2007-12-31
Welcome to Linux - first of all!

I use GIMP for sketching and such (I love the ink tool!), Inkscape for vector work, and Art Rage 2 (a windows program easily installable with WINE and Wine-Doors) for specific looks (you can do oil painting etc with it.) All work well with my Wacom Graphire 4...

If you need more info, just let me know!

---

### Post by sloggerkhan on 2007-12-31
Yeah, your wacom should work, just  do 
sudo aptitude install wacom-tools xserver-xorg-input-wacom
to get the packages.
You will then be able to use a bunch of options to modify the settings in
/etc/X11/xorg.conf    (things like aspect ratio of the drawing surface, sensitivity curves, etc.)


As for software, I also use gimp and inkscape, not sure how they compare to sketchbook.

---

### Post by toastysquirrel on 2008-01-28
Thanks for the info guys, by now I'm well into using Ubuntu and I only load up XP for Photoshop, Sketchbook Pro, and gaming.  I've started checking out GIMP and Artrage as far as sketching goes.  Sketchbook Pro is simply an awesome tool for mimicking real-world pencil sketching, so the big question is how well I can adapt the other programs, or rather *if* they can be adapted for that kind of drawing.  Unfortunately SKB works like garbage in Wine, or rather is plain **doesn't** work.  There was one case of it working, but the write up was pretty old and a nightmare to follow.  I'm still trying to get CS2 to work in Wine.

I've got the Wacom pad working, *with* pressure sensitivity.  But one thing I'm curious about is it doesn't seem like the pressure settings I make stick between system boots.  **[tablet-apps]("http://alexmac.cc/tablet-apps/")** has a pretty good GUI for making the adjustments, however like I said, they don't seem to stick between boots.  Do you know if there's another GUI out there that does this, or am I simply missing something and it *should* be working?

Thanks again! :KS

---

### Post by sloggerkhan on 2008-01-28
In the /etc/X11/xorg.conf file, I think there is a way to write custom pressure curves into the file for the pen input devices. Unfortunately, I am not sure of the details.

---

