---
title: "Dead slow with pictures"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by dbvanhorn on 2007-10-27
I'm having the same problem with gutsy that I had with fiesty.

I have one drive that has a large collection of pictures that I've taken over the years.
Multiple formats, mostly jpg and bmp.

XP handles this drive just fine.  I can navigate, select and move files, no problem.
With either version of ubuntu, and with debian on the same hardware, when I open the top level directory with images, it takes forever (apparently) to become ready.

The system is a dual core 64 bit athlon with 2G ram and 3G swap, The drive in question is a western digital 500G PATA.

Running top during it's effort to open the directory shows that within a few minutes, all of ram and all of swap is in use.   I've seen load numbers around 1.6-3.5 as well. Normally, the system runs at a load average of 0.2, with 1.5G free ram and 2.5G free swap

What can I do to prevent this?

---

### Post by kerry_s on 2007-10-27
> **dbvanhorn said:**
> I'm having the same problem with gutsy that I had with fiesty.

I have one drive that has a large collection of pictures that I've taken over the years.
Multiple formats, mostly jpg and bmp.

XP handles this drive just fine.  I can navigate, select and move files, no problem.
With either version of ubuntu, and with debian on the same hardware, when I open the top level directory with images, it takes forever (apparently) to become ready.

The system is a dual core 64 bit athlon with 2G ram and 3G swap, The drive in question is a western digital 500G PATA.

Running top during it's effort to open the directory shows that within a few minutes, all of ram and all of swap is in use.   I've seen load numbers around 1.6-3.5 as well. Normally, the system runs at a load average of 0.2, with 1.5G free ram and 2.5G free swap

What can I do to prevent this?

 sounds like there's 2 many pics in 1 folder, you should split them up in to sub folders so it does not have to cache them all for quick viewing. the better you organize the faster it can be. :)

---

### Post by dbvanhorn on 2007-10-27
Well, that's obvious I guess, but XP handles it just fine, and in order to do that. I'd have to scrub ubuntu again, reinstall XP, organize, and then reverse that. 

Seems to me like ubuntu ought to be able to handle it.

---

### Post by taurus on 2007-10-27
What filesystem is that harddrive?

---

### Post by kerry_s on 2007-10-27
> **dbvanhorn said:**
> Well, that's obvious I guess, but XP handles it just fine, and in order to do that. I'd have to scrub ubuntu again, reinstall XP, organize, and then reverse that. 

Seems to me like ubuntu ought to be able to handle it.

okay you lost me, why would you have to scrub ubuntu and install xp?
you just create the folders(tip:use the shortcut side bar to hold the folders) then just drag and drop the pics where you want(drag and drop on the short cut folders).

---

### Post by dbvanhorn on 2007-10-27
> **taurus said:**
> What filesystem is that harddrive?

It's EXT3 now, the system used to be XP and the drive was NTFS then.

---

### Post by dbvanhorn on 2007-10-27
> **kerry_s said:**
> okay you lost me, why would you have to scrub ubuntu and install xp?
you just create the folders(tip:use the shortcut side bar to fold the folders) then just drag and drop the pics where you want(drag and drop on the short cut folders).


Riiiight..  But when I open the folder with the pictures, it takes so long to open that folder, that I don't know how long it takes.  I've tried waiting several hours.  Within a few minutes, it's eaten 2G ram and 3G swapspace.

That's my problem, it's unmaintainable this way.

---

### Post by argie on 2007-10-27
Nautilus is thumbnailing. Edit » Preferences » Preview. There, disable thumbnails. Alternatively, if you'd like thumbnails enabled, make a launcher for Eye of Gnome. The command is 'eog'. Then just browse to the relevant folder like that.

---

### Post by Can+~ on 2007-10-27
> **argie said:**
> Nautilus is thumbnailing. Edit » Preferences » Preview. There, disable thumbnails. Alternatively, if you'd like thumbnails enabled, make a launcher for Eye of Gnome. The command is 'eog'. Then just browse to the relevant folder like that.

Yeah, same thing happened to me. Windows XP does not create thumbnails of pictures in "list view", but nautilus does. You can also reduce the size of pictures thumbnails; the default is "5MB", I guess with "1MB" or "500KB" it will work ok.

---

### Post by nelson.bolanos on 2007-10-27
Not sure if XP does the preview Ubuntu does, so, for a faster display you could try navigating in nautilus, edit > preferences, and in the preview tab, you can disable it for large pictures, so it takes a short time to load that directory, or you could disable it.:guitar:

---

### Post by dbvanhorn on 2007-10-27
> **argie said:**
> Nautilus is thumbnailing. Edit » Preferences » Preview. There, disable thumbnails. Alternatively, if you'd like thumbnails enabled, make a launcher for Eye of Gnome. The command is 'eog'. Then just browse to the relevant folder like that.

Ok, that helped TONS.  It still takes maybe 20 seconds to open the top level folder, but that's a big improvement.  

Thing is, XP does thumbnail, and it does it about as fast as Ubuntu does without thumbnailing.

But, this is at least a way to limp till I find a whole solution.

---

### Post by argie on 2007-10-28
Nice to hear.

Nautilus isn't perfect. Perhaps you can try another file manager. Maybe Thunar would work better.

---

### Post by jpangamarca on 2008-03-12
> **Can+~ said:**
> Yeah, same thing happened to me. Windows XP does not create thumbnails of pictures in "list view", but nautilus does. You can also reduce the size of pictures thumbnails; the default is "5MB", I guess with "1MB" or "500KB" it will work ok.

Having the same problem here. How can I reduce the thumbnail size? :confused:

---

### Post by jpangamarca on 2008-03-12
> **jpangamarca said:**
> Having the same problem here. How can I reduce the thumbnail size? :confused:

Forget it. I found out. But that really wouldn't help. I have some folders with 500+ images but none of those images is bigger than 5 MB, and it's still slow as an old turtle! Any workaround?

---

