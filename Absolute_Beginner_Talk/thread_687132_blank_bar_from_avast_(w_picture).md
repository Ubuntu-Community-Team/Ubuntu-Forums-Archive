---
title: "blank bar from avast (w/ picture)"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by DiscGo on 2008-02-04
I have seen several other posts with seemingly this same problem but I couldn't find a fix.

I installed Avant. And when I turned it on, it would bring up my active programs down at the bottom. I don't know what I did (but I screwed with something) and now when I open Avant, the bottom sixth of my screen is just blank.


I also lost my minimize, maximize, close features from my browser at the same time. Does anyone know what I did or how to fix this? 


What I really want is for the Avant to stay open at the bottom all the time, and no blank space at the bottom ever :D

Here is the picture of my screen:
[IMG]http://i51.photobucket.com/albums/f375/DiscGolfDiver/Website/blank.png[/IMG]
You can't tell very well but the bottom of the screen is just blank straight across.

---

### Post by hyperair on 2008-02-04
Right now I'm deducing that you've got nVidia's restricted drivers installed. So, run "sudo nvidia-xconfig --add-argb-glx-visuals --allow-glx-with-composite" in the terminal. Then restart X.

---

### Post by DiscGo on 2008-02-04
I put "sudo nvidia-xconfig --add-argb-glx-visuals --allow-glx-with-composite" in the terminal and then tried to start avant again (which is what I think "restart X" meant, and the problem continued. I have had a very frustrating 48 hours of Ubuntu here. 

Are there any more suggestions?

---

### Post by hyperair on 2008-02-04
I'm so very sorry. Restarting X is restarting your whole GUI not just avant. Ctrl+Alt+Backspace, or restarting your computer would do the job.

---

### Post by DiscGo on 2008-02-04
I don't have any idea how you learned that is what you needed to do, but I did that and it worked great.

---

