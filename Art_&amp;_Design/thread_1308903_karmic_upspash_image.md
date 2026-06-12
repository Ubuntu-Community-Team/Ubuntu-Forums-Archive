---
title: "karmic upspash image"
date: 2009-11-01
forum: Art &amp; Design
---

### Post by mrpeachy on 2009-11-01
is there anywhere that i can get the white ubuntu image that shows up on bootup?
does it exist somewhere as an image in the file system?

i want to edit the xsplash images so that the bootup is more aesthetically continuous (plus i dont like the brown)

thanks

---

### Post by hyperdude111 on 2009-11-01
If you download the source you can edit the image then compile it.

Download here [http://launchpadlibrarian.net/34157382/xsplash-0.8.5.tar.gz](http://launchpadlibrarian.net/34157382/xsplash-0.8.5.tar.gz)

---

### Post by mrpeachy on 2009-11-01
Thanks! 
I'm also looking for the usplash image that comes up first at boot, just the white ubuntu circle that appears in the middle of the screen.
The ubuntu logo in the source file you pointed to is the circle and text and it has an "aura" around it, so i cant edit out the ubuntu text to just leave the circle.

---

### Post by Anonymousable on 2009-11-01
Here it is. 

To get the smaller ones used on lower resolutions, use ```
apt-get source usplash-theme-ubuntu
```It creates several files though. Find the folder it creates, and you'll see all of the logos there.

---

### Post by mrpeachy on 2009-11-01
perfect.  

thanks all!

---

### Post by Shnatsel on 2009-11-03
I've recompiled the Karmic usplash from source with custom images, but they show up only on shutdown. I see the same Ubuntu default usplash on startup. Is there any way to get rid of this? I can attach the custom sources and binary library if needed.
**EDIT:** Solved this, thanks. I had to update the initial ram disk to apply changes.

---

### Post by jnew93 on 2009-11-04
> **Shnatsel said:**
> I've recompiled the Karmic usplash from source with custom images, but they show up only on shutdown. I see the same Ubuntu default usplash on startup. Is there any way to get rid of this? I can attach the custom sources and binary library if needed.
**EDIT:** Solved this, thanks. I had to update the initial ram disk to apply changes.

Interesting! I'll have to give this a go myself. Was it difficult overall?

---

### Post by Shnatsel on 2009-11-05
No, it wasn't difficult, it just requires correct approach. These two tutorials explain how to customize USplash: [https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash) and [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto). Actually, when I tried to follow the customization tutorial, I found it far too complex to deal with. Instead I downloaded ubuntu usplash artwork source code ([FONT="Courier New"]apt-get source usplash-theme-ubuntu[/FONT] without [FONT="Courier New"]sudo[/FONT]) and changed the images. In Karmic you don't need a progress bar so it's the easiest way to customize USplash for Karmic. Just remember you need an indexed PNG. If you use a non-indexed one, you'll get nothing but black screen. 
If you need any details, drop me a line, I'll try to explain everything.

---

### Post by szerencsefia on 2009-11-08
> **Shnatsel said:**
> No, it wasn't difficult... 
If you need any details, drop me a line, I'll try to explain everything.

Thanks man. I actually have two questions.
1. After the modification how can I make a deb file from the source? (What is the code)
2. After the deb file is created how can I replace the original with the new one? What'd have to be change to use the one I created instead?

---

### Post by Shnatsel on 2009-11-09
> **szerencsefia said:**
> 1. After the modification how can I make a deb file from the source? (What is the code)
2. After the deb file is created how can I replace the original with the new one? What'd have to be change to use the one I created instead?1. Go to the folder with the source code and execute [FONT="Courier New"]debuild[/FONT], or [FONT="Courier New"]debuild -us -uc[/FONT] if you don't want to mess with signatures. Or, if you don't need to redistribute the custom image, you can leave messing with DEBs to geeks and simply run 'make' in the folder with the source code. This will build usplash-theme-ubuntu.so file, your custom splash.
2. If you didn't change the name of resulting package, just install your DEB. [USplash]("https://help.ubuntu.com/community/USplash") article in the wiki explains what you need to do if you've changed the names of package and splash file. You need to run [FONT="Courier New"]sudo update-alternatives --config usplash-artwork.so[/FONT] and choose your theme there or simply remove the usplash-theme-ubuntu package. If you didn't use DEBs, replace the /usr/lib/usplash/usplash-theme-ubuntu.so with your custom splash file. Don't forget to update the initial ramdisk after any of this (run [FONT="Courier New"]sudo update-initramfs -u[/FONT]).

---

