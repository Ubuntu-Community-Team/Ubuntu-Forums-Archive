---
title: "My pictures won't match their rotation."
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-08-03
This is the one thing about Ubuntu that really enrages me, because it's something so simple yet despite 7 or 8 threads here, I've got nothing.

Just got home from vacation, took 960 pictures. Uploaded them all to my typical Pictures folder. The thumbnails show certain pictures turned, so I'll double click them to get the full version and correct them. The way they are turned in the full screen image is ALWAYS different than the thumbnail and it drives me absolutely insane. Why is it the thumbnail will be turned, yet when I see the full version, it's straight? Sometimes they're straight in the thumbnail, yet turned in the big picture. I see no reason for this, and I've been having trouble locating people with the same problem.

---

### Post by happy-and-lost on 2007-08-03
You could delete your *~/.thumbnails* folder, forcing them to refresh. This is probably a Gnome bug.

---

### Post by avik on 2007-08-03
Here's the problem: you had some thumbnails, then you edited the pictures.  However, the old thumbnails weren't updated.  Like happy-and-lost said, delete the thumbnails, and they'll refresh.

It's not a bug.

---

### Post by Roasted on 2007-08-03
sudo rm -rf ~/.thumbnails

???????????

---

### Post by callan79 on 2007-08-03
> **Roasted said:**
> Just got home from vacation, took 960 pictures. Uploaded them all to my typical Pictures folder. The thumbnails show certain pictures turned, so I'll double click them to get the full version and correct them. The way they are turned in the full screen image is ALWAYS different than the thumbnail and it drives me absolutely insane.


Hi There,

I not sure which image viewing software you're using, but I too have had issues with pictures rotating sideways and also the thumbnail does not match the image.

I use GQVIEW as my viewer, and in the options there is a setting to auto-rotate the image. This seems to work really well.

BUT, when I download the pics from the camera, there is an option to rotate the images physically. If I select this option, then GQVIEW starts showing images sideways.

It seems that this 'rotate images physically' has a problem, so I recommend you DO NOT do it.

This info might not fix your 960 images, but I hope it helps!

Cheers
Callan

---

### Post by Roasted on 2007-09-16
Just curious... that folder, the ./ folder, how can you get all of them to show? How would anybody know offhand to delete the thumbnail folder to refresh it?

---

