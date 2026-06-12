---
title: "Cinema 4D R10 - Wine - Ubuntu"
date: 2007-09-09
forum: Art &amp; Design
---

### Post by Jaryth on 2007-09-09
Ok! So! Cinema 4D, one of the most useful 3D programs Iv ever used (and Iv used a fair bit) out of 3Ds Max, Maya, and Blender, I still pick Cinema 4D.

Well, Iv been using Cinema 4D on windows for a few years now... since back in R7... right up to R10. And it runs fine on windows.

As of late however Iv been using Linux (Ubuntu) for my OS (however I have a Multi Boot system, so I can still use all of my windows programs), but Iv been trying to get Cinema working in Linux...

Well, though Wine I have... kinda... Succeeded... C4D runs... it.. 'Works' but its far from perfect. its quite slow, and... I don't know why but it likes to.. erm... turn black...
Here, I have a screencap:
[http://img.photobucket.com/albums/v481/jaryth000/blackC4D.jpg](http://img.photobucket.com/albums/v481/jaryth000/blackC4D.jpg)

Everything still works... I can create objects I can move them around... The black areas come and go... Menus still appear to work (if I can find them). Sometimes none of it is black (rarely).

I was however able to mess around enough to render a (VERY) simple picture, (Screen cap: [http://img.photobucket.com/albums/v481/jaryth000/C4DRenderandworking.jpg](http://img.photobucket.com/albums/v481/jaryth000/C4DRenderandworking.jpg) )

After doing a bit of searching here I haven't found much... and a bit more searching on the web suggested using WineTools to make it work, but WineTools does not want to work for me...

Im amazed Iv gotten this far, but if I could get Cinema 4D working completely on Linux I would be... purely amazed... and then I would have very little, if not no reason to go back to Windows.

So, does anyone have any suggestions, questions, and or help they could give me on this? Ether to make it faster somehow, or to make the black marks go away.

(Also, I know Cinema 4D may not be the most popular application, but any help on running Windows programs on Linux in general is also welcome if it apples)(and Im also not totally sure if this is where this topic should go... but Ill put it here, because it is strongly to do with art)(Finally, as a shameless plug, if anyone wants to see what I do with Cinema 4D: [http://jaryth000.deviantart.com/gallery/](http://jaryth000.deviantart.com/gallery/) )

Thanks!

-Jaryth

---

### Post by Jaryth on 2007-09-09
**UPDATE:**

After some more searching and golden find on the Wine site, I found how to fix it!
Edit > Preffrences > Viewport > Options > Change the OpenGL shading to Software Shading!

Everything works as far as I can tell... Although it still lags... pretty bad compared to running it natively on Windows XP... HOWEVER It still detects my Dual Core, and takes full advantage of that during rendering. (after running a few tests) Rendering is a BIT slowed down, but only by a bit (on a test render that I would usually average about 3 minutes and 30 seconds for, C4D on Linux took 3 minutes and 54 seconds)

the only other issue being the decreased preview quality of Software shading (but a slight loss in quality is still better then most of the screen turning black).


Yey for Cinema 4D! Yey for Wine! Yey for Ubuntu! and Yey for Linux!

---

### Post by mech7 on 2007-09-09
if you are serious about working with 3d get an app that runs nativly.. blender, maya, xsi, houdini are very good programs.

---

### Post by kayosiii on 2007-09-13
Yeah that bug also appears when trying to run sketchup...
There was a patch created a while back but obviously hasn't made it into wine proper which is a PITA... Maybe somebody should draw it to the wine devs attention.

---

### Post by Lwangaman on 2008-02-11
I also have been using Windows XP up until just recently, and I have begun using Cinema 4d which I am very satisfied with; lately I've been  switching over to Linux Ubuntu as an operating system and I don't have the dual boot configured. I tried to use Wine to launch my Cinema 4d but it gives me this error:

Internal Error: String Resource not found!
The 'resource' directory seems to be corrupt or missing.

I tried googling and i found one other with the same error but without answers, if anyone knows what could be the cause of this...
My resource folder is there in the Cinema 4d folder, so I really don't know, it always worked on Windows...

---

### Post by pemur1 on 2008-02-17
Has anyone gotten this program to work in Ubuntu? I've done some looking in other forums, and some have said that if you use Wine 0.9.47 ([http://www.c4dcafe.com/ipb/index.php?act=Print&client=printer&f=146&t=26233](http://www.c4dcafe.com/ipb/index.php?act=Print&client=printer&f=146&t=26233)) it will work. I haven't been able to find that version though.

Also, does anyone use Bryce 5.5? I've gotten the program to install, but for some reason I can't get it to run.

---

