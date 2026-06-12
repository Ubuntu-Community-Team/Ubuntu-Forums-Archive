---
title: "google earth black screen issue"
date: 2006-06-27
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-06-27
whenever google earth is opened, the right screen that's supposed to show planet earth is all black. i've tried maximizing the window and setting it back to normal, but that only causes my computer to lock up not able to revived (even with ctrl+alt+backspace)

---

### Post by shanepardue on 2006-06-29
any google earth experts?

---

### Post by MarkSheely on 2006-06-29
The only thing I can think to suggest is to go to the menu,

view -> view size -> computer playback -> 800x600 

Let me know if that doesn't work.  

Also, look on the google earth forums, here:
[http://bbs.keyhole.com/ubb/ubbthreads.php/Cat/0](http://bbs.keyhole.com/ubb/ubbthreads.php/Cat/0)

They may have a category for discussing these kinds of problems.
-Mark

---

### Post by shanepardue on 2006-06-29
that did not work.

i did post this on the google board too so hopefully that will help!

i appreciate your help! (and if any other ideas surface, that's cool too! ha)

---

### Post by WoodyMahan on 2006-09-01
Hi All

I recently installed Google Earth via Automatix on a Desktop and a Laptop and both of them show black in the box where the Globe should display.  I have only about 1/5 of the globe available at the top of the box.  Has anyone gotten a fix for this?

Thanks

---

### Post by blacktorch on 2006-10-11
I have the same issue... parts of the globe is black/purple/other colour, and flickering...

---

### Post by PriceChild on 2006-10-11
Have you all got 3D drivers working and installed?
```
glxinfo
``` Should report Yes to direct rendering at the top.

Secondly... using beryl or compiz?

---

### Post by blacktorch on 2006-10-11
It reports yes... and I have an Nvidia 6200TC, by the way. Warcraft 3, CS, WoW and Neverball all work.

I don't know, metacity? Haven't changed the window manager...

---

### Post by blacktorch on 2006-10-11
This is how it looks like, by the way:
[http://img237.imageshack.us/my.php?image=skrmdumprw6.png](http://img237.imageshack.us/my.php?image=skrmdumprw6.png)

---

### Post by cacharreo on 2006-10-11
Run googleearth in root mode:
***sudo googleearth***

---

### Post by PriceChild on 2006-10-11
> **cacharreo said:**
> Run googleearth in root mode:
***sudo googleearth***Please use gksudo for graphical apps.

Also have you tried installing straight from google? I've never had a problem with it.

---

### Post by blacktorch on 2006-10-11
I tried (gk)sudo /opt/bin/googleearth, but the problem persists...

No, I haven't tried that, but I don't see why it should be any different, though.

---

### Post by blacktorch on 2006-10-11
I did sudo apt-get remove googlearth, then I downloaded and installed directly from Google as you suggested, and as suspected, there was no change.

---

### Post by blacktorch on 2006-10-12
No one?

---

### Post by ajm2005 on 2006-10-25
> **blacktorch said:**
> No one?

yes, I had exactly the same problem. It turns out there is a bug with the current NVIDIA drivers with the 6200TC (which I have, and which you mentioned you have). NVIDIA has fixed the bug in the latest (beta) drivers (1.0-9625). I installed the beta drivers, and google earth works fine now.

Are you using Dapper or Edgy ubuntu?

---

### Post by Offoffoff on 2008-03-29
I have i915G integrated video card and I confirm this bugs. Google Earth flickering makes me mad. I don't want to shutdown compiz, because other applications work right.

---

### Post by borisattva on 2008-05-17
i had exact same issue.

i did

cd /home/borisattva/google-earth
sudo sh googleearth 

and it worked

it did not work from anywhere else.

i'm guessing without sudo the application is unable to get the internet access

does anyone know how to make each application menu launch to be acted like sudo?

---

