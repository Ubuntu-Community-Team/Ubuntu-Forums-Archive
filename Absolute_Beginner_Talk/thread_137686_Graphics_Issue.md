---
title: "Graphics Issue"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by uncleant on 2006-02-28
My lastest issue involves the behavior of my open windows.  When I move an open window such as firefox, oo writer or terminal, there seems to be a trail of shadows that follows.  They go away as soon as I get the window where I want it.  I'm guessing that it's either a driver issue or a settings issue.  Any help would be greatly appreciated.

---

### Post by shof2k on 2006-02-28
Post details of your computer and the graphics card that you're using. Hopefully someone will have a similar card and the way to get more out of it.

To see what your graphics card is like now type the following into a terminal.

glxgears -printfps
glxinfo|grep rendering

The 1st will see how many frames the program will draw.  The 2nd see's if you have any hardware acceleration.

---

### Post by uncleant on 2006-02-28
I don't have a separate video card.  The graphics are Integrated S3 UniChrome 2D/3D Graphics on an ECS KM400-M2 motherboard.  I'll try those commands tonight when I get home and I'll post the results.

---

### Post by Ramses de Norre on 2006-02-28
```
gconf-editor /apps/metacity/general
```
You can check the box 'reduced_resources', a lot of things (like moving windows) will look less pretty but your pc will run smoother.
It's appearance vs. performance ;)

---

### Post by uncleant on 2006-02-28
So are you saying this is normal behavior for ubuntu?  If it's something that can be simply turned off, I'm all for it.  I find the shadowing to be quite annoying.

---

### Post by Ramses de Norre on 2006-02-28
I think that maybe your machine isn't fast enough to show those graphics properly. I turned it off myself because I prefer the faster performance.

---

### Post by uncleant on 2006-02-28
** (gconf-editor:8545): WARNING **: Invalid borders specified for theme pixmap:
        /home/hank/.themes/d3a/gtk-2.0/list_header.png,
borders don't fit within the image
hank@globex03:/home$ glxgears -printfps
615 frames in 5.4 seconds = 113.345 FPS
600 frames in 5.6 seconds = 107.888 FPS
600 frames in 5.6 seconds = 107.936 FPS
600 frames in 5.5 seconds = 109.018 FPS
600 frames in 5.5 seconds = 109.708 FPS
600 frames in 5.5 seconds = 109.455 FPS
600 frames in 5.5 seconds = 109.088 FPS
600 frames in 5.5 seconds = 108.175 FPS
600 frames in 5.5 seconds = 109.667 FPS
600 frames in 5.4 seconds = 110.414 FPS
600 frames in 5.5 seconds = 110.026 FPS
600 frames in 5.5 seconds = 109.266 FPS
600 frames in 5.5 seconds = 109.121 FPS
600 frames in 5.5 seconds = 109.530 FPS
600 frames in 5.5 seconds = 108.409 FPS
600 frames in 5.5 seconds = 109.826 FPS
600 frames in 5.5 seconds = 109.812 FPS
600 frames in 5.5 seconds = 109.813 FPS
600 frames in 5.5 seconds = 109.253 FPS
600 frames in 5.5 seconds = 109.682 FPS
600 frames in 5.4 seconds = 110.189 FPS
600 frames in 5.5 seconds = 109.932 FPS
600 frames in 5.5 seconds = 109.415 FPS
600 frames in 5.5 seconds = 109.772 FPS
600 frames in 5.5 seconds = 109.945 FPS
600 frames in 5.5 seconds = 109.163 FPS
600 frames in 5.5 seconds = 109.819 FPS
600 frames in 5.5 seconds = 109.955 FPS
600 frames in 5.5 seconds = 109.918 FPS
600 frames in 5.5 seconds = 109.367 FPS
600 frames in 5.5 seconds = 109.640 FPS
600 frames in 5.4 seconds = 110.229 FPS
600 frames in 5.5 seconds = 109.871 FPS
600 frames in 5.5 seconds = 109.967 FPS
600 frames in 5.7 seconds = 105.058 FPS

---

### Post by Ramses de Norre on 2006-03-01
> ** (gconf-editor:8545): WARNING **: Invalid borders specified for theme pixmap:
/home/hank/.themes/d3a/gtk-2.0/list_header.png,
borders don't fit within the image
Is that what the command returns? Did it open the conf editor? (you can also open it by applications > system tools > configuration editor and go to the path I gave you).

And that frame rates are pretty low I think, I don't know what is default but mine are like 1700 fps..

I would definitely turn on the reduced resources.

---

### Post by shof2k on 2006-03-01
I agree. I have a built in Intel i845 board and can get ~500 fps with hardware acceleration.

You could also try using the bleeding edge drivers at freedesktop.org to see if you can get better performance.

---

