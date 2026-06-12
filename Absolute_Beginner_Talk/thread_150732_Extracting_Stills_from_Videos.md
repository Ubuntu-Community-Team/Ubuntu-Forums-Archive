---
title: "Extracting Stills from Videos"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by goober99 on 2006-03-26
I used [VirtualDub](http://virtualdub.org/) on Windows to extract stills from videos. VirtualDub made it extremely easy: I could skip around from frame to frame (or bigger chunks) with little to no delay and just copy the frame to the clipboard when I found the one I liked.

What application would you recommend for this on Ubuntu? I've been using Totem's Take Screenshot... feature, but it is not near as easy to use as VirtualDub. The finest control over navigation I've been able to achieve (shift + right arrow key) is 15 sec. increments. Frame-by-frame navigation would be nice. Plus the clumsy save dialog for the Take Screenshot... defaults back to my Desktop everytime I open a new video, so I have to navigate back to the directory where I am saving the screenshots.

---

### Post by bluevoodoo1 on 2006-03-26
You can do something similar to Totem with Xine. Xine might have slow-motion or something like that. You also might be able to take screenshots from any frame with dvdrip (if you're taking images from DVDs).

---

### Post by ronmarley1 on 2006-03-26
Kino will let you clip a scene with one click.  You can add it with the "Add Applications" selection at the bottom of the Applications menu.  It will ask for your password.  It's under "Sound and Video" and the "More programs..."  Just click the box in front of Kino and the Click "Apply" and it will install it.  For another option, you can also go to System -->Administration --> Synaptic Package Manager.  It will ask for your password.  Search for Kino and install it.  Your last choice is to open a Terminal window and type (or copy and paste) ```
sudo apt-get install kino
``` and hit enter.  It will ask for your password and then it will download and install it.  Good luck, and let me know how it goes!

---

### Post by gord on 2006-03-26
[avidemux](http://avidemux.sf.net), its basically virtualdub for linux

---

