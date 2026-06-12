---
title: "[SOLVED] copying files to different directory"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2007-11-04
I have a problem with firefox that started when I tried to install the flash plugin. I have tried a number of different ways and none of them seem to work. (Apt-get, aptitude, etc.)

I have the plugin unzipped on my desktop. 

The mozilla site tells me to copy 'libflashplayer.so' to my Mozilla plugins directory.
I have my mozilla plugins directory open in another window. 
I'll also have to copy "flashplayer.xpt to your Mozilla components directory." and am sure I'll run into the same issue there.

When I try to cut and paste, I am informed that I don't have permission to do this.
I don't know enough to do this through terminal, but should prolly learn it...
Does anyone know how I can get this to work?

---

### Post by chrismine on 2007-11-04
Try sudo nautilus in terminal and type your password if asked.

This gives you root priviliges and should work. Then navigate to your /home/username/desktop and copy the files and then paste into your plugins folder.
Hope it helps.

---

### Post by Papa-san on 2007-11-07
Thank you.
Using Nautilus did just what I needed it to do.

(Now if I could only get the flash plugin to do what IT'S supposed to do! LOL

OK... It worked! I just needed to make sure I navigated to the right directory.

---

