---
title: "nikon cam and capture software - view xn 2 and/or capture equivalent?"
date: 2010-12-11
forum: Art &amp; Design
---

### Post by tomekpilot on 2010-12-11
Greetings!
Is there software that would let me hook up a cam to laptop via usb and when a shot is taken it get displayed on the laptop automatically?

I've seen this at workshop where Niko D7(?) was hooked up to MacBook(Pro?) and when the guy took a shot he could view it on the screen. I think the software was "Camera Control Pro". 

I've been searching for a linux equivalent of that and I'm coming up empty (or I'm misusing what I have, fspot, shotwell, etc.)

Thanks in advance.

---

### Post by robert shearer on 2010-12-12
[http://darktable.sourceforge.net/](http://darktable.sourceforge.net/)

Darktable has tethering for several Nikon models.

otherwise try this in your favourite web browser...
```
site:ubuntuforums.org  camera tethering
```

---

### Post by tomekpilot on 2010-12-12
So can I call you Santa now? I got it to work with Darktable, however as linux noob there was a little snag.

When the camera got plugged in it got mounted as a volumed( I think), F-Spot could see just fine, importing pixes as expected. But Darktable couldn't see it. So I just tried unmounting it, but leaving it plugged in and Darktable could see it then! Magic!

In the meantime I found this as well, and it seems to work like magic as well: [http://photodoto.com/tethered-shooting-with-linux/]("http://photodoto.com/tethered-shooting-with-linux/")

So thanks again! You've made my day.

---

### Post by prokoudine on 2010-12-12
> **tomekpilot said:**
> When the camera got plugged in it got mounted as a volumed( I think), F-Spot could see just fine, importing pixes as expected. But Darktable couldn't see it. So I just tried unmounting it, but leaving it plugged in and Darktable could see it then!

It used to be configurable in GNOME, but alas this applet doesn't seem to be available anymore.

---

### Post by robert shearer on 2010-12-12
> **prokoudine said:**
> It used to be configurable in GNOME, but alas this applet doesn't seem to be available anymore.

Not quite sure of your meaning there but if you are referring to the auto-mounting then I believe that this still applies...
Open your home folder and select Edit>Preferences>Media  and put a check in the box for 'never prompt or start programs on media insertion' 

Then when a disc, camera, external drive is attached/inserted an icon will appear on the desktop.
Left click the icon to access the device, right click for options.

For Tomekpilot, this should allow you to plug in the Nikon, then start Darktable and select the tethering option without the camera first being auto-run at plugin and then having to be un-mounted from that app.. 

Of course nothing else will be auto-run either, though I prefer this behaviour myself. :D   Click to access as required.

---

### Post by prokoudine on 2010-12-12
> **robert shearer said:**
> Not quite sure of your meaning there but if you are referring to the auto-mounting then I believe that this still applies...
Open your home folder and select Edit>Preferences>Media  and put a check in the box for 'never prompt or start programs on media insertion' 

That's exactly the applet I was referring to, but my 10.04 installation is missing it. I wish I knew why.

---

### Post by robert shearer on 2010-12-12
> **prokoudine said:**
> That's exactly the applet I was referring to, but my 10.04 installation is missing it. I wish I knew why.
 Works here on 10.04 and 10.10. Both standard installs and Gnome desktop.

Maybe.... alt-F2 and type  "gconf-editor", enter, then navigate to  Apps>Nautilus>Preferences

Scroll down and there is a line.." media_autorun_never" and this has a tick in it for my set-up. 
I am presuming that this is the 'under-the-hood' adjustment made by using the steps in my last post.

You may want to try setting manually by placing a tick there yourself and logging out and in again to see the result.

I don't know enough about gconf-editor so this is a guess and worth just that.
Perhaps some-one more familiar with it can enlighten us..:)

---

### Post by prokoudine on 2010-12-12
> **robert shearer said:**
> 
Maybe.... alt-F2 and type  "gconf-editor", enter, then navigate to  Apps>Nautilus>Preferences

Oh well, *Nautilus*. Dunno what I was thinking about :) Thanks for the tip!

---

### Post by tomekpilot on 2010-12-13
... so I put a little bit of time in playing with the camera and Darktable and a follow up question emerges about Darktable.

I've noticed that it will not always capture/display the photo even though the camera takes it. I thought maybe it's only in a case when the subject is too dark, but turns out even if I use flash it will fails to show it. However, no matter the light conditions when I hit 'capture image(s)' the camera goes off and it shows the image even if it's pitch dark.

Am I missing something or is this just the peculiar behavior of Darktable?

---

### Post by robert shearer on 2010-12-13
Darktable is a work in progress.
Draft user manual here.....[http://darktable.sourceforge.net/darktable-usermanual-draft-20101022.pdf](http://darktable.sourceforge.net/darktable-usermanual-draft-20101022.pdf)

This thread.....[http://ubuntuforums.org/showthread.php?t=1480098](http://ubuntuforums.org/showthread.php?t=1480098)
is visited by one of the Darktable developers....dinamic78
[http://ubuntuforums.org/member.php?u=689438](http://ubuntuforums.org/member.php?u=689438)

You could post your questions about Darktable and tethering there for a more comprehensive viewing.

There is also the Darktable contact page ...[http://darktable.sourceforge.net/contact.shtml](http://darktable.sourceforge.net/contact.shtml)

Unfortunately, my camera does not support tethering much to my regret, so my experience is limited.
All the best for your adventure..:D

**Edit**... I see **prokoudine**  is also on the Darktable team :)
perhaps he can comment on your findings here ??....

---

### Post by prokoudine on 2010-12-13
> **tomekpilot said:**
> I've noticed that it will not always capture/display the photo even though the camera takes it. I thought maybe it's only in a case when the subject is too dark, but turns out even if I use flash it will fails to show it. However, no matter the light conditions when I hit 'capture image(s)' the camera goes off and it shows the image even if it's pitch dark.

Oh, it could be a gPhoto issue. For some cameras, for example, gPhoto won't download captured images at all. We have a somewhat outdated page that covers support for various cameras re some features including tethering [here]("http://darktable.sourceforge.net/documentation.shtml"). Your primary contact indeed would be dinamic78, because he was the person who implemented tethering mode.

---

### Post by prokoudine on 2010-12-13
> **tomekpilot said:**
> I've noticed that it will not always capture/display the photo even though the camera takes it. I thought maybe it's only in a case when the subject is too dark, but turns out even if I use flash it will fails to show it. However, no matter the light conditions when I hit 'capture image(s)' the camera goes off and it shows the image even if it's pitch dark.

Oh, it could be a gPhoto issue. For some cameras, for example, gPhoto won't download captured images at all. We have a somewhat outdated page that covers support for various cameras re some features including tethering [here]("http://darktable.sourceforge.net/documentation.shtml"). Your primary contact indeed would be dinamic78, because he was the person who implemented tethering mode. You can also refer to [http://www.gphoto.org/doc/remote/]("http://www.gphoto.org/doc/remote/") for information about your camera and tethering with gPhoto.

---

### Post by dinamic78 on 2010-12-13
> **robert shearer said:**
> Darktable is a work in progress.
Draft user manual here.....[http://darktable.sourceforge.net/darktable-usermanual-draft-20101022.pdf](http://darktable.sourceforge.net/darktable-usermanual-draft-20101022.pdf)

This thread.....[http://ubuntuforums.org/showthread.php?t=1480098](http://ubuntuforums.org/showthread.php?t=1480098)
is visited by one of the Darktable developers....dinamic78
[http://ubuntuforums.org/member.php?u=689438](http://ubuntuforums.org/member.php?u=689438)

You could post your questions about Darktable and tethering there for a more comprehensive viewing.

There is also the Darktable contact page ...[http://darktable.sourceforge.net/contact.shtml](http://darktable.sourceforge.net/contact.shtml)

Unfortunately, my camera does not support tethering much to my regret, so my experience is limited.
All the best for your adventure..:D

**Edit**... I see **prokoudine**  is also on the Darktable team :)
perhaps he can comment on your findings here ??....

Evning, what camera do you use, gphoto2 project did announce a new version with new tethereing support for older Canon cameras.

[http://sourceforge.net/mailarchive/forum.php?thread_name=20101212222947.GB18077%40jet.franken.de&forum_name=gphoto-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20101212222947.GB18077%40jet.franken.de&forum_name=gphoto-devel)

/Henrik

---

### Post by dinamic78 on 2010-12-13
> **tomekpilot said:**
> ... so I put a little bit of time in playing with the camera and Darktable and a follow up question emerges about Darktable.

I've noticed that it will not always capture/display the photo even though the camera takes it. I thought maybe it's only in a case when the subject is too dark, but turns out even if I use flash it will fails to show it. However, no matter the light conditions when I hit 'capture image(s)' the camera goes off and it shows the image even if it's pitch dark.

Am I missing something or is this just the peculiar behavior of Darktable?

Hi there, go thru these steps to verify the functionality with your camera:

[http://sourceforge.net/apps/trac/darktable/wiki/CaptureCameraSupport](http://sourceforge.net/apps/trac/darktable/wiki/CaptureCameraSupport)

/Henrik

---

### Post by tomekpilot on 2010-12-13
Indeed. Thanks for all the help, I'm amazed by all the options that became available to do this :-)

---

