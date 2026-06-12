---
title: "Resolution issue : Kubuntu running in VirtualBox under OS X"
date: 2009-05-01
forum: Apple Hardware Users
---

### Post by theraccoonbear on 2009-05-01
Hello Anyone Reading This!

I've got a MacBook Pro running OS X 10.5.6 that I recently installed VirtualBox 2.2.2 onto and then installed Kubuntu 9.04 from a downloaded ISO to a VirtualBox image.  I've installed the "guest additions" (I believe that was the name) and added the "vboxvideo" bit to my xorg.conf.  I've setup the xorg.conf for Kubuntu to use the MacBook's native 1900x1200 resolution and the computer goes through its text and lo-res graphical boot screens, and then brings up the KDE login screen at 1900x1200.  Perfect, right?  Well, once I login, I get the splash graphic with the icons coming into focus as KDE loads, and then right when the desktop proper starts up, the display gets weird.  I've seen weird video driver issues where color/scale were off, but this is different.  It appears that the 1900x1200 is trying to be displayed in the top half of a display that's setup at 1024x768 (as reported by VirtualBox's diagnostic Machine -> Session Information -> Runtime Attributes).

Anyway, I've attached some screenshots of what I see before, during, and after login.  I'm not sure if the issue is with VirtualBox or Kubuntu, but I thought I might start here.  Hopefully someone can provide some guidance on this.  Thanks in advance.

---

### Post by cyberdork33 on 2009-05-01
Do you have 3Dacceleration enabled in the setup? Try disabling it.

---

### Post by theraccoonbear on 2009-05-02
Nope, no 3d acceleration.

---

### Post by cyberdork33 on 2009-05-02
> **theraccoonbear said:**
> Nope, no 3d acceleration.
i'd guess it was a bug with the virtualbox driver... you can set xorg to use the framebuffer (fbdev) and it should at least display.

---

### Post by theraccoonbear on 2009-05-04
That seems odd though.  Why would everything be fine up until the KDE login?  The VirtualBox video driver would've been loaded since the graphical login was presented and everything looks fine up until that point.

---

### Post by cyberdork33 on 2009-05-04
> **theraccoonbear said:**
> That seems odd though.  Why would everything be fine up until the KDE login?  The VirtualBox video driver would've been loaded since the graphical login was presented and everything looks fine up until that point.
because xorg doesn't start until the login screen (and the xorg video driver isn't loaded until then).

---

### Post by theraccoonbear on 2009-05-04
The screenshots clearly show the display working for both the login screen and the KDE startup splash animation.  Are you saying that the login screen and the KDE startup are using a different driver and then KDE switches drivers?  I don't know all the ins and outs of either X or KDE in any deep way, but that sounds awfully odd.

---

### Post by cyberdork33 on 2009-05-04
Why don't you try the workaround I suggested, see of that is any better and we can narrow down what part of the system to put the blame on.

---

### Post by theraccoonbear on 2009-05-04
OK, I changed the the driver from vboxvideo to fbdev and X failed to start.

Attached is a screenshot of what I see of interest at the end of /var/log/Xorg.0.log (I'm not sure how to copy/paste from the VirtualBox sessions so I used a screenshot)

---

### Post by cyberdork33 on 2009-05-04
looks like vbox is not proiding a framebuffer device... that seems strange... you could try the "vga" driver or the "vesa" driver which are just generic drivers (This will probably give you a really low resolution, but you should get a desktop.)

It might be the resolution that the desktop is trying to use as well. the login screen often uses a limited resolution.

---

### Post by theraccoonbear on 2009-05-04
I may try the other generic drivers and see what I can get.

Something smells fishy with all of this though because right now I get the login window and the login process running fine at 1900x1200 (not a lower resolution) but it's only when the KDE desktop proper starts that things go haywire.

I can run with the vboxvideo driver and get a resolution of around 1024x768 at login, and then when the desktop is running too, without any issues, but doing it at that low resolution with either vboxvideo or fbdev or vga or whatever is really a deal breaker for me.  If I can't get full native resolution it's just not worth it, IMO.

Thanks for your ideas though, I do appreciate it.  If anything else occurs to you as a possible cause or solution, please do post back here.

I may hit the VirtualBox forums to see if anyone there has experience with an issue like this.  If I do come up with something, I'll try to post the resolution back here on this thread.

---

### Post by cyberdork33 on 2009-05-05
> **theraccoonbear said:**
> Something smells fishy with all of this though because right now I get the login window and the login process running fine at 1900x1200 (not a lower resolution) but it's only when the KDE desktop proper starts that things go haywire.This is why I thought 3D Acceleration at first. The login screen doesn't use that, but the desktop would. Vbox recently added 3D Acceleration support for Linux guests, but it is a bit buggy still. 

> **theraccoonbear said:**
> I can run with the vboxvideo driver and get a resolution of around 1024x768 at login, and then when the desktop is running too, without any issues, but doing it at that low resolution with either vboxvideo or fbdev or vga or whatever is really a deal breaker for me.  If I can't get full native resolution it's just not worth it, IMO.I agree, just debugging here.


I would double-check in your VM settings that the 3D Acceleration checkbox is not checked. Other than that, I would say that it is trying to use the wrong res at the desktop or something along those lines. getting the xorg log file might help a bit. (Can you switch to a console when the screen gets garbled with Fn+Ctrl+Alt+F1)

---

### Post by 10011010 on 2009-05-23
You might check the video card in the Mac, I know Jaunty had a fit with my ATi card, drivers still on the way.  I imagine virtualbox will be using xorg binary fglrx drivers if it is an ati card, and that could be the reason for your screen in kde.  mine looked a lot like that.

---

