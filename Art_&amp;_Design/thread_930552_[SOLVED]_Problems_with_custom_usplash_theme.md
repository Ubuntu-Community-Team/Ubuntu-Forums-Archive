---
title: "[SOLVED] Problems with custom usplash theme"
date: 2008-09-26
forum: Art &amp; Design
---

### Post by MacUntu on 2008-09-26
I modified the standard usplash-theme-ubuntu to better fit my 1280x768 widescreen monitor.

I therefor used GIMP to crop the original wallpaper to 1280x768. I then changed the mode to RGB, resized the image to 1024x768 (because that image version is chosen by usplash, just replaced it later), added the progress bar images, reindexed to 256, did some cropping, and ended with:
- A new 1024x768 wallpaper with a squished logo, and
- The two progress bar images.
All three using the same palette (which got a bit mixed up so I changed the colors in the usplash-theme-ubuntu.c source file to represent the "old" colors).

Result after compiling: The logo is shown correctly without any distortions but the text area is dark blue - strange, because it should be black and there is no dark blue in the color palette used by the images. If I change the console resolution to 1024x768 (vga=791) the blue is gone but the console text looks bad. If I use the original theme there is no blue either, so there's definitively a problem with the above procedure.

Any hints?

---

### Post by smartboyathome on 2008-09-27
Usplash can only use 16 bit color. I am guessing you didn't convert it to that.

---

### Post by MacUntu on 2008-09-27
16? AFAIK it can only handle 8 bit colors. That's why all the images have indexed 256 color palettes.

I will try to preserve the original palette by directly inserting the squished logo in the original wallpaper, maybe that helps.

Edit: Tried as said. I now didn't touch any files except the 1024x768 background image into which I pasted the squished logo. Same palette as original, same source file as original, and: NO blue background. So I guess I have to look a little more into the files I created in the first place.

---

### Post by MacUntu on 2008-09-27
Ok, it turns out that the original ubuntu theme had the same blue box but hardly visible. So no usplash thingy - it was a "wrong" console resolution.

I had no "vga=..." in my kernel line in /boot/grub/menu.lst and changed it to "vga=792". 

That fixed the problem.

---

