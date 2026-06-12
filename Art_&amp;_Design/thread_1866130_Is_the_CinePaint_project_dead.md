---
title: "Is the CinePaint project dead?"
date: 2011-10-21
forum: Art &amp; Design
---

### Post by thrischan on 2011-10-21
Somebody knows what happen to Cinepaint? This program is great, however it seems it is abandoned, There is not information on the internet about what happened. 

I work with floating point images from 3d renderers and cinepaint is able to open these images with no problem. I installed this version they adapted for ubuntu : 

[https://launchpad.net/~secretlondon/+archive/ppa/+sourcepub/293092/+listing-archive-extra](https://launchpad.net/~secretlondon/+archive/ppa/+sourcepub/293092/+listing-archive-extra)

But this version seems to lack support for wacom tablet sensitivity. At least I can't find where to activate it, like one would have to do in Gimp. If you have any news or information about what happen to this project I would appreciate any information.

Thanks in advance!

---

### Post by PayPaul on 2011-10-21
Apparently the last blog entry for this program was in 2009. What is the paradigm for Linux projects? It does seem a lot of what I've seen is projects that get started and then halt at a certain point and never progress. One would almost want to argue that free, open source developments have a short shelf life because there's no gain to be made after awhile. Does the love die out after awhile?

[http://cinepaint.blogspot.com/](http://cinepaint.blogspot.com/)

The website is still up and one can download the program and such.

[http://www.cinepaint.org/more/](http://www.cinepaint.org/more/)

The "Plugins" section doesn't seem to have much in the way of downloadable files at all.

[http://www.cinepaint.org/more/plug-ins.html](http://www.cinepaint.org/more/plug-ins.html)

This program is really used by Hollywood studios?

---

### Post by prokoudine on 2011-10-22
> **thrischan said:**
> Somebody knows what happen to Cinepaint? This program is great, however it seems it is abandoned, There is not information on the internet about what happened. 

What happened is that the project manager failed to keep Cinepaint maintained. There haven't been releases in years despite of endless promises.

There is a personal fork by a former team member here:

[http://www.oyranos.org/scm?p=cinepaint.git](http://www.oyranos.org/scm?p=cinepaint.git)

No releases per se, but it's somewhat maintained.


> **PayPaul said:**
> What is the paradigm for Linux projects? It does seem a lot of what I've seen is projects that get started and then halt at a certain point and never progress. One would almost want to argue that free, open source developments have a short shelf life because there's no gain to be made after awhile. Does the love die out after awhile?

Pardon? There's tons of apps that are maintained even after 10 years of work. So? :)

> **PayPaul said:**
> This program is really used by Hollywood studios?

It was before. Now? Who knows.

---

### Post by thrischan on 2011-10-28
Hi Guys, 

In case you are interested, I asked Kai-Uwe Behrmann, he is still developing cinepaint. As I suspected he is developing cinepaint as a platform to test his color management system Oyranos. 

As you can read in here, [http://sourceforge.net/tracker/?func=detail&aid=3428077&group_id=177017&atid=879556](http://sourceforge.net/tracker/?func=detail&aid=3428077&group_id=177017&atid=879556) , his long term plan is to switch to Krita cause is "color managment wise"

I use cinepaint myself to edit my 32 bit floating point images coming from Renderman 3d renderers. But for some reason my tablet's pressure is not recognized in Qneiric, dont know if this is a problem or just a limitation of this version of cinepaint. 

I have been using Krita for a while and it is good, It supports 32 bit floating point images but for some reason the colors of the 32 bit images get darkened when I open them, that sends me back to cinepaint. 

I cant believe this, It is so weird that there isn't an application on Linux to manipulate 32 bit floating point images. There seems to be just cinepaint and it is about to be abandoned. 

Thoughts?

---

### Post by robert shearer on 2011-10-28
> I cant believe this, It is so weird that there isn't an application on Linux to manipulate 32 bit floating point images. There seems to be just cinepaint and it is about to be abandoned.

Thoughts?

Seek and ye shall find....
[http://ubuntuforums.org/showthread.php?t=1868244](http://ubuntuforums.org/showthread.php?t=1868244)

:)

---

### Post by prokoudine on 2011-10-28
> **thrischan said:**
> But for some reason my tablet's pressure is not recognized in Qneiric, dont know if this is a problem or just a limitation of this version of cinepaint. 

GTK+2 is horribly broken in everything that relates to graphic tablets. Things might or might not work at all.

> **thrischan said:**
> I cant believe this, It is so weird that there isn't an application on Linux to manipulate 32 bit floating point images.

What do you mean? darktable does 32bit float, so does delaboratory. None of them have selection tools though.

---

### Post by Favux on 2011-10-28
Oneiric has GTK 3 with GNOME 3.2.

Currently there are some bugs in Oneiric.  See:  [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/863154)  And upstream at the Linux Wacom Project the Button 1 1 bug has been found and fixed but not yet committed to xf86-input-wacom.  So if you are running a xsetwacom script where you are assigning Button 1 1 for the stylus or eraser don't do that for now.  Besides it is the driver default.  Turns out that when they did the switch over to valuators they didn't rename a button release function xsetwacom.c calls on in wcmCommon.c.  Easy fix.

Also GNOME 3.2 introduces the Wacom tablet applet in System Settings.  This first version only uses some of the Wacom hooks that were introduced in the gnome-settings-daemon.  The gnome-settings-daemon key settings will override anything you set in a xorg.conf.d wacom.conf file or in xorg.conf.  The pressure default setting should be linear 0 0 100 100.  But if for some reason the value is different you might want to use dconf-editor to check.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)  Of course a xsetwacom pressure command would override the gnome-settings-daemon key setting.

---

### Post by prokoudine on 2011-10-28
> **Favux said:**
> Oneiric has GTK 3 with GNOME 3.2.

And how is it related to GTK+2 based Cinepaint? :)

---

### Post by thrischan on 2011-10-30
Hi Robert Shearer, Favux and Prokoudine,

**1 -** Unfortunately delaboratory and darktable are not painting or image manipulation tools like gimp or krita. I mean, I can open 32-bit images and manipulate colors or tonemap but I can't paint with brushes and do all the other things you could do with gimp or krita.

I work with 3d software and I work with a "linear workflow". This means I render my images at 32 bit floating point from the 3d renderer. This gives me a lot of flexibility when I'm compositing my images because I have lot of information per pixel and this allows to work lighting and color correction in another level of detail. 

But in order to work in linear mode I also have to work my textures in a linear fashion ( 32 bit ) :-( This is when a ****painting program comes into play.


**2 -** Now, regarding tablet support I asked Kai-Uwe Behrmann again and he told me :

*"The pressure sensitivity depends on drivers and the Gtk toolkit stack. My last stylus tests are from years ago, when I had a graphics tablet available for development. As that device went back, I can not test it right now"*


**3 -** I asked also David Revoy ( [http://www.davidrevoy.com/](http://www.davidrevoy.com/) ) about the krita problem ( 32 bit images are darker when I load them into the program) and he recommended I should report the weird krita behavior  the team so they can fix it for 2.4. I will ask them and keep you updated. 


**Ps:** If you know someone from Krita team and have a way to contact him please let me know, otherwise I will go to the Krita website and send a mail for information :-) Thanks Again.

---

### Post by prokoudine on 2011-11-01
> **thrischan said:**
> **1 -** Unfortunately delaboratory and darktable are not painting or image manipulation tools like gimp or krita. I mean, I can open 32-bit images and manipulate colors or tonemap but I can't paint with brushes and do all the other things you could do with gimp or krita.

Fair enough :)

> **thrischan said:**
> **2 -** Now, regarding tablet support I asked Kai-Uwe Behrmann again and he told me :

*"The pressure sensitivity depends on drivers and the Gtk toolkit stack. My last stylus tests are from years ago, when I had a graphics tablet available for development. As that device went back, I can not test it right now"*

GTK 2.24 is terribly broken with regards to advanced input devices, and nobody's going to fix it. The only thing you can do is to build an earlier version of GTK+ and build Cinepaint yourself against it.

> **thrischan said:**
> **Ps:** If you know someone from Krita team and have a way to contact him please let me know, otherwise I will go to the Krita website and send a mail for information :-) Thanks Again.

IMO, it'a always best to contact the team yourself, because you cut out the middle man :)

---

### Post by Royalist on 2012-05-11
This may answer your queries?

[http://www.cinepaint.org/](http://www.cinepaint.org/)

Roy:)

---

### Post by Horse Racing Tips on 2012-05-11
I hope this msg

---

